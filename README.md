# --------------------------------------------
# Service Account (security baseline)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: login-sa
  namespace: be-test

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: login-deployment
  namespace: be-test

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
      app: login-backend

  template:
    metadata:
      labels:
        app: login-backend

    spec:
      # Dedicated service account for RBAC/security
      serviceAccountName: login-sa

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
              app: login-backend

      # Existing hostAliases preserved
      hostAliases:
        - ip: "10.189.42.83"
          hostnames:
            - "uatrootdc1.uatad.sbi"

      # Existing volumes preserved
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

        # Production resource governance
        resources:
          requests:
            memory: "512Mi"
            cpu: "200m"
          limits:
            memory: "1Gi"
            cpu: "500m"

        ports:
          - containerPort: 8085

        # Startup probe prevents restart loops during boot
        startupProbe:
          tcpSocket:
            port: 8085
          failureThreshold: 30
          periodSeconds: 10

        # Liveness probe for self-healing
        livenessProbe:
          tcpSocket:
            port: 8085
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        # Readiness probe controls traffic routing
        readinessProbe:
          tcpSocket:
            port: 8085
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        # Graceful shutdown hook
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

        volumeMounts:
          - name: truststore-volume
            mountPath: "/etc/fincore/secrets"
            readOnly: true

---
# --------------------------------------------
# Service (internal cluster communication)
# --------------------------------------------
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

---
# --------------------------------------------
# Horizontal Pod Autoscaler (CPU-based scaling)
# --------------------------------------------
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
  name: login-pdb
  namespace: be-test

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: login-backend

---
# --------------------------------------------
# Network Policy (baseline security)
# --------------------------------------------
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

  # Allow inbound traffic (can tighten later)
  ingress:
    - {}

  # Allow outbound traffic (LDAP / Redis access)
  egress:
    - {}