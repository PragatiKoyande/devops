this is my yaml file:
# --------------------------------------------
# Service Account (security baseline)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: process-status-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: process-status-deployment
  namespace: backend

spec:
  replicas: 2

  # Keep previous ReplicaSets for rollback
  revisionHistoryLimit: 5

  # Zero-downtime rolling updates
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: process-status-backend

  template:
    metadata:
      labels:
        app: process-status-backend

    spec:
      # Dedicated service account for RBAC/security
      serviceAccountName: process-status-sa

      # Graceful shutdown duration
      terminationGracePeriodSeconds: 30

      # Disable automatic service env vars
      enableServiceLinks: false

      # Pod-level security hardening
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      # Spread pods across nodes (HA readiness)
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: process-status-backend

      containers:
      - name: process-status-container
        image: h06vksharbor.corp.ad.sbi/cbops/process-status-service:SV04
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"

        ports:
        - containerPort: 3000

        # Resource management (required for stable clusters + HPA)
        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        # Startup probe prevents restart loops during boot
        startupProbe:
          tcpSocket:
            port: 3000
          failureThreshold: 30
          periodSeconds: 10

        # Liveness probe for self-healing
        livenessProbe:
          tcpSocket:
            port: 3000
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        # Readiness probe controls traffic routing
        readinessProbe:
          tcpSocket:
            port: 3000
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        # Graceful shutdown hook
        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

        # Container-level security hardening
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: true
          capabilities:
            drop:
              - ALL

---
# --------------------------------------------
# Service (internal cluster communication)
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: process-status-service
  namespace: backend

spec:
  selector:
    app: process-status-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 3000

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler (CPU-based scaling)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: process-status-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: process-status-deployment

  minReplicas: 1
  maxReplicas: 5

  # Stabilization avoids scale flapping
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
# Ensures availability during maintenance
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: process-status-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: process-status-backend

---
