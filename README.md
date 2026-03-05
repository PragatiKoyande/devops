# --------------------------------------------
# Service Account
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
  revisionHistoryLimit: 5

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
      serviceAccountName: process-status-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      # ✅ Writable volumes required because root FS is read-only
      volumes:
        - name: logs-volume
          emptyDir: {}
        - name: tmp-volume
          emptyDir: {}

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

          # ✅ Mount writable directories
          volumeMounts:
            - name: logs-volume
              mountPath: /logs
            - name: tmp-volume
              mountPath: /tmp

          resources:
            requests:
              cpu: "200m"
              memory: "256Mi"
            limits:
              cpu: "500m"
              memory: "512Mi"

          startupProbe:
            tcpSocket:
              port: 3000
            failureThreshold: 30
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 3000
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 3
            failureThreshold: 3

          readinessProbe:
            tcpSocket:
              port: 3000
            initialDelaySeconds: 15
            periodSeconds: 5
            timeoutSeconds: 3
            failureThreshold: 3

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: true
            capabilities:
              drop:
                - ALL

---
# --------------------------------------------
# Service
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
# Horizontal Pod Autoscaler
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
  name: process-status-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: process-status-backend