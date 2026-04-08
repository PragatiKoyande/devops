# =====================================================
# Service Account (Dedicated Identity for Pod Security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: journal-sa
  namespace: uat-cbops1
automountServiceAccountToken: false
---
# =====================================================
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: journal-pdb
  namespace: uat-cbops1
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
  namespace: uat-cbops1
spec:
  replicas: 1

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

      serviceAccountName: journal-sa
      terminationGracePeriodSeconds: 30

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: journal-app

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      containers:
        - name: journal-app-container
          image: h06vksharbor.corp.ad.sbi/cbops/journal-service:UAT03
          imagePullPolicy: Always

          envFrom:
            - configMapRef:
                name: uat-common-app-config
            - secretRef:
                name: uat-common-app-secret

          ports:
            - containerPort: 9999

          resources:
            requests:
              cpu: "250m"
              memory: "512Mi"
            limits:
              cpu: "500m"
              memory: "1Gi"

          startupProbe:
            tcpSocket:
              port: 9999
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 9999
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 9999
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
  name: journal-hpa
  namespace: uat-cbops1
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
# Service
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: journal-service
  namespace: uat-cbops1
spec:
  selector:
    app: journal-app
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9999
  type: ClusterIP