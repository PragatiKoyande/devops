# =====================================================
# Service Account (Dedicated identity for pod security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: notification-sa
  namespace: cbops
automountServiceAccountToken: false

---
# =====================================================
# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: notification-deployment
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
      app: notification-backend

  template:
    metadata:
      labels:
        app: notification-backend

    spec:
      # -----------------------------------------------
      # Attach service account
      # -----------------------------------------------
      serviceAccountName: notification-sa

      # -----------------------------------------------
      # Graceful shutdown settings
      # -----------------------------------------------
      terminationGracePeriodSeconds: 30

      # -----------------------------------------------
      # Pod-level security
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
              app: notification-backend

      containers:
        - name: notification-container
          image: h06vksharbor.corp.ad.sbi/cbops/notification-service:SIT01

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
            - name: SPRING_DATASOURCE_URL
              value: "jdbc:postgresql://postgres-db:5432/notification_db"
            - name: SPRING_DATASOURCE_USERNAME
              value: "notification_user"
            - name: SPRING_DATASOURCE_PASSWORD
              value: "notification_password"
            - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
              value: "kafka.cbops.svc.cluster.local:9092"
            - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
              value: "kafka.cbops.svc.cluster.local:9092"
            - name: SPRING_KAFKA_CONSUMER_GROUP_ID
              value: "notification-service-group"
            - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
              value: "earliest"
            - name: SPRING_DATA_REDIS_HOST
              value: "redis-service"
            - name: SPRING_DATA_REDIS_PORT
              value: "6379"
            - name: SPRING_DATA_REDIS_CLIENT_TYPE
              value: "lettuce"

          ports:
            - containerPort: 9010

          imagePullPolicy: Always

          # -----------------------------------------------
          # Health probes (Spring Boot standard)
          # -----------------------------------------------
          readinessProbe:
            httpGet:
              path: /actuator/health
              port: 9010
            initialDelaySeconds: 20
            periodSeconds: 10

          livenessProbe:
            httpGet:
              path: /actuator/health
              port: 9010
            initialDelaySeconds: 40
            periodSeconds: 20

          startupProbe:
            httpGet:
              path: /actuator/health
              port: 9010
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
  name: notification-service
  namespace: cbops
spec:
  selector:
    app: notification-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9010
  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler (CPU-based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: notification-hpa
  namespace: cbops
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: notification-deployment
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
  name: notification-pdb
  namespace: cbops
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: notification-backend