# =========================================================
# SERVICE ACCOUNT
# Dedicated service account for workload identity and RBAC
# =========================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: ascii-generation-sa
  namespace: be-test

---
# =========================================================
# DEPLOYMENT
# =========================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ascii-generation-deployment
  namespace: be-test

spec:
  replicas: 1

  # Rolling update strategy for zero/minimal downtime deployments
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: ascii-generation-backend

  template:
    metadata:
      labels:
        app: ascii-generation-backend

    spec:

      # Graceful shutdown period
      terminationGracePeriodSeconds: 60

      # Dedicated Service Account
      serviceAccountName: ascii-generation-sa

      # Pod level security context
      securityContext:
        runAsNonRoot: true
        fsGroup: 2000
        seccompProfile:
          type: RuntimeDefault

      # Spread pods across nodes when replicas increase
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: ascii-generation-backend

      containers:
      - name: ascii-generation-container
        image: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service:DEV01

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_KAFKA_BOOTSTRAP_SERVERS
            value: "kafka-0.kafka.be-test.svc.cluster.local:9092"
          - name: HADOOP_FS_URI
            value: "hdfs://10.177.103.199:8022"
          - name: HADOOP_FS_USER
            value: "root"
          - name: APP_INPUT_BASE_PATH
            value: "/reports"
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.103.192:1523/fincorepdb1"
          - name: SPRING_DATASOURCE_USERNAME
            value: "fincore"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "Password#1234"

        ports:
        - containerPort: 8084

        imagePullPolicy: Always

        # Container level security hardening
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL

        # Resource management
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "1000m"
            memory: "1Gi"

        # Graceful shutdown hook
        lifecycle:
          preStop:
            exec:
              command:
                - /bin/sh
                - -c
                - sleep 20

        # Startup probe
        startupProbe:
          tcpSocket:
            port: 8084
          failureThreshold: 30
          periodSeconds: 10

        # Readiness probe
        readinessProbe:
          tcpSocket:
            port: 8084
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 3

        # Liveness probe
        livenessProbe:
          tcpSocket:
            port: 8084
          initialDelaySeconds: 60
          periodSeconds: 20
          timeoutSeconds: 5
          failureThreshold: 3

---
# =========================================================
# SERVICE
# =========================================================
apiVersion: v1
kind: Service
metadata:
  name: ascii-generation-service
  namespace: be-test

spec:
  selector:
    app: ascii-generation-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8084

  type: ClusterIP

---
# =========================================================
# HORIZONTAL POD AUTOSCALER
# CPU Based Autoscaling
# =========================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: ascii-generation-hpa
  namespace: be-test

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: ascii-generation-deployment

  minReplicas: 1
  maxReplicas: 5

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

---
# =========================================================
# POD DISRUPTION BUDGET
# Prevents voluntary disruptions
# =========================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: ascii-generation-pdb
  namespace: be-test

spec:
  minAvailable: 1

  selector:
    matchLabels:
      app: ascii-generation-backend