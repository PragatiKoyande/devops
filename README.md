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
 
  # Keeps previous ReplicaSets for rollback
  revisionHistoryLimit: 5
 
  # Zero-downtime rolling update strategy
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
 
      # Prometheus auto-scrape annotations (future monitoring readiness)
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "2000"
 
    spec:
      # Use dedicated service account
      serviceAccountName: common-master-sa
 
      # Allows graceful shutdown before SIGKILL
      terminationGracePeriodSeconds: 30
 
      # Prevent automatic service env injection (cleaner env)
      enableServiceLinks: false
 
 
      # Distribute pods across nodes (HA readiness)
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
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_PROFILES_ACTIVE  
            value: "dev"           
        ports:
        - containerPort: 2000
 
        # Resource management (required for stable clusters + HPA)
        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"
 
        # Startup probe prevents restart loops for slow-starting apps
        startupProbe:
          tcpSocket:
            port: 2000
          failureThreshold: 30
          periodSeconds: 10
 
        # Checks if container is alive (auto-restart if failed)
        livenessProbe:
          tcpSocket:
            port: 2000
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3
 
        # Controls when traffic is allowed to this pod
        readinessProbe:
          tcpSocket:
            port: 2000
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3
 
        # Graceful shutdown before pod termination
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
 
  # Prevent aggressive scaling (stability)
  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300
 
  # Scale based on CPU usage
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
# Prevents downtime during node maintenance
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
 
---

    
    



This is my manisfest file: kindly do changes and revert me the file dont alter any other thing just the changes required to resolve this iissue
