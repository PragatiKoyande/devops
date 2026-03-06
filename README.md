# ------------------------------------------------
# Service Account
# ------------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: notification-sa
  namespace: backend

---
# ------------------------------------------------
# Deployment
# ------------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: notification-deployment
  namespace: backend
  labels:
    app: notification-backend

spec:
  replicas: 2
  revisionHistoryLimit: 5

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
      serviceAccountName: notification-sa
      enableServiceLinks: false
      terminationGracePeriodSeconds: 30

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      topologySpreadConstraints:
      - maxSkew: 1
        topologyKey: kubernetes.io/hostname
        whenUnsatisfiable: ScheduleAnyway
        labelSelector:
          matchLabels:
            app: notification-backend

      containers:
      - name: notification-container
        image: h06vksharbor.corp.ad.sbi/cbops/notification-service:TEST-1
        imagePullPolicy: Always

        ports:
        - containerPort: 9010

        env:
        - name: SPRING_DATASOURCE_URL
          value: "jdbc:postgresql://postgres-db:5432/notification_db"

        - name: SPRING_DATASOURCE_USERNAME
          value: "notification_user"

        - name: SPRING_DATASOURCE_PASSWORD
          value: "notification_password"

        - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
          value: "kafka.backend.svc.cluster.local:9092"

        - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
          value: "kafka.backend.svc.cluster.local:9092"

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

        # Resources
        resources:
          requests:
            cpu: "200m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        # Mount writable logs directory
        volumeMounts:
        - name: logs-volume
          mountPath: /logs

        # Startup probe
        startupProbe:
          tcpSocket:
            port: 9010
          failureThreshold: 30
          periodSeconds: 10

        # Liveness probe
        livenessProbe:
          tcpSocket:
            port: 9010
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        # Readiness probe
        readinessProbe:
          tcpSocket:
            port: 9010
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh","-c","sleep 10"]

        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: true
          capabilities:
            drop:
            - ALL

      # Writable volume for logs
      volumes:
      - name: logs-volume
        emptyDir: {}

---
# ------------------------------------------------
# Service
# ------------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: notification-service
  namespace: backend
  labels:
    app: notification-backend

spec:
  type: ClusterIP

  selector:
    app: notification-backend

  ports:
  - name: http
    protocol: TCP
    port: 80
    targetPort: 9010

---
# ------------------------------------------------
# Horizontal Pod Autoscaler
# ------------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: notification-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: notification-deployment

  minReplicas: 1
  maxReplicas: 5

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 70

---
# ------------------------------------------------
# Pod Disruption Budget
# ------------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: notification-pdb
  namespace: backend

spec:
  minAvailable: 1

  selector:
    matchLabels:
      app: notification-backend