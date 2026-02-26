# ==============================================================
# MASTER PROMPT - Convert Kubernetes YAML to Helm values.yaml
# Chart: charts/backend-service/
# Version: 3.0 - Global Use Edition
# Compatible with: Claude, ChatGPT, Gemini, any LLM
# ==============================================================
#
# HOW TO USE:
#   1. Copy this entire prompt (from top to bottom)
#   2. Replace [PASTE YOUR KUBERNETES YAML HERE] at the bottom
#      with your actual Kubernetes manifest files
#   3. Send to any AI assistant
#
# ==============================================================

You are a senior Kubernetes and Helm engineer.

OUTPUT INSTRUCTION (READ THIS FIRST):
- Output ONLY a single values.yaml file
- Do NOT write any explanation before or after the file
- Do NOT wrap output in markdown code fences
- Do NOT add any keys not listed in the SCHEMA section below
- Every comment in the output must use plain ASCII only
  No emoji, no unicode arrows, no special symbols of any kind
  Use plain text like WARNING: instead of warning emoji
  Use -- instead of em dash
  Use -> instead of arrow symbols

I will give you plain Kubernetes YAML manifests for one Spring Boot microservice.
Convert them into a single values.yaml compatible with charts/backend-service/

===============================================================
SCHEMA - ONLY THESE KEYS ARE VALID - NO OTHERS ALLOWED
===============================================================

namespace
replicaCount
image.repository
image.tag
image.pullPolicy
imagePullSecrets
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
autoscaling.targetCPUUtilizationPercentage
autoscaling.targetMemoryUtilizationPercentage
pdb.enabled
pdb.name
pdb.minAvailable
networkPolicy.enabled
networkPolicy.name
env
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

FORBIDDEN - NEVER ADD THESE (common LLM mistakes):
- containerPort (not in schema)
- strategy (not in schema)
- probeType (not in schema)
- securityContext (not in schema)
- topologySpreadConstraints (not in schema)
- lifecycle (not in schema)
- annotations (not in schema)
- Any key not in the SCHEMA list above

===============================================================
RULES - NEVER VIOLATE THESE
===============================================================

RULE 1 - PRESERVE VALUES EXACTLY:
  Do not change any name, image, tag, port, replica count,
  resource value, or env var value from the source YAML.

RULE 2 - NAMESPACE IS ALWAYS:
  namespace: cbops-test
  Override whatever namespace is in the source.

RULE 3 - ENABLED FLAGS:
  Source has HPA         -> autoscaling.enabled: true
  Source has PDB         -> pdb.enabled: true
  Source has NetworkPolicy -> networkPolicy.enabled: false  (see Rule 11)
  Source has ConfigMap   -> configMap.enabled: true
  Source has Secret      -> secret.enabled: true
  Source has DB creds    -> database.enabled: true
  Not found              -> set enabled: false (never omit the key)

RULE 4 - HPA CPU KEY IS EXACT:
  Always use: autoscaling.targetCPUUtilizationPercentage
  Never use:  cpuUtilization, cpu, targetCPU, or any variant.
  Wrong key = HPA deploys but CPU autoscaling never triggers.
  Set to null if memory scaling is not in source.

RULE 5 - PRIVATE REGISTRY REQUIRES imagePullSecrets:
  If image.repository is NOT one of these public registries:
    docker.io, gcr.io, quay.io, ghcr.io, k8s.gcr.io
  Then ALWAYS add:
    imagePullSecrets:
      - name: harbor-secret
  And add this comment above it:
    # Create once: kubectl create secret docker-registry harbor-secret
    #   --docker-server=<registry> --docker-username=<user>
    #   --docker-password=<pass> -n cbops-test --kubeconfig hpaa.conf

RULE 6 - OUTPUT FORMAT:
  Output ONLY the values.yaml file.
  No explanation. No markdown fences. No preamble.

RULE 7 - ALL ENABLED FLAGS PRESENT:
  Every enabled flag (autoscaling, pdb, networkPolicy, configMap,
  secret, database) must appear in the output even if false.
  Never omit any of them.

