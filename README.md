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

      volumes:
      - name: tmp-dir
        emptyDir:
          medium: Memory
          sizeLimit: 64Mi

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000  

      containers:
      - name: notification-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/notification-service:PR-01
        imagePullPolicy: Always

        volumeMounts:
        - name: tmp-dir
          mountPath: /tmp        

        ports:
        - containerPort: 9010

        env:

        # ---------------------------
        # PostgreSQL
        # ---------------------------
        - name: SPRING_DATASOURCE_URL
          value: "jdbc:postgresql://10.190.224.113:5432/notification_db"

        - name: SPRING_DATASOURCE_USERNAME
          value: "fincore"

        - name: SPRING_DATASOURCE_PASSWORD
          value: "Password#1234"

        - name: SPRING_DATASOURCE_DRIVER_CLASS_NAME
          value: "org.postgresql.Driver"

        - name: SPRING_JPA_DATABASE_PLATFORM
          value: "org.hibernate.dialect.PostgreSQLDialect"

        - name: SPRING_JPA_HIBERNATE_DDL_AUTO
          value: "none"

        # ---------------------------
        # Kafka
        # ---------------------------
        - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
          value: "kafka.backend.svc.cluster.local:9092"

        - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
          value: "kafka.backend.svc.cluster.local:9092"

        - name: SPRING_KAFKA_CONSUMER_GROUP_ID
          value: "notification-service-group"

        - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
          value: "earliest"

        # ---------------------------
        # Redis
        # ---------------------------
        - name: SPRING_DATA_REDIS_HOST
          value: "redis-service"

        - name: SPRING_DATA_REDIS_PORT
          value: "6379"

        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: "lettuce"

        resources:
          requests:
            cpu: "200m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        startupProbe:
          tcpSocket:
            port: 9010
          failureThreshold: 30
          periodSeconds: 10

        livenessProbe:
          tcpSocket:
            port: 9010
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3

        readinessProbe:
          tcpSocket:
            port: 9010
          initialDelaySeconds: 15
          periodSeconds: 5

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
---
# ------------------------------------------------
# Service
# ------------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: notification-service
  namespace: backend

spec:
  type: ClusterIP

  selector:
    app: notification-backend

  ports:
  - port: 80
    targetPort: 9010
    protocol: TCP

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
