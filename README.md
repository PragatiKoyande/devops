I am sharing the deployment file for one of the micro service - common-master and let me tell you one thing here the config maps and secrets which i m send are different for this region and would be different for another region this is for dev..the values would be different for st prod and uat

# --------------------------------------------
# Service Account (security best practice)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-master-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: common-master-deployment
  namespace: backend

spec:
  replicas: 1

  revisionHistoryLimit: 5

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
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "2000"

    spec:
      serviceAccountName: common-master-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: common-master-backend

      containers:
        - name: common-master-container
          image: h06vksharbor.corp.ad.sbi/cbops/common-master-service:DEV02
          imagePullPolicy: Always

          envFrom:
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret

          ports:
            - containerPort: 2000

          resources:
            requests:
              cpu: "250m"
              memory: "512Mi"
            limits:
              cpu: "500m"
              memory: "1Gi"

          startupProbe:
            tcpSocket:
              port: 2000
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 2000
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 2000
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

---
# --------------------------------------------
# Service (internal cluster access)
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: common-master-service
  namespace: backend

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
# --------------------------------------------
# Horizontal Pod Autoscaler (auto scaling)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: common-master-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: common-master-deployment

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
  name: common-master-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: common-master-backend



this is my deployment file for one the microservice

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
