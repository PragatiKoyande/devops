# =====================================================
# Service Account (Dedicated identity for pod security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: journal-sa
  namespace: cbops
automountServiceAccountToken: false

---
# =====================================================
# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: journal-deployment
  namespace: cbops
spec:
  replicas: 1

  # -----------------------------------------------
  # Zero-downtime rolling update strategy
  # -----------------------------------------------
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: journal-app

  template:
    metadata:
      labels:
        app: journal-app

    spec:
      # -----------------------------------------------
      # Attach service account
      # -----------------------------------------------
      serviceAccountName: journal-sa

      # -----------------------------------------------
      # Graceful shutdown configuration
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
              app: journal-app

      containers:
      - name: journal-app-container
        image: h06vksharbor.corp.ad.sbi/cbops/journal-service:A2

        # -----------------------------------------------
        # Resource management (mandatory for production)
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
        - containerPort: 9999

        imagePullPolicy: Always

        # -----------------------------------------------
        # Health probes (Spring Boot standard endpoints)
        # -----------------------------------------------
        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 9999
          initialDelaySeconds: 20
          periodSeconds: 10

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 9999
          initialDelaySeconds: 40
          periodSeconds: 20

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 9999
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
  name: journal-service
  namespace: cbops
spec:
  selector:
    app: journal-app
  ports:
  - name: http
    protocol: TCP
    port: 80
    targetPort: 9999
  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler (CPU-based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: journal-hpa
  namespace: cbops
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: journal-deployment
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
  name: journal-pdb
  namespace: cbops
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: journal-app