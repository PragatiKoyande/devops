  Normal   Created    70s                kubelet            Created container: journal-app-container
  Normal   Started    70s                kubelet            Started container journal-app-container
  Warning  Unhealthy  41s (x3 over 61s)  kubelet            Startup probe failed: Get "http://192.168.2.205:9999/actuator/health": dial tcp 192.168.2.205:9999: connect: connection refused
  Warning  Unhealthy  1s (x4 over 31s)   kubelet            Startup probe failed: HTTP probe failed with statuscode: 500


  I am getting this issue

  my yaml is:
  # =====================================================
# Service Account (Dedicated identity for security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: journal-sa
  namespace: backend
automountServiceAccountToken: false  # Prevent unnecessary token mounting
---
# =====================================================
# Pod Disruption Budget
# Ensures pod is not voluntarily evicted during maintenance
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: journal-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: journal-app
---
# =====================================================
# Deployment (Enterprise Hardened)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: journal-deployment
  namespace: backend
spec:
  replicas: 2

  # Zero-downtime rolling updates
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: journal-app

  template:
    metadata:
      labels:
        app: journal-app
    spec:

      # Attach ServiceAccount
      serviceAccountName: journal-sa

      # Graceful shutdown window
      terminationGracePeriodSeconds: 30

      # Spread pods across nodes (future-proof scaling)
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: journal-app

      # Pod-level security context
      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      containers:
      - name: journal-app-container
        image: h06vksharbor.corp.ad.sbi/cbops/journal-service:DEV04
        imagePullPolicy: Always

        env:
        - name: SPRING_DATA_REDIS_HOST
          value: "redis-service"
        - name: SPRING_DATA_REDIS_PORT
          value: "6379"
        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: "lettuce"

        ports:
        - containerPort: 9999

        # =================================================
        # Resource Management (Prevent resource starvation)
        # =================================================
        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        # =================================================
        # Health Probes (Safe Spring Boot defaults)
        # =================================================
        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 9999
          initialDelaySeconds: 15
          periodSeconds: 10
          failureThreshold: 5

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 9999
          initialDelaySeconds: 30
          periodSeconds: 20
          failureThreshold: 5

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 9999
          failureThreshold: 30
          periodSeconds: 10

        # =================================================
        # Graceful Shutdown Hook
        # =================================================
        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

        # =================================================
        # Container-level Security Hardening
        # =================================================
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL
---
# =====================================================
# Horizontal Pod Autoscaler (CPU-based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: journal-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: journal-deployment
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
# Service (Original logic preserved)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: journal-service
  namespace: backend
spec:
  selector:
    app: journal-app
  ports:
  - name: http
    protocol: TCP
    port: 80
    targetPort: 9999
  type: ClusterIP
