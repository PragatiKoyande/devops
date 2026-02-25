# ==============================================================
# SERVICE:     journal-service
# ENVIRONMENT: dev
# CHART:       charts/backend-service/
# DEPLOY:      helm upgrade --install journal charts/backend-service/ \
#                -f journal-service-dev.yaml \
#                -n cbops-test \
#                --kubeconfig hpaa.conf
#
# DRY RUN:     helm upgrade --install journal charts/backend-service/ \
#                -f journal-service-dev.yaml \
#                -n cbops-test \
#                --dry-run --debug \
#                --kubeconfig hpaa.conf
#
# VERIFY:      kubectl get all -n cbops-test --kubeconfig hpaa.conf
# ==============================================================
#
# WARNING:  OBSERVATIONS & GAPS FROM SOURCE YAML (read before deploying):
#
# [GAP 1] -- PROBE TYPE MISMATCH
#   Source uses: httpGet /actuator/health on port 9999
#   Chart uses:  tcpSocket on probes.port (hardcoded in deployment.yaml)
#   Impact:      Port 9999 connectivity is checked correctly.
#                HTTP path /actuator/health check is NOT performed.
#   Action:      Upgrade chart deployment.yaml to support httpGet probes
#                if Spring Boot actuator health endpoint check is required.
#
# [GAP 2] -- securityContext NOT IN CHART SCHEMA -- DROPPED
#   Pod-level (dropped):
#     runAsNonRoot: true
#     runAsUser: 10001
#     fsGroup: 10001
#   Container-level (dropped):
#     allowPrivilegeEscalation: false
#     readOnlyRootFilesystem: false
#     capabilities.drop: [ALL]
#   Action:      Add securityContext block to chart deployment.yaml
#                and values schema. One fix covers all services.
#
# [GAP 3] -- NETWORK POLICY RULES NOT TEMPLATED
#   Source ingress: allow TCP:9999 from namespace cbops-test only
#   Source egress:  allow all namespaces
#   Impact:      networkPolicy.enabled: true creates the resource
#                but ingress/egress rules are NOT applied.
#                Zero-trust intent from source is NOT enforced.
#   Action:      Extend templates/networkpolicy.yaml to support
#                ingress/egress rule injection via values.
#
# [GAP 4] -- automountServiceAccountToken: false NOT IN SCHEMA
#   Source sets this on ServiceAccount for security hardening.
#   Chart's serviceaccount.yaml does not template this field.
#   Impact:      Token is auto-mounted by default (minor security gap).
#   Action:      Add automountServiceAccountToken: false to
#                templates/serviceaccount.yaml.
#
# NO DATABASE -- No DB credentials found in source YAML.
# NO CONFIGMAP -- No ConfigMap found in source YAML.
# NO SECRET    -- No generic Secret found in source YAML.
# ==============================================================


# ==============================================================
# === Namespace ===
# Always cbops-test per deployment standard.
# ==============================================================
namespace: cbops-test


# ==============================================================
# === Replica Count ===
# ==============================================================
replicaCount: 1


# ==============================================================
# === Image ===
# Private Harbor registry -- imagePullSecrets required (see below).
# ==============================================================
image:
  repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
  tag: DEV04
  pullPolicy: Always


# ==============================================================
# === Image Pull Secrets ===
# Required: image is on private registry h06vksharbor.corp.ad.sbi
#
# Run this ONCE per namespace to create the pull secret:
#   kubectl create secret docker-registry harbor-secret \
#     --docker-server=h06vksharbor.corp.ad.sbi \
#     --docker-username=YOUR_HARBOR_USERNAME \
#     --docker-password=YOUR_HARBOR_PASSWORD \
#     -n cbops-test --kubeconfig hpaa.conf
#
# Verify before deploying:
#   kubectl get secret harbor-secret -n cbops-test --kubeconfig hpaa.conf
# ==============================================================
imagePullSecrets:
  - name: harbor-secret


# ==============================================================
# === Deployment ===
# revisionHistoryLimit: not in source -- chart default (5) applied.
# terminationGracePeriodSeconds: 30 matches source exactly.
# ==============================================================
deployment:
  name: journal-deployment
  revisionHistoryLimit: 5
  terminationGracePeriodSeconds: 30


