# =====================================================
# Service Account (Dedicated Identity for Pod Security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-request-sa
  namespace: backend
automountServiceAccountToken: false
---
# =====================================================
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: common-request-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: common-request-backend
---
# =====================================================
# Deployment (Enterprise Hardened)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: common-request-deployment
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
      app: common-request-backend

  template:
    metadata:
      labels:
        app: common-request-backend
    spec:

      serviceAccountName: common-request-sa
      terminationGracePeriodSeconds: 30

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: common-request-backend

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      # ✅ ADD THIS (volume to create /logs)
      volumes:
        - name: log-volume
          emptyDir: {}

      containers:
      - name: common-request-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/common-request-service:PR01
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
            value: "kafka.backend.svc.cluster.local:9092"
          - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
            value: "kafka.backend.svc.cluster.local:9092"

        ports:
        - containerPort: 9000

        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        # ✅ ADD THIS (mount /logs inside container)
        volumeMounts:
          - name: log-volume
            mountPath: /logs

        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 9000
          initialDelaySeconds: 15
          periodSeconds: 10
          failureThreshold: 5

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 9000
          initialDelaySeconds: 30
          periodSeconds: 20
          failureThreshold: 5

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 9000
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
---
# =====================================================
# Horizontal Pod Autoscaler
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: common-request-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: common-request-deployment
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
  name: common-request-service
  namespace: backend
spec:
  selector:
    app: common-request-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9000
  type: ClusterIP