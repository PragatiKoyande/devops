# =====================================================
# Service Account (Dedicated identity for pod security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: user-sa
  namespace: cbops
automountServiceAccountToken: false

---
# =====================================================
# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-deployment
  namespace: cbops
spec:
  replicas: 1

  # -----------------------------------------------
  # Rolling update strategy (zero downtime)
  # -----------------------------------------------
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: user-backend

  template:
    metadata:
      labels:
        app: user-backend

    spec:
      # -----------------------------------------------
      # Attach service account
      # -----------------------------------------------
      serviceAccountName: user-sa

      # -----------------------------------------------
      # Graceful shutdown
      # -----------------------------------------------
      terminationGracePeriodSeconds: 30

      # -----------------------------------------------
      # Pod-level security context
      # -----------------------------------------------
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        fsGroup: 1000

      # -----------------------------------------------
      # High availability - spread pods
      # -----------------------------------------------
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: user-backend

      # -----------------------------------------------
      # Existing hostAliases (unchanged)
      # -----------------------------------------------
      hostAliases:
      - ip: "10.189.42.83"
        hostnames:
        - "uatrootdc1.uatad.sbi"

      # -----------------------------------------------
      # Existing volumes (unchanged)
      # -----------------------------------------------
      volumes:
      - name: truststore-volume
        secret:
          secretName: ldap-truststore-file
          items:
            - key: ad-truststore.jks
              path: ad-truststore.jks

      containers:
      - name: user-container
        image: h06vksharbor.corp.ad.sbi/cbops/user-service:SIT06

        # -----------------------------------------------
        # Resource management
        # -----------------------------------------------
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        # -----------------------------------------------
        # Container security hardening
        # -----------------------------------------------
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

        env:
            # ========= REQUIRED =========
            - name: SPRING_LDAP_URLS
              value: "ldaps://uatrootdc1.uatad.sbi:3269"
            - name: JAVA_TOOL_OPTIONS
              value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"
            - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
              value: "kafka-0.kafka.cbops.svc.cluster.local:9092"
            - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
              value: "kafka-0.kafka.cbops.svc.cluster.local:9092"
            - name: SPRING_KAFKA_CONSUMER_GROUP_ID
              value: "rbac-cache-group"
            - name: SPRING_DATA_REDIS_HOST
              value: "redis-service"
            - name: SPRING_DATA_REDIS_PORT
              value: "6379"
            - name: SPRING_DATA_REDIS_CLIENT_TYPE
              value: "lettuce"
            - name: SPRING_DATASOURCE_URL
              value: "jdbc:oracle:thin:@10.177.179.46:1523/fincorepdb1"
            - name: SPRING_DATASOURCE_USERNAME
              value: "fincore"
            - name: SPRING_DATASOURCE_PASSWORD
              value: "Password#1234"
            # LDAP TRUSTSTORE CONFIG
            - name: LDAP_TRUSTSTORE_PATH
              value: "file:/etc/fincore/secrets/ad-truststore.jks"
            - name: LDAP_TRUSTSTORE_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: ldap-creds
                  key: truststore-password

        ports:
        - containerPort: 8087

        imagePullPolicy: Always

        # -----------------------------------------------
        # Health probes (Spring Boot safe defaults)
        # -----------------------------------------------
        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 8087
          initialDelaySeconds: 20
          periodSeconds: 10

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 8087
          initialDelaySeconds: 40
          periodSeconds: 20

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 8087
          failureThreshold: 30
          periodSeconds: 10

        # -----------------------------------------------
        # Graceful shutdown hook
        # -----------------------------------------------
        lifecycle:
          preStop:
            exec:
              command: ["sh", "-c", "sleep 10"]

---
# =====================================================
# Service (unchanged)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: user-service
  namespace: cbops
spec:
  selector:
    app: user-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8087
  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler (CPU-based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: user-hpa
  namespace: cbops
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: user-deployment
  minReplicas: 1
  maxReplicas: 5
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
# =====================================================
# Pod Disruption Budget (ensure availability)
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: user-pdb
  namespace: cbops
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: user-backend