I will give you plain Kubernetes YAML manifests for one backend microservice.
Convert them into a single values.yaml file compatible with my reusable
Helm chart at: charts/backend-service/

═══════════════════════════════════════════════════════════════
SECTION 1 — SUPPORTED CHART SCHEMA
Only these keys are valid. Do NOT add anything outside this list.
═══════════════════════════════════════════════════════════════

namespace
replicaCount
image.repository
image.tag
image.pullPolicy
imagePullSecrets                          ← list of {name: secret-name}
deployment.name
deployment.revisionHistoryLimit
deployment.terminationGracePeriodSeconds
container.name
serviceAccount.name
service.name
service.type
service.port
service.targetPort
labels.app
autoscaling.enabled
autoscaling.name
autoscaling.minReplicas
autoscaling.maxReplicas
autoscaling.targetCPUUtilizationPercentage    ← EXACT key — no variants allowed
autoscaling.targetMemoryUtilizationPercentage ← set null if not used
pdb.enabled
pdb.name
pdb.minAvailable
networkPolicy.enabled
networkPolicy.name
env                                       ← list of {name, value}
configMap.enabled
configMap.data
secret.enabled
secret.data
database.enabled
database.existingSecret
database.url
database.username
database.password
database.driverClassName
resources.requests.cpu
resources.requests.memory
resources.limits.cpu
resources.limits.memory
probes.port

═══════════════════════════════════════════════════════════════
SECTION 2 — ABSOLUTE RULES (never violate these)
═══════════════════════════════════════════════════════════════

RULE 1 — PRESERVE ALL VALUES EXACTLY:
  - Do NOT change names, images, tags, ports, replicas,
    env vars, resource values, or any other value from the source YAML.

RULE 2 — NAMESPACE IS ALWAYS:
  namespace: cbops-test
  (override whatever is in the source YAML)

RULE 3 — ENABLED FLAG MAPPING:
  Source contains a Secret      → secret.enabled: true
  Source contains a ConfigMap   → configMap.enabled: true
  Source contains DB credentials → database.enabled: true
  Source contains an HPA        → autoscaling.enabled: true
  Source contains a PDB         → pdb.enabled: true
  Source contains NetworkPolicy → networkPolicy.enabled: true
  If NOT found                  → set enabled: false (never omit)

RULE 4 — HPA CPU KEY IS EXACT:
  MUST use: autoscaling.targetCPUUtilizationPercentage
  NEVER use: cpuUtilization, cpu, targetCPU, or any other variant.
  Wrong key → HPA deploys but CPU scaling NEVER triggers (silent failure).

RULE 5 — PRIVATE REGISTRY REQUIRES imagePullSecrets:
  If image.repository contains anything other than docker.io or
  standard public registries (gcr.io, quay.io, ghcr.io, k8s.gcr.io),
  always add:
    imagePullSecrets:
      - name: harbor-secret
  And add a comment: "Create with: kubectl create secret docker-registry..."

RULE 6 — DO NOT OUTPUT KUBERNETES MANIFESTS.
  Only output the final values.yaml file.

RULE 7 — ALL ENABLED FLAGS MUST BE PRESENT:
  Even if pdb.enabled and networkPolicy.enabled are not in the source,
  check if pdb.name or networkPolicy.name exist. If they do, set enabled: true.

RULE 8 — DO NOT ADD FIELDS NOT IN THE SCHEMA.
  If the source YAML has extra fields not in Section 1, ignore them.

═══════════════════════════════════════════════════════════════
SECTION 3 — DATABASE REFERENCE (CRITICAL — READ CAREFULLY)
═══════════════════════════════════════════════════════════════

Different microservices use different databases.
ALWAYS preserve the exact url and driverClassName from the source.
Use this reference to verify correctness:

