Similar to notification service now I want to do the helm deployment with different 3 environments for another service which is process-status service and I am sharing the manifest with you for the same

# --------------------------------------------
# Service Account 
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
        image: h06vksharbor.corp.ad.sbi/cbops/react-service:DEV46
        imagePullPolicy: Always

        ports:
        - containerPort: 80

        # Resource requests/limits for stable scheduling
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

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