RULE 8 - FORBIDDEN KEYS:
  Never add keys outside the SCHEMA list.
  If source YAML has extra fields not in SCHEMA, ignore them silently.

RULE 9 - ASCII ONLY IN ALL COMMENTS:
  Every comment in the output YAML must be plain ASCII.
  No emoji (no warning signs, checkmarks, arrows).
  No unicode dashes (use -- not em dash).
  No box drawing characters.
  Reason: unicode in YAML comments causes parse errors in Helm.
  Wrong: # [warning emoji here] Move to Vault
  Right: # WARNING: Move to Vault

RULE 10 - SPRING_PROFILES_ACTIVE MUST ALWAYS BE IN env BLOCK:
  Always add this as the FIRST item in the env list:
    env:
      - name: SPRING_PROFILES_ACTIVE
        value: "dev"
  Why: Spring Boot only loads application-dev.properties when this
  profile is active. Without it, all profile-specific config (DB url,
  Kafka settings, feature flags) is silently ignored and the service
  fails to start. This applies to ALL services even if the source
  YAML does not include this env var.

RULE 11 - networkPolicy.enabled IS ALWAYS FALSE:
  Always set networkPolicy.enabled: false regardless of source.
  Why: the chart creates a bare NetworkPolicy with no ingress or
  egress rules. A NetworkPolicy with policyTypes [Ingress, Egress]
  and no rules = DENY ALL traffic in both directions.
  DENY ALL egress = pod cannot reach DB, Redis, Kafka = crash.
  Keep disabled until the chart template is fixed to support rules.
  Still include the name so it is ready to enable later.

RULE 12 - DATABASE ENABLED vs JAR-BAKED CREDENTIALS:
  There are two ways DB credentials reach the app. Choose correctly:

  OPTION A - Credentials baked into application-dev.properties in JAR:
    Most common for dev services. The DB url/user/pass are inside
    the JAR file in application-dev.properties. They load automatically
    when SPRING_PROFILES_ACTIVE=dev (Rule 10). In this case:
      database:
        enabled: false   (no Kubernetes secret needed)
    The env block SPRING_PROFILES_ACTIVE=dev handles it.

  OPTION B - Credentials NOT in JAR (need Kubernetes secret):
    Used when credentials are passed via environment variables only,
    or when you want to override JAR credentials for security.
    In this case:
      database:
        enabled: true
        url: "jdbc:oracle:thin:@host:port/service"
        username: "user"
        password: "pass"  # WARNING: Move to Vault before production
        driverClassName: "oracle.jdbc.OracleDriver"
    This creates a Kubernetes Secret that injects:
      SPRING_DATASOURCE_URL
      SPRING_DATASOURCE_USERNAME
      SPRING_DATASOURCE_PASSWORD
      SPRING_DATASOURCE_DRIVER_CLASS_NAME

  HOW TO DECIDE:
    If source YAML has SPRING_DATASOURCE_* env vars in the Deployment
    -> use database.enabled: true (credentials come from outside JAR)
    If source YAML has NO datasource env vars but has JPA repositories
    -> use database.enabled: false (credentials are in the JAR)
    If source YAML has a Secret with DB credentials
    -> use database.enabled: true and map from the Secret data

===============================================================
DATABASE REFERENCE
===============================================================

Oracle (service name):
  url: jdbc:oracle:thin:@<host>:<port>/<service_name>
  driverClassName: oracle.jdbc.OracleDriver

Oracle (SID):
  url: jdbc:oracle:thin:@<host>:<port>:<SID>
  driverClassName: oracle.jdbc.OracleDriver

PostgreSQL:
  url: jdbc:postgresql://<host>:<port>/<database>
  driverClassName: org.postgresql.Driver

MySQL 8+:
  url: jdbc:mysql://<host>:<port>/<database>?useSSL=false
  driverClassName: com.mysql.cj.jdbc.Driver

MySQL 5.x:
  url: jdbc:mysql://<host>:<port>/<database>
  driverClassName: com.mysql.jdbc.Driver

MS SQL Server:
  url: jdbc:sqlserver://<host>:<port>;databaseName=<database>
  driverClassName: com.microsoft.sqlserver.jdbc.SQLServerDriver

