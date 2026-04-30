# =====================================================
# Service Account (Dedicated identity for pod security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-request-sa
  namespace: cbops
automountServiceAccountToken: false

---
# =====================================================
# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: common-request-deployment
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
      app: common-request-backend

  template:
    metadata:
      labels:
        app: common-request-backend

    spec:
      # -----------------------------------------------
      # Attach service account
      # -----------------------------------------------
      serviceAccountName: common-request-sa

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
      # High availability - distribute pods across nodes
      # -----------------------------------------------
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: common-request-backend

      containers:
      - name: common-request-container
        image: h06vksharbor.corp.ad.sbi/cbops/common-request-service:SIT16

        # -----------------------------------------------
        # Resource requests & limits (mandatory)
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
          - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
            value: "kafka.cbops.svc.cluster.local:9092"
          - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
            value: "kafka.cbops.svc.cluster.local:9092"

        ports:
        - containerPort: 9000

        imagePullPolicy: Always

        # -----------------------------------------------
        # Health probes (Spring Boot safe defaults)
        # -----------------------------------------------
        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 9000
          initialDelaySeconds: 20
          periodSeconds: 10

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 9000
          initialDelaySeconds: 40
          periodSeconds: 20

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 9000
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
  name: common-request-service
  namespace: cbops
spec:
  selector:
    app: common-request-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9000
  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler (CPU-based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: common-request-hpa
  namespace: cbops
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: common-request-deployment
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
# Pod Disruption Budget (ensure minimum availability)
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: common-request-pdb
  namespace: cbops
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: common-request-backend