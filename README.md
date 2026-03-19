# =====================================================
# Service Account (Dedicated identity for security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: dashboard-sa
  namespace: backend
automountServiceAccountToken: false

---
# =====================================================
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: dashboard-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: dashboard-backend

---
# =====================================================
# Deployment
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: dashboard-deployment
  namespace: backend
spec:
  replicas: 2

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: dashboard-backend

  template:
    metadata:
      labels:
        app: dashboard-backend
    spec:

      serviceAccountName: dashboard-sa
      terminationGracePeriodSeconds: 30

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: dashboard-backend

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      containers:
      - name: dashboard-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/dashboard-service:PR01
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"

          # ✅ ADDED: Database Configuration (FIX)
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@//<DB_HOST>:<PORT>/<SERVICE_NAME>"
          - name: SPRING_DATASOURCE_USERNAME
            value: "<DB_USERNAME>"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "<DB_PASSWORD>"
          - name: SPRING_JPA_DATABASE_PLATFORM
            value: "org.hibernate.dialect.OracleDialect"

        ports:
        - containerPort: 9015

        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 9015
          initialDelaySeconds: 15
          periodSeconds: 10
          failureThreshold: 5

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 9015
          initialDelaySeconds: 30
          periodSeconds: 20
          failureThreshold: 5

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 9015
          failureThreshold: 30
          periodSeconds: 10

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL

        volumeMounts:
          - name: logs-volume
            mountPath: /logs

      volumes:
        - name: logs-volume
          emptyDir: {}

---
# =====================================================
# Horizontal Pod Autoscaler
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: dashboard-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: dashboard-deployment
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
# Service
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: dashboard-service
  namespace: backend
spec:
  selector:
    app: dashboard-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9015
  type: ClusterIP