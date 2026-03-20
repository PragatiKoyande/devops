# --------------------------------------------
# Service Account (security baseline)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: report-builder-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: report-builder-deployment
  namespace: backend

spec:
  replicas: 2
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: report-builder-app

  template:
    metadata:
      labels:
        app: report-builder-app

    spec:
      serviceAccountName: report-builder-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: report-builder-app

      containers:
      - name: report-builder-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/report-builder-service:PR01
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: HADOOP_FS_URI
            value: "hdfs://10.177.103.199:8022"
          - name: HADOOP_FS_USER
            value: "root"
          - name: GLIF_REPORTS_BASE_PATH
            value: "/reports"
          - name: LOGGING_FILE_PATH
            value: "/logs"

        ports:
        - containerPort: 8091

        volumeMounts:
          - name: logs-volume
            mountPath: /logs

        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        # ✅ FIXED: More tolerant startup probe
        startupProbe:
          tcpSocket:
            port: 8091
          failureThreshold: 60     # was 30 → doubled
          periodSeconds: 10        # total startup time = 10 min

        # ✅ FIXED: Liveness waits until app is stable
        livenessProbe:
          tcpSocket:
            port: 8091
          initialDelaySeconds: 90   # was 30 → increased
          periodSeconds: 15
          timeoutSeconds: 5
          failureThreshold: 5

        # ✅ FIXED: Readiness more forgiving
        readinessProbe:
          tcpSocket:
            port: 8091
          initialDelaySeconds: 30   # was 15
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 5

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

      volumes:
        - name: logs-volume
          emptyDir: {}

---
# --------------------------------------------
# Service (internal communication)
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: report-builder-service
  namespace: backend

spec:
  selector:
    app: report-builder-app

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8091

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler (CPU-based)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: report-builder-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: report-builder-deployment

  minReplicas: 1
  maxReplicas: 5

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
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: report-builder-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: report-builder-app