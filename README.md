# =====================================================
# Service Account (Dedicated identity for pod security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: transactions-sa
  namespace: cbops
automountServiceAccountToken: false

---
# =====================================================
# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: transactions-deployment
  namespace: cbops
spec:
  replicas: 1

  # -----------------------------------------------
  # Rolling update strategy (zero downtime)
  # -----------------------------------------------
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: transactions-backend

  template:
    metadata:
      labels:
        app: transactions-backend

    spec:
      # -----------------------------------------------
      # Attach service account
      # -----------------------------------------------
      serviceAccountName: transactions-sa

      # -----------------------------------------------
      # Graceful shutdown
      # -----------------------------------------------
      terminationGracePeriodSeconds: 30

      # -----------------------------------------------
      # Pod-level security context
      # -----------------------------------------------
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        fsGroup: 1000

      # -----------------------------------------------
      # High availability - spread pods across nodes
      # -----------------------------------------------
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: transactions-backend

      containers:
      - name: transactions-container
        image: h06vksharbor.corp.ad.sbi/cbops/transactions-service:A2

        # -----------------------------------------------
        # Resource management (mandatory)
        # -----------------------------------------------
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        # -----------------------------------------------
        # Container security hardening
        # -----------------------------------------------
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: true
          capabilities:
            drop:
              - ALL

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.179.46:1523/fincorepdb1"
          - name: SPRING_DATASOURCE_USERNAME
            value: "fincore"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "Password#1234"

        ports:
        - containerPort: 4000

        imagePullPolicy: Always

        # -----------------------------------------------
        # Health probes (Spring Boot safe defaults)
        # -----------------------------------------------
        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 4000
          initialDelaySeconds: 20
          periodSeconds: 10

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 4000
          initialDelaySeconds: 40
          periodSeconds: 20

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 4000
          failureThreshold: 30
          periodSeconds: 10

        # -----------------------------------------------
        # Graceful shutdown hook
        # -----------------------------------------------
        lifecycle:
          preStop:
            exec:
              command: ["sh", "-c", "sleep 10"]

---
# =====================================================
# Service (unchanged)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: transactions-service
  namespace: cbops
spec:
  selector:
    app: transactions-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 4000
  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler (CPU-based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: transactions-hpa
  namespace: cbops
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: transactions-deployment
  minReplicas: 1
  maxReplicas: 5
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
# =====================================================
# Pod Disruption Budget (ensure availability)
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: transactions-pdb
  namespace: cbops
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: transactions-backend