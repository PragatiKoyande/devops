# =====================================================
# Service Account (Dedicated Identity for Pod Security)
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
# Deployment (Enterprise Hardened)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: dashboard-deployment
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
          image: h06vksharbor.corp.ad.sbi/cbops/dashboard-service:UAT03
          imagePullPolicy: Always

          envFrom:
            - configMapRef:
                name: uat-common-app-config
            - secretRef:
                name: uat-common-app-secret

          ports:
            - containerPort: 9015

          resources:
            requests:
              cpu: "250m"
              memory: "512Mi"
            limits:
              cpu: "500m"
              memory: "1Gi"

          startupProbe:
            tcpSocket:
              port: 9015
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 9015
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 9015
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