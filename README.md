# =====================================================
# Service Account (Dedicated Identity for Pod Security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: login-sa
  namespace: be-test
automountServiceAccountToken: false   # Prevent unnecessary token mounting

---
# =====================================================
# Pod Disruption Budget
# Prevents voluntary eviction during maintenance
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: login-pdb
  namespace: be-test
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: login-backend

---
# =====================================================
# Deployment (Enterprise Hardened)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: login-deployment
  namespace: be-test
spec:
  replicas: 1

  # Keep old ReplicaSets for rollback safety
  revisionHistoryLimit: 5

  # Rolling update for zero-downtime deployments
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: login-backend

  template:
    metadata:
      labels:
        app: login-backend
    spec:

      # Attach dedicated Service Account
      serviceAccountName: login-sa

      # Graceful shutdown window
      terminationGracePeriodSeconds: 30

      # Disable automatic service environment variables
      enableServiceLinks: false

      # Spread pods across nodes if scaled in future
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: login-backend

      # Pod-level security hardening
      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      # Existing hostAliases (UNCHANGED)
      hostAliases:
      - ip: "10.189.42.83"
        hostnames:
        - "uatrootdc1.uatad.sbi"

      # Existing volume (UNCHANGED)
      volumes:
      - name: truststore-volume
        secret:
          secretName: ldap-truststore-file
          items:
            - key: ad-truststore.jks
              path: ad-truststore.jks

      containers:
      - name: login-backend-container
        image: h06vksharbor.corp.ad.sbi/cbops/login-service:DEV09
        imagePullPolicy: Always

        # Existing volume mount (UNCHANGED)
        volumeMounts:
        - name: truststore-volume
          mountPath: "/etc/fincore/secrets"
          readOnly: true

        # Existing environment variables (UNCHANGED)
        env:
        - name: SPRING_LDAP_URLS
          value: "ldaps://uatrootdc1.uatad.sbi:3269"
        - name: JAVA_TOOL_OPTIONS
          value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"
        - name: SPRING_DATA_REDIS_HOST
          value: "redis-service.be-test.svc.cluster.local"
        - name: SPRING_DATA_REDIS_PORT
          value: "6379"
        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: "lettuce"
        - name: SPRING_PROFILES_ACTIVE
          value: "dev"
        - name: LDAP_TRUSTSTORE_PATH
          value: "file:/etc/fincore/secrets/ad-truststore.jks"
        - name: LDAP_TRUSTSTORE_PASSWORD
          valueFrom:
            secretKeyRef:
              name: ldap-creds
              key: truststore-password

        ports:
        - containerPort: 8085

        # =================================================
        # Resource Management (Prevents Noisy Neighbor)
        # =================================================
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        # =================================================
        # Health Probes (Safe Spring Boot Defaults)
        # =================================================
        readinessProbe:
          tcpSocket:
            port: 8085
          initialDelaySeconds: 15
          periodSeconds: 10
          failureThreshold: 5

        livenessProbe:
          tcpSocket:
            port: 8085
          initialDelaySeconds: 30
          periodSeconds: 20
          failureThreshold: 5

        startupProbe:
          tcpSocket:
            port: 8085
          failureThreshold: 30
          periodSeconds: 10

        # =================================================
        # Graceful Shutdown Hook
        # =================================================
        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

        # =================================================
        # Container-level Security Hardening
        # =================================================
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false   # Disabled because truststore is mounted
          capabilities:
            drop:
              - ALL

---
# =====================================================
# Horizontal Pod Autoscaler (CPU Based)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: login-hpa
  namespace: be-test
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: login-deployment
  minReplicas: 1
  maxReplicas: 3
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
# =====================================================
# Network Policy (Zero Trust - Namespace Scoped)
# =====================================================
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: login-network-policy
  namespace: be-test
spec:
  podSelector:
    matchLabels:
      app: login-backend
  policyTypes:
    - Ingress
    - Egress

  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              kubernetes.io/metadata.name: be-test
      ports:
        - protocol: TCP
          port: 8085

  egress:
    - to:
        - namespaceSelector: {}
      ports:
        - protocol: TCP
          port: 6379   # Redis
        - protocol: TCP
          port: 3269   # LDAPS

---
# =====================================================
# Service (Unchanged Logic)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: login-service
  namespace: be-test
spec:
  selector:
    app: login-backend
  ports:
  - name: http
    protocol: TCP
    port: 80
    targetPort: 8085
  type: ClusterIP