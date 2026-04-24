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
  name: redis-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-deployment
  namespace: backend

spec:
  replicas: 2

  # Keep previous ReplicaSets for rollback
  revisionHistoryLimit: 5

  # Zero-downtime rolling update strategy
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: redis-server

  template:
    metadata:
      labels:
        app: redis-server

    spec:
      # Dedicated service account
      serviceAccountName: redis-sa

      # Graceful shutdown timing
      terminationGracePeriodSeconds: 30

      # Avoid automatic service env vars
      enableServiceLinks: false


      # Spread pods across nodes (HA readiness)
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: redis-server

      containers:
      - name: redis-container

        # Use a standard Redis image
        image: a2p05vksharbor.corp.ad.sbi/cbops/redis/redis-stack-server:latest
        imagePullPolicy: Always

        env:
          - name: ALLOW_EMPTY_PASSWORD
            value: "yes"

        ports:
        - containerPort: 6379

        # Resource requests & limits for stable scheduling
        resources:
          requests:
            cpu: "100m"
            memory: "128Mi"
          limits:
            cpu: "300m"
            memory: "512Mi"

        # Startup probe prevents restart loops during initialization
        startupProbe:
          tcpSocket:
            port: 6379
          failureThreshold: 30
          periodSeconds: 10

        # Liveness probe ensures Redis is alive
        livenessProbe:
          tcpSocket:
            port: 6379
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        # Readiness probe ensures service traffic only when ready
        readinessProbe:
          tcpSocket:
            port: 6379
          initialDelaySeconds: 10
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        # Graceful shutdown hook
        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

---
# --------------------------------------------
# Service (internal DNS access)
# redis-service.be-test.svc.cluster.local
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: redis-service # This name becomes the internal DNS hostname
  namespace: backend

spec:
  selector:
    app: redis-server

  ports:
    - protocol: TCP
      port: 6379
      targetPort: 6379

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler (CPU-based)
# NOTE: Redis is usually stateful — scaling should
# be validated for your architecture.
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: redis-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: redis-deployment

  minReplicas: 1
  maxReplicas: 3

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
# Prevents downtime during node maintenance
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: redis-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: redis-server

---
