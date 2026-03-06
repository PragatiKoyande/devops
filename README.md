# --------------------------------------------
# Service Account
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: user-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-deployment
  namespace: backend
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
      app: user-backend

  template:
    metadata:
      labels:
        app: user-backend

    spec:
      serviceAccountName: user-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

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
            app: user-backend

      # CREATE LOG DIRECTORY
      volumes:
      - name: logs-volume
        emptyDir: {}

      containers:
      - name: user-container
        image: h06vksharbor.corp.ad.sbi/cbops/user-service:TEST-1
        imagePullPolicy: Always

        # MOUNT /logs
        volumeMounts:
        - name: logs-volume
          mountPath: /logs

        env:
        - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
          value: "kafka-0.kafka.backend.svc.cluster.local:9092"

        - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
          value: "kafka-0.kafka.backend.svc.cluster.local:9092"

        - name: SPRING_KAFKA_CONSUMER_GROUP_ID
          value: "rbac-cache-group"

        - name: SPRING_DATA_REDIS_HOST
          value: "redis-service"

        - name: SPRING_DATA_REDIS_PORT
          value: "6379"

        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: "lettuce"

        ports:
        - containerPort: 8087

        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        startupProbe:
          tcpSocket:
            port: 8087
          failureThreshold: 30
          periodSeconds: 10

        livenessProbe:
          tcpSocket:
            port: 8087
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        readinessProbe:
          tcpSocket:
            port: 8087
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

---
# --------------------------------------------
# Service
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: user-service
  namespace: backend
spec:
  selector:
    app: user-backend

  ports:
  - name: http
    protocol: TCP
    port: 80
    targetPort: 8087

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: user-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: user-deployment

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
# --------------------------------------------
# Pod Disruption Budget
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: user-pdb
  namespace: backend

spec:
  minAvailable: 1

  selector:
    matchLabels:
      app: user-backend
