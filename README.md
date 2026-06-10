# ============================================================
# SERVICE ACCOUNT
# Dedicated service account for workload identity and RBAC
# ============================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: help-service-sa
  namespace: be-test

---
# ============================================================
# DEPLOYMENT
# ============================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: help-service-deployment
  namespace: be-test
spec:
  replicas: 1

  # Rolling update strategy for zero/low downtime deployments
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: help-service-backend

  template:
    metadata:
      labels:
        app: help-service-backend

    spec:

      # Dedicated service account
      serviceAccountName: help-service-sa

      # Graceful shutdown period
      terminationGracePeriodSeconds: 30

      # Spread pods across nodes whenever replicas increase
      topologySpreadConstraints:
      - maxSkew: 1
        topologyKey: kubernetes.io/hostname
        whenUnsatisfiable: ScheduleAnyway
        labelSelector:
          matchLabels:
            app: help-service-backend

      # Pod-level security settings
      securityContext:
        runAsNonRoot: true
        fsGroup: 2000

      containers:
      - name: help-service-container
        image: h06vksharbor.corp.ad.sbi/cbops/help-service:DEV01

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"

        ports:
        - containerPort: 9099

        imagePullPolicy: Always

        # Container security hardening
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL

        # Enterprise resource governance
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "1000m"
            memory: "1024Mi"

        # Graceful shutdown hook
        lifecycle:
          preStop:
            exec:
              command:
                - /bin/sh
                - -c
                - sleep 15

        # Startup probe
        # Prevents liveness checks until application is fully started
        startupProbe:
          tcpSocket:
            port: 9099
          failureThreshold: 30
          periodSeconds: 10

        # Readiness probe
        # Pod receives traffic only when ready
        readinessProbe:
          tcpSocket:
            port: 9099
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 2
          failureThreshold: 3
          successThreshold: 1

        # Liveness probe
        # Restarts unhealthy containers
        livenessProbe:
          tcpSocket:
            port: 9099
          initialDelaySeconds: 60
          periodSeconds: 20
          timeoutSeconds: 2
          failureThreshold: 3

---
# ============================================================
# SERVICE
# ============================================================
apiVersion: v1
kind: Service
metadata:
  name: help-service
  namespace: be-test
spec:
  selector:
    app: help-service-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9099
  type: ClusterIP

---
# ============================================================
# HORIZONTAL POD AUTOSCALER
# Auto-scales pods based on CPU utilization
# ============================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: help-service-hpa
  namespace: be-test
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: help-service-deployment

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
    scaleDown:
      stabilizationWindowSeconds: 300

---
# ============================================================
# POD DISRUPTION BUDGET
# Prevents voluntary disruptions from taking down all pods
# ============================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: help-service-pdb
  namespace: be-test
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: help-service-backend