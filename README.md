# ==========================================================
# SERVICE ACCOUNT
# Dedicated service account for workload isolation
# ==========================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: nwsa-variance-sa
  namespace: be-test

---
# ==========================================================
# DEPLOYMENT
# Enterprise-grade production deployment
# ==========================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nwsa-variance-deployment
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
      app: nwsa-variance-backend

  template:
    metadata:
      labels:
        app: nwsa-variance-backend

    spec:
      # Dedicated ServiceAccount
      serviceAccountName: nwsa-variance-sa

      # Graceful shutdown period
      terminationGracePeriodSeconds: 60

      # Spread pods across nodes when replicas increase
      topologySpreadConstraints:
      - maxSkew: 1
        topologyKey: kubernetes.io/hostname
        whenUnsatisfiable: ScheduleAnyway
        labelSelector:
          matchLabels:
            app: nwsa-variance-backend

      # Pod-level security context
      securityContext:
        runAsNonRoot: true
        fsGroup: 2000
        seccompProfile:
          type: RuntimeDefault

      containers:
      - name: nwsa-variance-container
        image: h06vksharbor.corp.ad.sbi/cbops/nwsa-variance-service:DEV01

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
          - name: NWSA_GENERATED_REPORT_ROOT
            value: "/reports"
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.103.192:1523/fincorepdb1"
          - name: SPRING_DATASOURCE_USERNAME
            value: "fincore"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "Password#1234"
          - name: NWSA_REPORT_ROOT
            value: "/reports"

        ports:
        - containerPort: 8093

        imagePullPolicy: Always

        # --------------------------------------------------
        # Resource Management
        # Prevent noisy-neighbor issues and enable HPA
        # --------------------------------------------------
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "1000m"
            memory: "1Gi"

        # --------------------------------------------------
        # Container Security
        # --------------------------------------------------
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
            - ALL

        # --------------------------------------------------
        # Startup Probe
        # Gives Spring Boot enough startup time
        # --------------------------------------------------
        startupProbe:
          tcpSocket:
            port: 8093
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 30

        # --------------------------------------------------
        # Readiness Probe
        # Traffic sent only when application is ready
        # --------------------------------------------------
        readinessProbe:
          tcpSocket:
            port: 8093
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 3
          successThreshold: 1

        # --------------------------------------------------
        # Liveness Probe
        # Restarts unhealthy containers automatically
        # --------------------------------------------------
        livenessProbe:
          tcpSocket:
            port: 8093
          initialDelaySeconds: 60
          periodSeconds: 20
          timeoutSeconds: 5
          failureThreshold: 3

        # --------------------------------------------------
        # Graceful Shutdown Hook
        # Allows ongoing requests to complete
        # --------------------------------------------------
        lifecycle:
          preStop:
            exec:
              command:
                - /bin/sh
                - -c
                - sleep 20

---
# ==========================================================
# SERVICE
# Existing Service retained unchanged
# ==========================================================
apiVersion: v1
kind: Service
metadata:
  name: nwsa-variance-service
  namespace: be-test
spec:
  selector:
    app: nwsa-variance-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8093
  type: ClusterIP

---
# ==========================================================
# HORIZONTAL POD AUTOSCALER
# CPU-based scaling
# ==========================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: nwsa-variance-hpa
  namespace: be-test
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: nwsa-variance-deployment
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
# ==========================================================
# POD DISRUPTION BUDGET
# Prevents voluntary disruptions from causing downtime
# ==========================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: nwsa-variance-pdb
  namespace: be-test
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: nwsa-variance-backend