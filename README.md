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
  replicas: 2
 
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
        image: a2p05vksharbor.corp.ad.sbi/cbops/common-master-service:PR01
        imagePullPolicy: Always
 
        env:
          # ✅ EXISTING
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_PROFILES_ACTIVE  
            value: "dev"

          # ✅ ADDED (FIX FOR DB ISSUE)
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@//<DB_HOST>:<PORT>/<SERVICE_NAME>"
          - name: SPRING_DATASOURCE_USERNAME
            value: "<DB_USERNAME>"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "<DB_PASSWORD>"
          - name: SPRING_DATASOURCE_DRIVER_CLASS_NAME
            value: "oracle.jdbc.OracleDriver"
          - name: SPRING_JPA_PROPERTIES_HIBERNATE_DIALECT
            value: "org.hibernate.dialect.OracleDialect"
 
        ports:
        - containerPort: 2000
 
        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"
 
        startupProbe:
          tcpSocket:
            port: 2000
          failureThreshold: 30
          periodSeconds: 10
 
        livenessProbe:
          tcpSocket:
            port: 2000
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3
 
        readinessProbe:
          tcpSocket:
            port: 2000
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