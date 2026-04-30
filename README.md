# =====================================================
# Service Account (Dedicated identity for pod)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-master-sa
  namespace: cbops
automountServiceAccountToken: false

---
# =====================================================
# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: common-master-deployment
  namespace: cbops
spec:
  replicas: 1

  # -----------------------------------------------
  # Rolling update strategy for zero downtime
  # -----------------------------------------------
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: common-master-backend

  template:
    metadata:
      labels:
        app: common-master-backend

    spec:
      serviceAccountName: common-master-sa

      # -----------------------------------------------
      # Graceful shutdown handling
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
      # Spread pods across nodes (HA readiness)
      # -----------------------------------------------
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: common-master-backend

      containers:
      - name: common-master-container
        image: h06vksharbor.corp.ad.sbi/cbops/common-master-service:SIT04

        # -----------------------------------------------
        # Resource management (MANDATORY in production)
        # -----------------------------------------------
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        # -----------------------------------------------
        # Container security context
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
        - containerPort: 2000

        imagePullPolicy: Always

        # -----------------------------------------------
        # Health checks (safe defaults for Spring Boot)
        # -----------------------------------------------
        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 2000
          initialDelaySeconds: 20
          periodSeconds: 10

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 2000
          initialDelaySeconds: 40
          periodSeconds: 20

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 2000
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
# Service (unchanged - kept as is)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: common-master-service
  namespace: cbops
spec:
  selector:
    app: common-master-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 2000
  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler (CPU based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: common-master-hpa
  namespace: cbops
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: common-master-deployment
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
# Pod Disruption Budget (Ensure availability)
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: common-master-pdb
  namespace: cbops
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: common-master-backend