# ==============================================================
# === Container Name ===
# Explicitly defined in source as "journal-app-container".
# Preserved exactly -- overrides default fallback to deployment.name.
# ==============================================================
container:
  name: journal-app-container


# ==============================================================
# === Service Account ===
# ==============================================================
serviceAccount:
  name: journal-sa


# ==============================================================
# === Service ===
# port 80 ? targetPort 9999 -- preserved exactly from source.
# Other services in cluster call: http://journal-service/...
# ==============================================================
service:
  name: journal-service
  type: ClusterIP
  port: 80
  targetPort: 9999


# ==============================================================
# === Labels ===
# Matches pod selector label in source Deployment, PDB, and
# NetworkPolicy. Must be unique per service in the namespace.
# ==============================================================
labels:
  app: journal-app


# ==============================================================
# === Autoscaling (HPA) ===
# HPA found in source ? autoscaling.enabled: true
# CPU target: 70% -- preserved exactly from source.
# Memory scaling not in source ? null (disabled).
#
# WARNING:  KEY NAME MUST BE: targetCPUUtilizationPercentage (EXACT)
#     Any other key name is silently ignored by the chart template.
# ==============================================================
autoscaling:
  enabled: true
  name: journal-hpa
  minReplicas: 1
  maxReplicas: 3
  targetCPUUtilizationPercentage: 70
  targetMemoryUtilizationPercentage: null


# ==============================================================
# === Pod Disruption Budget ===
# PDB found in source ? pdb.enabled: true
# Ensures 1 pod stays running during node drains and upgrades.
# ==============================================================
pdb:
  enabled: true
  name: journal-pdb
  minAvailable: 1


# ==============================================================
# === Network Policy ===
# NetworkPolicy found in source ? networkPolicy.enabled: true
#
# WARNING:  See GAP 3 above -- ingress/egress rules from source are not
#     applied by the current chart template. Extend
#     templates/networkpolicy.yaml for full zero-trust enforcement.
# ==============================================================
networkPolicy:
  enabled: true
  name: journal-network-policy


# ==============================================================
# === Environment Variables ===
# Redis connection config -- non-sensitive, plain key/value.
# Injected directly into the container as env vars.
# ==============================================================
env:
  - name: SPRING_DATA_REDIS_HOST
    value: "redis-service"
  - name: SPRING_DATA_REDIS_PORT
    value: "6379"
  - name: SPRING_DATA_REDIS_CLIENT_TYPE
    value: "lettuce"


# ==============================================================
# === ConfigMap ===
# No ConfigMap found in source YAML.
# ==============================================================
configMap:
  enabled: false
  data: {}


# ==============================================================
# === Generic Secret ===
# No generic Secret found in source YAML.
# ==============================================================
secret:
  enabled: false
  data: {}


# ==============================================================
# === Database ===
# No database credentials found in source YAML.
# This service does not use Oracle, PostgreSQL, or any other DB.
# If DB is added in future, set enabled: true and fill in below:
#
# Oracle example:
#   database:
#     enabled: true
#     existingSecret: ""
#     url: jdbc:oracle:thin:@<host>:<port>/<service>
#     username: <username>
#     password: <password>   # WARNING: Move to Vault/ESO before production
#     driverClassName: oracle.jdbc.OracleDriver
#
# PostgreSQL example:
#   database:
#     enabled: true
#     existingSecret: ""
#     url: jdbc:postgresql://<host>:<port>/<database>
#     username: <username>
#     password: <password>   # WARNING: Move to Vault/ESO before production
#     driverClassName: org.postgresql.Driver
# ==============================================================
database:
  enabled: false
  existingSecret: ""
  url: ""
  username: ""
  password: ""
  driverClassName: ""


# ==============================================================
# === Resources ===
# Preserved exactly from source.
# JVM tip: set -Xmx410m in app (~80% of 512Mi limit) to prevent
# OOMKill from JVM overhead exceeding the memory limit.
# ==============================================================
resources:
  requests:
    cpu: "200m"
    memory: "256Mi"
  limits:
    cpu: "500m"
    memory: "512Mi"


# ==============================================================
# === Probes Port ===
# Spring Boot app listens on port 9999 (server.port=9999).
# Named port "http" in deployment.yaml maps to this value.
# Service targetPort "http" resolves to this port.
# See GAP 1 above -- source uses httpGet, chart uses tcpSocket.
# ==============================================================
probes:
  port: 9999