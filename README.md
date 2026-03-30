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
          value: "prod" 
        - name: SPRING_DATA_REDIS_HOST
          value: "redis-service"
        - name: SPRING_DATA_REDIS_PORT
          value: "6379"
        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: "lettuce"
        - name: SPRING_DATASOURCE_URL
          value: "jdbc:oracle:thin:@10.190.224.79:1523/fincorepdb1"
        - name: SPRING_DATASOURCE_USERNAME
          value: "fincore"
        - name: SPRING_DATASOURCE_PASSWORD
          value: "Password#1234"
        - name: SPRING_DATASOURCE_DRIVER_CLASS_NAME
          value: "oracle.jdbc.OracleDriver"

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



I want to inject these below secrets and config maps configuration in above manifest kindly do the changes and send me back entire manifest file also send me the valid yaml with proper indeatation fix issue