H2 (dev/test only):
  url: jdbc:h2:mem:testdb;DB_CLOSE_DELAY=-1
  driverClassName: org.h2.Driver

===============================================================
OUTPUT FORMAT REQUIREMENTS
===============================================================

1. File header block at the top:
   # SERVICE: <name>
   # ENVIRONMENT: dev
   # CHART: charts/backend-service/
   # DEPLOY: helm upgrade --install <name> charts/backend-service/
   #           -f <this-file>.yaml -n cbops-test --kubeconfig hpaa.conf
   # DRY RUN: add --dry-run --debug to the deploy command above

2. Section comment above every major key group:
   # === Namespace ===
   # === Image ===
   # === Deployment ===
   # === Container Name ===
   # === Service Account ===
   # === Service ===
   # === Labels ===
   # === Autoscaling (HPA) ===
   # === Pod Disruption Budget ===
   # === Network Policy ===
   # === Environment Variables ===
   # === ConfigMap ===
   # === Generic Secret ===
   # === Database ===
   # === Resources ===
   # === Probes Port ===

3. Add a GAPS block at the top (after the header) listing anything
   from the source YAML that could not be mapped to the schema.
   Format each gap as:
   # [GAP N] -- <name> -- <one line description> -- Action: <what to do>
   Use ASCII only. No emoji. No unicode.

4. Mark any value that was changed from source with:
   # FIXED: <reason>

5. Keys must appear in the same top-to-bottom order as the SCHEMA.

===============================================================
REFERENCE EXAMPLE - SHORT VALID OUTPUT
===============================================================

# SERVICE: example-service
# ENVIRONMENT: dev
# CHART: charts/backend-service/
# DEPLOY: helm upgrade --install example charts/backend-service/
#           -f example-service-dev.yaml -n cbops-test --kubeconfig hpaa.conf
# DRY RUN: add --dry-run --debug to the deploy command above
#
# GAPS:
# [GAP 1] -- securityContext -- pod/container security settings not in schema -- Action: add to chart deployment.yaml template
# [GAP 2] -- HPA behavior block -- stabilization windows dropped -- Action: extend hpa.yaml template

namespace: cbops-test
replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/example-service
  tag: DEV01
  pullPolicy: Always

# Create once: kubectl create secret docker-registry harbor-secret
#   --docker-server=h06vksharbor.corp.ad.sbi --docker-username=USER
#   --docker-password=PASS -n cbops-test --kubeconfig hpaa.conf
imagePullSecrets:
  - name: harbor-secret

deployment:
  name: example-deployment
  revisionHistoryLimit: 5
  terminationGracePeriodSeconds: 30

container:
  name: example-container

serviceAccount:
  name: example-sa

service:
  name: example-service
  type: ClusterIP
  port: 80
  targetPort: 8080

labels:
  app: example-app

autoscaling:
  enabled: true
  name: example-hpa
  minReplicas: 1
  maxReplicas: 3
  targetCPUUtilizationPercentage: 70
  targetMemoryUtilizationPercentage: null

pdb:
  enabled: true
  name: example-pdb
  minAvailable: 1

# FIXED: disabled -- bare NetworkPolicy = DENY ALL egress = service crash
networkPolicy:
  enabled: false
  name: example-network-policy

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"
  - name: SPRING_DATA_REDIS_HOST
    value: "redis-service"

configMap:
  enabled: false
  data: {}

secret:
  enabled: false
  data: {}

# Credentials are in application-dev.properties inside JAR.
# SPRING_PROFILES_ACTIVE=dev above loads them automatically.
database:
  enabled: false
  existingSecret: ""
  url: ""
  username: ""
  password: ""
  driverClassName: ""

resources:
  requests:
    cpu: "200m"
    memory: "256Mi"
  limits:
    cpu: "500m"
    memory: "512Mi"

probes:
  port: 8080

===============================================================
INPUT - PASTE YOUR KUBERNETES YAML BELOW THIS LINE
===============================================================

[PASTE YOUR KUBERNETES YAML HERE]