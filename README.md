I am getting indentation issue kindly reso;ve the issue and send me back entire file as is dont alter any other values:


# =====================================================
# Service Account
# Dedicated identity for secure pod execution
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: enquiry-service-sa
  namespace: backend
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
  namespace: backend
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
  namespace: backend
spec:
  replicas: 1
  revisionHistoryLimit: 5

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
      serviceAccountName: enquiry-service-sa
      terminationGracePeriodSeconds: 60

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 1000
        seccompProfile:
          type: RuntimeDefault

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: enquiry-service-backend

      containers:
      - name: enquiry-service-container
        image: h06vksharbor.corp.ad.sbi/cbops/enquiry-service:DEV-01
        imagePullPolicy: Always
		
        envFrom:
          - secretRef:
              name: oracle-secret

        ports:
        - containerPort: 4001
		
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "1000m"
            memory: "1Gi"

        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL

        livenessProbe:
          tcpSocket:
            port: 4001
          initialDelaySeconds: 60
          periodSeconds: 20
          timeoutSeconds: 5
          failureThreshold: 5

        readinessProbe:
          tcpSocket:
            port: 4001
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 3

        startupProbe:
          tcpSocket:
            port: 4001
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 30

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
  namespace: backend
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
  namespace: backend
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
