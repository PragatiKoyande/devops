# --------------------------------------------
# Service Account (security baseline)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: report-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: report-deployment
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
      app: report-backend

  template:
    metadata:
      labels:
        app: report-backend

    spec:
      serviceAccountName: report-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      hostAliases:
        - ip: "10.177.224.102"
          hostnames:
            - "fincore"
        - ip: "10.177.224.103"
          hostnames:
            - "fincore"
        - ip: "10.177.224.104"
          hostnames:
            - "fincore"
        - ip: "10.177.224.105"
          hostnames:
            - "fincore"
        - ip: "10.177.224.106"
          hostnames:
            - "fincore"

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: report-backend

      containers:
        - name: report-container
          image: a2p05vksharbor.corp.ad.sbi/cbops/report-service:PR-01
          imagePullPolicy: Always

          envFrom:
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: kafka-config
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret
            - configMapRef:
                name: hadoop-config

          resources:
            requests:
              memory: "1Gi"
              cpu: "500m"
            limits:
              memory: "8Gi"
              cpu: "4"

          ports:
            - containerPort: 9005

          startupProbe:
            tcpSocket:
              port: 9005
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 9005
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 9005
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

---
# --------------------------------------------
# Service
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: report-service
  namespace: backend

spec:
  selector:
    app: report-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9005

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: report-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: report-deployment

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
  name: report-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: report-backend