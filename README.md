
# =====================================================
# Service Account (Dedicated identity for pod security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: redis-sa
  namespace: cbops
automountServiceAccountToken: false

---
# =====================================================
# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-deployment
  namespace: cbops # Use the same namespace as your app
spec:
  replicas: 1

  # -----------------------------------------------
  # Rolling update strategy
  # -----------------------------------------------
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
      # -----------------------------------------------
      # Attach service account
      # -----------------------------------------------
      serviceAccountName: redis-sa

      # -----------------------------------------------
      # Graceful shutdown
      # -----------------------------------------------
      terminationGracePeriodSeconds: 30

      # -----------------------------------------------
      # Pod-level security
      # -----------------------------------------------
      securityContext:
        runAsNonRoot: true
        runAsUser: 1001
        fsGroup: 1001

      # -----------------------------------------------
      # Spread pods across nodes
      # -----------------------------------------------
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
        image: h06vksharbor.corp.ad.sbi/cbops/redis-server:latest

        # -----------------------------------------------
        # Resource management
        # -----------------------------------------------
        resources:
          requests:
            cpu: "100m"
            memory: "256Mi"
          limits:
            cpu: "300m"
            memory: "512Mi"

        # -----------------------------------------------
        # Container security
        # -----------------------------------------------
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false  # Redis needs write access for data
          capabilities:
            drop:
              - ALL

        env:
          - name: ALLOW_EMPTY_PASSWORD
            value: "yes"

        ports:
        - containerPort: 6379

        imagePullPolicy: Always

        # -----------------------------------------------
        # Health probes for Redis (TCP based)
        # -----------------------------------------------
        readinessProbe:
          tcpSocket:
            port: 6379
          initialDelaySeconds: 10
          periodSeconds: 10

        livenessProbe:
          tcpSocket:
            port: 6379
          initialDelaySeconds: 20
          periodSeconds: 20

        startupProbe:
          tcpSocket:
            port: 6379
          failureThreshold: 30
          periodSeconds: 5

        # -----------------------------------------------
        # Graceful shutdown hook
        # -----------------------------------------------
        lifecycle:
          preStop:
            exec:
              command: ["sh", "-c", "sleep 5"]

---
# =====================================================
# Service (unchanged)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: redis-service # This name becomes the internal DNS hostname
  namespace: cbops
spec:
  selector:
    app: redis-server
  ports:
    - protocol: TCP
      port: 6379
      targetPort: 6379
  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler (CPU-based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: redis-hpa
  namespace: cbops
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: redis-deployment
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
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: redis-pdb
  namespace: cbops
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: redis-server