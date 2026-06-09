# =========================================================
# SERVICE ACCOUNT
# Dedicated ServiceAccount for workload identity and RBAC
# =========================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: voucher-enquiry-sa
  namespace: be-test

---
# =========================================================
# DEPLOYMENT
# =========================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: voucher-enquiry-deployment
  namespace: be-test

spec:
  replicas: 1

  # Rolling update strategy for zero/minimal downtime deployments
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: voucher-enquiry-backend

  template:
    metadata:
      labels:
        app: voucher-enquiry-backend

    spec:

      # Dedicated Service Account
      serviceAccountName: voucher-enquiry-sa

      # Allows application to shutdown gracefully
      terminationGracePeriodSeconds: 60

      # Pod Security Context
      securityContext:
        runAsNonRoot: true
        fsGroup: 2000
        seccompProfile:
          type: RuntimeDefault

      # Spread pods across nodes when replicas increase
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: voucher-enquiry-backend

      containers:
      - name: voucher-enquiry-container
        image: h06vksharbor.corp.ad.sbi/cbops/voucher-enquiry-service:DEV-01

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_PROFILES_ACTIVE
            value: "dev"
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.103.192:1523/fincorepdb1"
          - name: SPRING_DATASOURCE_USERNAME
            value: "fincore"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "Password#1234"

        ports:
        - containerPort: 9025

        imagePullPolicy: Always

        # Container Security Context
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL

        # Resource Requests and Limits
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "1000m"
            memory: "1Gi"

        # Graceful termination before pod shutdown
        lifecycle:
          preStop:
            exec:
              command:
                - /bin/sh
                - -c
                - sleep 20

        # Startup Probe
        startupProbe:
          tcpSocket:
            port: 9025
          periodSeconds: 10
          failureThreshold: 30

        # Readiness Probe
        readinessProbe:
          tcpSocket:
            port: 9025
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 3

        # Liveness Probe
        livenessProbe:
          tcpSocket:
            port: 9025
          initialDelaySeconds: 60
          periodSeconds: 20
          timeoutSeconds: 5
          failureThreshold: 3

---
# =========================================================
# SERVICE
# =========================================================
apiVersion: v1
kind: Service
metadata:
  name: voucher-enquiry-service
  namespace: be-test

spec:
  selector:
    app: voucher-enquiry-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9025

  type: ClusterIP

---
# =========================================================
# HORIZONTAL POD AUTOSCALER
# CPU Based Autoscaling
# =========================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: voucher-enquiry-hpa
  namespace: be-test

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: voucher-enquiry-deployment

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
# =========================================================
# POD DISRUPTION BUDGET
# Prevents voluntary disruptions during maintenance
# =========================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: voucher-enquiry-pdb
  namespace: be-test

spec:
  minAvailable: 1

  selector:
    matchLabels:
      app: voucher-enquiry-backend