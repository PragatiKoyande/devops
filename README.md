I am providing a Kubernetes YAML file.

IMPORTANT RULES — FOLLOW STRICTLY:

1. DO NOT change any existing values.
   - Do NOT modify names
   - Do NOT change image, ports, env, replicas
   - Do NOT rename resources
   - Do NOT alter existing logic

2. ONLY add enterprise-grade / production-grade Kubernetes features on top of the existing YAML.

3. Add all REQUIRED production and enterprise best practices EXCEPT Prometheus or monitoring annotations.
   Add things like:
   - resources requests & limits
   - liveness/readiness/startup probes (safe defaults)
   - rolling update strategy
   - security context
   - service account
   - HPA (CPU based)
   - PodDisruptionBudget
   - lifecycle preStop hook
   - topology spread constraints
   - network policy
   - graceful shutdown settings
   - any other MUST-HAVE enterprise features

4. Do NOT add Prometheus annotations or monitoring-related configs.

5. Keep YAML structure clean and production-ready.

6. Do not ask for permission before adding missing enterprise features — just add them.

7. After YAML, explain briefly what new things were added and why.
8. add also comments in yaml file for better understanding 
Here is the YAML:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: notification-deployment
  namespace: be-test
spec:
  replicas: 1
  selector:
    matchLabels:
      app: notification-backend
  template:
    metadata:
      labels:
        app: notification-backend
    spec:
      containers:
        - name: notification-container
          image: h06vksharbor.corp.ad.sbi/cbops/notification-service:TEST-1
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
---
apiVersion: v1
kind: Service
metadata:
  name: notification-service
  namespace: be-test
spec:
  selector:
    app: notification-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9010
  type: ClusterIP


  I want in this similar fashion:

  # --------------------------------------------
# Service Account (security best practice)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-master-sa
  namespace: cbops-test
 
---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: common-master-deployment
  namespace: cbops-test
 
spec:
  replicas: 1
 
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
        image: h06vksharbor.corp.ad.sbi/cbops/common-master-service:CBOPS-04
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
  namespace: cbops-test
 
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
  namespace: cbops-test
 
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
  namespace: cbops-test
 
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: common-master-backend
 
---
# --------------------------------------------
# Network Policy (baseline network security)
# --------------------------------------------
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: common-master-network-policy
  namespace: cbops-test
 
spec:
  podSelector:
    matchLabels:
      app: common-master-backend
 
  policyTypes:
    - Ingress
    - Egress
 
  # Allow inbound traffic (can be restricted later)
  ingress:
    - {}
 
  # Allow outbound traffic (can be restricted later)
  egress:
    - {}
    
    
