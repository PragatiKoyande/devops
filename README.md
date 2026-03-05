Please make it in this fashion

# --------------------------------------------
# Service Account (security baseline)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: report-sa
  namespace: cbops-test

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: report-deployment
  namespace: cbops-test

spec:
  replicas: 1

  # Keep previous ReplicaSets for rollback
  revisionHistoryLimit: 5

  # Zero-downtime rolling updates
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
      # Dedicated service account for RBAC/security
      serviceAccountName: report-sa

      # Graceful shutdown duration
      terminationGracePeriodSeconds: 30

      # Disable automatic service env vars
      enableServiceLinks: false

      # Pod-level security hardening
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      # Spread pods across nodes (HA readiness)
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: report-backend

      containers:
      - name: report-container
        image: h06vksharbor.corp.ad.sbi/cbops/report-service:DEV11
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
            value: "kafka.cbops-test.svc.cluster.local:9092"
          - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
            value: "kafka.cbops-test.svc.cluster.local:9092"

        # Existing resources kept exactly as provided
        resources:
          requests:
            memory: "1Gi"
            cpu: "500m"
          limits:
            memory: "8Gi"
            cpu: "4"

        ports:
        - containerPort: 9005

        # Startup probe prevents restart loops during boot
        startupProbe:
          tcpSocket:
            port: 9005
          failureThreshold: 30
          periodSeconds: 10

        # Liveness probe for self-healing
        livenessProbe:
          tcpSocket:
            port: 9005
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        # Readiness probe controls traffic routing
        readinessProbe:
          tcpSocket:
            port: 9005
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        # Graceful shutdown hook
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
  name: report-service
  namespace: cbops-test

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
# Horizontal Pod Autoscaler (CPU-based scaling)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: report-hpa
  namespace: cbops-test

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: report-deployment

  minReplicas: 1
  maxReplicas: 5

  # Stabilization avoids scale flapping
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
# Ensures availability during maintenance
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: report-pdb
  namespace: cbops-test

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: report-backend

---
# --------------------------------------------
# Network Policy (baseline security)
# --------------------------------------------
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: report-network-policy
  namespace: cbops-test

spec:
  podSelector:
    matchLabels:
      app: report-backend

  policyTypes:
    - Ingress
    - Egress

  # Allow inbound traffic (can tighten later)
  ingress:
    - {}

  # Allow outbound traffic (Kafka/Redis access)
  egress:
    - {}
