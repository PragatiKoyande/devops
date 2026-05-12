# =====================================================
# Service Account
# Dedicated identity for secure pod execution
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: enquiry-service-sa
  namespace: be-test
automountServiceAccountToken: false

---
# =====================================================
# Pod Disruption Budget
# Ensures minimum pod availability during maintenance
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: enquiry-service-pdb
  namespace: be-test
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: enquiry-service-backend

---
# =====================================================
# Deployment
# Enterprise-grade production deployment configuration
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: enquiry-service-deployment
  namespace: be-test
spec:
  replicas: 1

  # -------------------------------------------------
  # Retain rollout history for rollback safety
  # -------------------------------------------------
  revisionHistoryLimit: 5

  # -------------------------------------------------
  # Rolling update strategy for zero downtime
  # -------------------------------------------------
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: enquiry-service-backend

  template:
    metadata:
      labels:
        app: enquiry-service-backend

    spec:
      # -------------------------------------------------
      # Dedicated Service Account
      # -------------------------------------------------
      serviceAccountName: enquiry-service-sa

      # -------------------------------------------------
      # Graceful shutdown handling
      # -------------------------------------------------
      terminationGracePeriodSeconds: 60

      # -------------------------------------------------
      # Pod-level security context
      # -------------------------------------------------
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 1000
        seccompProfile:
          type: RuntimeDefault

      # -------------------------------------------------
      # Spread pods across nodes for HA
      # -------------------------------------------------
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: enquiry-service-backend

      containers:
      - name: enquiry-service-container
        image: h06vksharbor.corp.ad.sbi/cbops/enquiry-service:DEV03

        # -------------------------------------------------
        # Environment Variables
        # -------------------------------------------------
        env:
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.103.192:1523/fincorepdb1"

          - name: SPRING_DATASOURCE_USERNAME
            value: "fincore"

          - name: SPRING_DATASOURCE_PASSWORD
            value: "Password#1234"

        ports:
        - containerPort: 4001

        imagePullPolicy: Always

        # -------------------------------------------------
        # Resource Management
        # Prevents noisy-neighbor issues
        # -------------------------------------------------
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "1000m"
            memory: "1Gi"

        # -------------------------------------------------
        # Container Security Context
        # -------------------------------------------------
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL

        # -------------------------------------------------
        # Liveness Probe
        # Restarts unhealthy containers
        # -------------------------------------------------
        livenessProbe:
          tcpSocket:
            port: 4001
          initialDelaySeconds: 60
          periodSeconds: 20
          timeoutSeconds: 5
          failureThreshold: 5

        # -------------------------------------------------
        # Readiness Probe
        # Ensures traffic only reaches ready pods
        # -------------------------------------------------
        readinessProbe:
          tcpSocket:
            port: 4001
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 3

        # -------------------------------------------------
        # Startup Probe
        # Protects slow-starting applications
        # -------------------------------------------------
        startupProbe:
          tcpSocket:
            port: 4001
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 30

        # -------------------------------------------------
        # Graceful Shutdown Hook
        # Allows in-flight requests to complete
        # -------------------------------------------------
        lifecycle:
          preStop:
            exec:
              command:
                - /bin/sh
                - -c
                - sleep 20

---
# =====================================================
# Service
# Internal ClusterIP service exposure
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: enquiry-service
  namespace: be-test
spec:
  selector:
    app: enquiry-service-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 4001

  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler
# CPU based autoscaling configuration
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: enquiry-service-hpa
  namespace: be-test
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: enquiry-service-deployment

  minReplicas: 1
  maxReplicas: 5

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
      policies:
        - type: Percent
          value: 100
          periodSeconds: 60

    scaleDown:
      stabilizationWindowSeconds: 300
      policies:
        - type: Percent
          value: 50
          periodSeconds: 60