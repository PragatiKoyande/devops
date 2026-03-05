I am providing a Kubernetes YAML file.

IMPORTANT RULES — FOLLOW STRICTLY:

1. DO NOT change any existing values.
   - Do NOT modify names
   - Do NOT change image, ports, env, replicas
   - Do NOT rename resources
   - Do NOT alter existing logic

2. ONLY add enterprise-grade / production-grade Kubernetes features on top of the existing YAML.

3. Add all REQUIRED production and enterprise best practices EXCEPT Prometheus or monitoring annotations.
   Add things like:
   - resources requests & limits
   - liveness/readiness/startup probes (safe defaults)
   - rolling update strategy
   - security context
   - service account
   - HPA (CPU based)
   - PodDisruptionBudget
   - lifecycle preStop hook
   - topology spread constraints
   - network policy
   - graceful shutdown settings
   - any other MUST-HAVE enterprise features

4. Do NOT add Prometheus annotations or monitoring-related configs.

5. Keep YAML structure clean and production-ready.

6. Do not ask for permission before adding missing enterprise features — just add them.

7. After YAML, explain briefly what new things were added and why.
8. add also comments in yaml file for better understanding 
Here is the YAML:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: login-deployment
  namespace: be-test
spec:
  replicas: 1
  selector:
    matchLabels:
      app: login-backend
  template:
    metadata:
      labels:
        app: login-backend
    spec:
      hostAliases:
      - ip: "10.189.42.83"
        hostnames:
        - "uatrootdc1.uatad.sbi"
      volumes:
      - name: truststore-volume
        secret:
          secretName: ldap-truststore-file
          items:
            - key: ad-truststore.jks        # Ensure this matches the key you created
              path: ad-truststore.jks       # Forces the filename inside /etc/fincore/secrets/
      containers:
      - name: login-backend-container
        image: h06vksharbor.corp.ad.sbi/cbops/login-service:DEV09

        volumeMounts:
        - name: truststore-volume
          mountPath: "/etc/fincore/secrets"
          readOnly: true

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

        # LDAP TRUSTSTORE CONFIG
        - name: LDAP_TRUSTSTORE_PATH
          value: "file:/etc/fincore/secrets/ad-truststore.jks"

        - name: LDAP_TRUSTSTORE_PASSWORD
          valueFrom:
            secretKeyRef:
              name: ldap-creds
              key: truststore-password

        ports:
        - containerPort: 8085
        imagePullPolicy: Always

--- 
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

I want this in this fashion:

# =====================================================
# Service Account (Dedicated Identity for Pod Security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-request-sa
  namespace: cbops-test
automountServiceAccountToken: false   # Prevent unnecessary token mounting
---
# =====================================================
# Pod Disruption Budget
# Prevents voluntary eviction during maintenance
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: common-request-pdb
  namespace: cbops-test
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
  namespace: cbops-test
spec:
  replicas: 1

  # Rolling update for zero-downtime deployments
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

      # Attach Service Account
      serviceAccountName: common-request-sa

      # Graceful termination window
      terminationGracePeriodSeconds: 30

      # Spread pods across nodes if scaled in future
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: common-request-backend

      # Pod-level security
      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      containers:
      - name: common-request-container
        image: h06vksharbor.corp.ad.sbi/cbops/common-request-service:DEV08
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"

        ports:
        - containerPort: 9000

        # =================================================
        # Resource Management (Prevents Noisy Neighbor)
        # =================================================
        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        # =================================================
        # Health Probes (Spring Boot Safe Defaults)
        # =================================================
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
          readOnlyRootFilesystem: false
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
  name: common-request-hpa
  namespace: cbops-test
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
# Network Policy (Zero Trust Approach)
# Only allow traffic within namespace
# =====================================================
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: common-request-network-policy
  namespace: cbops-test
spec:
  podSelector:
    matchLabels:
      app: common-request-backend
  policyTypes:
    - Ingress
    - Egress
  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              kubernetes.io/metadata.name: cbops-test
      ports:
        - protocol: TCP
          port: 9000
  egress:
    - to:
        - namespaceSelector: {}
---
# =====================================================
# Service (Unchanged Logic)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: common-request-service
  namespace: cbops-test
spec:
  selector:
    app: common-request-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9000
  type: ClusterIP
