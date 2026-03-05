# --------------------------------------------
# Service Account (security best practice)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: notification-sa
  namespace: be-test

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: notification-deployment
  namespace: be-test

spec:
  replicas: 1

  # Keeps previous ReplicaSets for rollback
  revisionHistoryLimit: 5

  # Zero-downtime rolling update strategy
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: notification-backend

  template:
    metadata:
      labels:
        app: notification-backend

    spec:
      # Use dedicated service account
      serviceAccountName: notification-sa

      # Allows graceful shutdown before SIGKILL
      terminationGracePeriodSeconds: 30

      # Prevent automatic service env injection
      enableServiceLinks: false

      # Pod-level security context
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      # Distribute pods across nodes (HA readiness)
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: notification-backend

      containers:
      - name: notification-container
        image: h06vksharbor.corp.ad.sbi/cbops/notification-service:TEST-1
        imagePullPolicy: Always

        env:
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:postgresql://postgres-db:5432/notification_db"
          - name: SPRING_DATASOURCE_USERNAME
            value: "notification_user"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "notification_password"
          - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
            value: "kafka.cbops.svc.cluster.local:9092"
          - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
            value: "kafka.cbops.svc.cluster.local:9092"
          - name: SPRING_KAFKA_CONSUMER_GROUP_ID
            value: "notification-service-group"
          - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
            value: "earliest"
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"

        ports:
          - containerPort: 9010

        # Resource management (required for stable clusters + HPA)
        resources:
          requests:
            cpu: "200m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        # Startup probe prevents restart loops for slow-starting apps
        startupProbe:
          tcpSocket:
            port: 9010
          failureThreshold: 30
          periodSeconds: 10

        # Checks if container is alive (auto-restart if failed)
        livenessProbe:
          tcpSocket:
            port: 9010
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        # Controls when traffic is allowed to this pod
        readinessProbe:
          tcpSocket:
            port: 9010
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        # Graceful shutdown before pod termination
        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

        # Container-level security hardening
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: true
          capabilities:
            drop:
              - ALL

---
# --------------------------------------------
# Service (internal cluster access)
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: notification-service
  namespace: be-test

spec:
  selector:
    app: notification-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9010

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler (auto scaling)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: notification-hpa
  namespace: be-test

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: notification-deployment

  minReplicas: 1
  maxReplicas: 5

  # Prevent aggressive scaling (stability)
  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

  # Scale based on CPU usage
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
# Prevents downtime during node maintenance
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: notification-pdb
  namespace: be-test

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: notification-backend

---
# --------------------------------------------
# Network Policy (baseline network security)
# --------------------------------------------
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: notification-network-policy
  namespace: be-test

spec:
  podSelector:
    matchLabels:
      app: notification-backend

  policyTypes:
    - Ingress
    - Egress

  # Allow inbound traffic (can be restricted later)
  ingress:
    - {}

  # Allow outbound traffic (Postgres / Kafka / Redis access)
  egress:
    - {}