Now I am sharing with you another microservice manifest files and details kilndly make proper congiuartion and send me backk all files:

# =====================================================
# Service Account 
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-request-sa
  namespace: backend
automountServiceAccountToken: false
---
# =====================================================
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: common-request-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: common-request-backend
---
# =====================================================
# Deployment 
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: common-request-deployment
  namespace: backend
spec:
  replicas: 1

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

      serviceAccountName: common-request-sa
      terminationGracePeriodSeconds: 30

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: common-request-backend

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      containers:
        - name: common-request-container
          image: h06vksharbor.corp.ad.sbi/cbops/common-request-service:DEV14
          imagePullPolicy: Always

          envFrom:
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: kafka-config
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret

          ports:
            - containerPort: 9000

          resources:
            requests:
              cpu: "250m"
              memory: "512Mi"
            limits:
              cpu: "500m"
              memory: "1Gi"

          startupProbe:
            tcpSocket:
              port: 9000
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 9000
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 9000
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: false
            capabilities:
              drop:
                - ALL
---
# =====================================================
# Horizontal Pod Autoscaler
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: common-request-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: common-request-deployment
  minReplicas: 1
  maxReplicas: 3
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
---
# =====================================================
# Service
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: common-request-service
  namespace: backend
spec:
  selector:
    app: common-request-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9000
  type: ClusterIP


----------------------------

redis-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: redis-config
  namespace: backend

data:
  SPRING_DATA_REDIS_HOST: "redis-service"
  SPRING_DATA_REDIS_PORT: "6379"
  SPRING_DATA_REDIS_CLIENT_TYPE: "lettuce"
  -----------------------------
  oracle-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: oracle-config
  namespace: backend

data:
  SPRING_DATASOURCE_URL: "jdbc:oracle:thin:@10.177.179.85:1523/fincorepdb1"
  SPRING_DATASOURCE_DRIVER_CLASS_NAME: "oracle.jdbc.OracleDriver"
  
oracle-secret:
apiVersion: v1
kind: Secret
metadata:
  name: oracle-secret
  namespace: backend

type: Opaque

data:
  SPRING_DATASOURCE_USERNAME: ZmluY29yZQ==
  SPRING_DATASOURCE_PASSWORD: UGFzc3dvcmQjMTIzNA==
  ----------------------------------------------------
  kafka-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: kafka-config
  namespace: backend

data:
  SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS: "kafka-0.kafka.backend.svc.cluster.local:9092"
  SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS: "kafka-0.kafka.backend.svc.cluster.local:9092"
