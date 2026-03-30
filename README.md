# --------------------------------------------
# Service Account (security best practice)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: template-config-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: template-config-deployment
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
      app: template-app

  template:
    metadata:
      labels:
        app: template-app

    spec:
      serviceAccountName: template-config-sa
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
              app: template-app

      containers:
        - name: template-config-container
          image: h06vksharbor.corp.ad.sbi/cbops/template-config-service:UAT04
          imagePullPolicy: Always
	  
	  env:
            - name: SPRING_PROFILES_ACTIVE
              value: "uat"

          envFrom:
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret

          ports:
            - containerPort: 8090

          resources:
            requests:
              cpu: "40m"
              memory: "256Mi"
            limits:
              cpu: "100m"
              memory: "512Mi"

          startupProbe:
            tcpSocket:
              port: 8090
            failureThreshold: 30
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 8090
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 3
            failureThreshold: 3

          readinessProbe:
            tcpSocket:
              port: 8090
            initialDelaySeconds: 15
            periodSeconds: 5
            timeoutSeconds: 3
            failureThreshold: 3

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

---
# --------------------------------------------
# Service (internal cluster communication)
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: template-config-service
  namespace: backend

spec:
  selector:
    app: template-app

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8090

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler (CPU-based)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: template-config-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: template-config-deployment

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
  name: template-config-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: template-app

      please resolve the indentation error and send me back the entire file
