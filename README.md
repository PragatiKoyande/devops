I am providing a Kubernetes YAML file for one microservice.

STRICT RULES:

1. DO NOT change any existing values.
   - Do NOT modify names
   - Do NOT rename resources
   - Do NOT change image
   - Do NOT change ports
   - Do NOT change env variables
   - Do NOT change replicas
   - Do NOT change logic
   - Do NOT remove any production or enterprise features

2. Convert this plain YAML into Helm chart compatible structure
   based on my existing reusable Helm chart:
   charts/springboot-service/

3. The output must:
   - Generate environments/base/<service-name>.yaml
   - Generate environments/dev/<service-name>.yaml if needed
   - Map values correctly into:
       namespace
       deployment.name
       service.name
       hpa.name
       pdb.name
       labels.app
       image.repository
       image.tag
       probes.port
       env
       resources

5. Do NOT redesign the YAML.
6. Do NOT simplify it.
7. Do NOT restructure logic.
8. Only parameterize safely to fit springboot-service chart.

9. Provide:
   - values file for base
   - dev override file if needed
   - exact helm upgrade command

10. use the namespace: backend   
11. I am having 4 different envrionmnets and I want to parameterize the code according to image and imagetag values make proper directory structure of charts values file and templates as I am having 3 different environments which are dev,sit,uat and prod so accordingly you make values. yaml  and send me back all the code snippets
12.  Please maintain consistency and keep these values separate for 4 different environments as you kept earlier for common-master and common-request in which you mentioned 
image:
  repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: DEV14


Here is the YAML:

# --------------------------------------------
# Service Account (security baseline)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: react-app-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: react-app-deployment
  namespace: backend

spec:
  replicas: 1

  # Keeps old ReplicaSets for rollback safety
  revisionHistoryLimit: 5

  # Zero-downtime rolling updates
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: reactive-app

  template:
    metadata:
      labels:
        app: reactive-app

    spec:
      # Use dedicated service account
      serviceAccountName: react-app-sa

      # Graceful shutdown time before force kill
      terminationGracePeriodSeconds: 30

      # Prevent automatic service env injection
      enableServiceLinks: false

      # Spread pods across nodes for HA readiness
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: reactive-app

      containers:
      - name: reactive-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/react-service:PR-16
        imagePullPolicy: Always

        ports:
        - containerPort: 80

        # Resource requests/limits for stable scheduling
        resources:
          requests:
            cpu: "100m"
            memory: "128Mi"
          limits:
            cpu: "300m"
            memory: "256Mi"

        # Startup probe prevents premature restarts
        startupProbe:
          tcpSocket:
            port: 80
          failureThreshold: 30
          periodSeconds: 10

        # Checks if container is alive
        livenessProbe:
          tcpSocket:
            port: 80
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        # Controls traffic routing to healthy pods
        readinessProbe:
          tcpSocket:
            port: 80
          initialDelaySeconds: 10
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        # Graceful shutdown for active connections
        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

---
# --------------------------------------------
# Service (internal access)
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: react-service
  namespace: backend

spec:
  selector:
    app: reactive-app

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 80

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler
# Auto-scales based on CPU usage
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: react-app-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: react-app-deployment

  minReplicas: 1
  maxReplicas: 5

  # Stabilization avoids rapid scale up/down
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
# Prevents downtime during node upgrades
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: react-app-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: reactive-app

---