┌─────────────────┬────────────────────────────────────────────────────────────────────┬──────────────────────────────────────────────┐
│ Database        │ JDBC URL Format                                                    │ driverClassName                              │
├─────────────────┼────────────────────────────────────────────────────────────────────┼──────────────────────────────────────────────┤
│ Oracle (service)│ jdbc:oracle:thin:@<host>:<port>/<service_name>                     │ oracle.jdbc.OracleDriver                     │
│ Oracle (SID)    │ jdbc:oracle:thin:@<host>:<port>:<SID>                              │ oracle.jdbc.OracleDriver                     │
│ PostgreSQL      │ jdbc:postgresql://<host>:<port>/<database>                         │ org.postgresql.Driver                        │
│ MySQL 8+        │ jdbc:mysql://<host>:<port>/<database>?useSSL=false                 │ com.mysql.cj.jdbc.Driver                     │
│ MySQL 5.x       │ jdbc:mysql://<host>:<port>/<database>                              │ com.mysql.jdbc.Driver                        │
│ MS SQL Server   │ jdbc:sqlserver://<host>:<port>;databaseName=<database>             │ com.microsoft.sqlserver.jdbc.SQLServerDriver │
│ H2 (dev only)   │ jdbc:h2:mem:testdb;DB_CLOSE_DELAY=-1                               │ org.h2.Driver                                │
└─────────────────┴────────────────────────────────────────────────────────────────────┴──────────────────────────────────────────────┘

For all database sections, add a comment identifying the DB type:
  # Database type: Oracle / PostgreSQL / MySQL / etc.

If password is in plain text, add this comment on the same line:
  password: "abc123"   # ⚠️ Move to Vault/ESO before production go-live

═══════════════════════════════════════════════════════════════
SECTION 4 — OUTPUT FORMAT REQUIREMENTS
═══════════════════════════════════════════════════════════════

1. Output ONLY the values.yaml file — no explanation, no markdown fences.

2. Add a header block at the top:
   # SERVICE: <service-name>
   # ENVIRONMENT: <dev/staging/prod — infer from source>
   # CHART: charts/backend-service/
   # DEPLOY: helm upgrade --install <name> charts/backend-service/ -f <this-file>.yaml -n cbops-test

3. Add a section comment above every major key group:
   # === Namespace ===
   # === Image ===
   # === Deployment ===
   # === Autoscaling ===
   etc.

4. Add inline comments explaining:
   - Why imagePullSecrets is needed (with the kubectl create command)
   - What env vars are injected by database.enabled
   - Any fields that were fixed/corrected vs the source

5. Keep the output clean, ordered top-to-bottom per the schema in Section 1.

6. Mark any fixes with a comment:  # FIXED: <explanation>

I am pasting my manifest file here:

# =====================================================
# Service Account (Dedicated identity for security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: dashboard-sa
  namespace: cbops-test
automountServiceAccountToken: false  # Security hardening

---
# =====================================================
# Pod Disruption Budget
# Ensures availability during voluntary disruptions
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: dashboard-pdb
  namespace: cbops-test
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: dashboard-backend

---
# =====================================================
# Deployment (Enterprise Hardened)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: dashboard-deployment
  namespace: cbops-test
spec:
  replicas: 1

  # Zero-downtime rolling updates
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: dashboard-backend

  template:
    metadata:
      labels:
        app: dashboard-backend
    spec:

      # Attach ServiceAccount
      serviceAccountName: dashboard-sa

      # Graceful termination
      terminationGracePeriodSeconds: 30

      # Spread pods across nodes (future scaling safety)
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: dashboard-backend

      # Pod-level security
      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      containers:
      - name: dashboard-container
        image: h06vksharbor.corp.ad.sbi/cbops/dashboard-service:DEV01
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"

        ports:
        - containerPort: 9015

        # Resource management
        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        # Health Probes (Spring Boot safe defaults)
        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 9015
          initialDelaySeconds: 15
          periodSeconds: 10
          failureThreshold: 5

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 9015
          initialDelaySeconds: 30
          periodSeconds: 20
          failureThreshold: 5

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 9015
          failureThreshold: 30
          periodSeconds: 10

        # Graceful shutdown hook
        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

        # Container security hardening
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL

---
# =====================================================
# Horizontal Pod Autoscaler (CPU based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: dashboard-hpa
  namespace: cbops-test
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: dashboard-deployment
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
# Network Policy (Zero Trust Networking)
# =====================================================
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: dashboard-network-policy
  namespace: cbops-test
spec:
  podSelector:
    matchLabels:
      app: dashboard-backend
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
          port: 9015
  egress:
    - to:
        - namespaceSelector: {}

---
# =====================================================
# Service (Original Logic Preserved)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: dashboard-service
  namespace: cbops-test
spec:
  selector:
    app: dashboard-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9015
  type: ClusterIP

  
