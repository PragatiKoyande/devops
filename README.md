Now I am sharing with you another microservice manifest file please make in helm format like yesterday and add details kilndly make proper congiuartion and send me backk all files:

# =====================================================
# Service Account 
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: transactions-sa
  namespace: backend
automountServiceAccountToken: false
---
# =====================================================
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: transactions-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: transactions-backend
---
# =====================================================
# Deployment 
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: transactions-deployment
  namespace: backend
spec:
  replicas: 1

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: transactions-backend

  template:
    metadata:
      labels:
        app: transactions-backend
    spec:
      serviceAccountName: transactions-sa
      terminationGracePeriodSeconds: 30

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: transactions-backend

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      containers:
        - name: transactions-container
          image: h06vksharbor.corp.ad.sbi/cbops/transactions-service:DEV01
          imagePullPolicy: Always

          envFrom:
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret

          ports:
            - containerPort: 4000

          resources:
            requests:
              cpu: "250m"
              memory: "512Mi"
            limits:
              cpu: "500m"
              memory: "1Gi"

          startupProbe:
            tcpSocket:
              port: 4000
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 4000
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 4000
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

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
---
# =====================================================
# Horizontal Pod Autoscaler
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: transactions-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: transactions-deployment
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
  name: transactions-service
  namespace: backend
spec:
  selector:
    app: transactions-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 4000
  type: ClusterIP
