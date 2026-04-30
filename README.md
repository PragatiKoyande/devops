# =====================================================
# Service Account (Dedicated identity for pod security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: redis-sa
  namespace: be-test
automountServiceAccountToken: false

---
# =====================================================
# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-deployment
  namespace: be-test
spec:
  replicas: 1

  # -----------------------------------------------
  # Rolling update strategy (safe deployment)
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
      # Graceful shutdown configuration
      # -----------------------------------------------
      terminationGracePeriodSeconds: 30

      # -----------------------------------------------
      # Pod-level security context
      # -----------------------------------------------
      securityContext:
        runAsNonRoot: true
        runAsUser: 1001
        fsGroup: 1001

      # -----------------------------------------------
      # High availability (spread pods across nodes)
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
        image: h06vksharbor.corp.ad.sbi/cbops/redis-server:latest

        # -----------------------------------------------
        # Resource management (mandatory)
        # -----------------------------------------------
        resources:
          requests:
            cpu: "100m"
            memory: "256Mi"
          limits:
            cpu: "300m"
            memory: "512Mi"

        # -----------------------------------------------
        # Container security hardening
        # -----------------------------------------------
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false  # Redis requires write access
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
        # Health probes (TCP-based for Redis)
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
  namespace: be-test
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
  namespace: be-test
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
# Pod Disruption Budget (ensure availability)
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: redis-pdb
  namespace: be-test
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: redis-server