# ==============================================================
# SERVICE:     notification-service
# ENVIRONMENT: dev
# CHART:       charts/backend-service/
# DEPLOY:      helm upgrade --install notification charts/backend-service/ \
#                -f notification-service-dev.yaml \
#                -n cbops-test \
#                --kubeconfig hpaa.conf
#
# DRY RUN:     helm upgrade --install notification charts/backend-service/ \
#                -f notification-service-dev.yaml \
#                -n cbops-test \
#                --dry-run --debug \
#                --kubeconfig hpaa.conf
#
# VERIFY:      kubectl get all -n cbops-test --kubeconfig hpaa.conf
# ==============================================================
# PROD-GRADE UPGRADES APPLIED (source was bare -- missing features):
#   ADDED: ServiceAccount (notification-sa)
#   ADDED: HPA -- CPU autoscaling 1-3 replicas at 70%
#   ADDED: PDB -- 1 pod always available during maintenance
#   ADDED: resources requests/limits
#   ADDED: tcpSocket probes on port 9010
#   ADDED: revisionHistoryLimit: 5
#   ADDED: terminationGracePeriodSeconds: 30
#   ADDED: SPRING_PROFILES_ACTIVE: dev
#   MOVED: DB credentials from plain env vars into database secret
#
# GAPS FROM SOURCE YAML:
#
# [GAP 1] -- DB CREDENTIALS WERE PLAIN ENV VARS -- MOVED TO SECRET
#   Source exposed SPRING_DATASOURCE_URL/USERNAME/PASSWORD as plain env vars.
#   Moved to database section -- chart creates a Kubernetes Secret.
#   Secret name: notification-deployment-db-secret
#   Injected via envFrom as:
#     SPRING_DATASOURCE_URL, USERNAME, PASSWORD, DRIVER_CLASS_NAME
#   WARNING: Password is still plain text in this file -- move to Vault.
#
# [GAP 2] -- NETWORK POLICY DISABLED INTENTIONALLY
#   Bare NetworkPolicy with no rules = DENY ALL egress.
#   DENY ALL = Kafka, Redis, PostgreSQL all unreachable = crash.
#
# [GAP 3] -- NAMESPACE OVERRIDDEN
#   FIXED: Source namespace was be-test. Overridden to cbops-test.
#
# [GAP 4] -- KAFKA DNS USES cbops NAMESPACE
#   Source: kafka.cbops.svc.cluster.local:9092
#   Preserved exactly from source. Verify Kafka is in cbops namespace:
#     kubectl get svc kafka -n cbops --kubeconfig hpaa.conf
#   If Kafka moved to cbops-test, update to:
#     kafka.cbops-test.svc.cluster.local:9092
# ==============================================================


# ==============================================================
# === Namespace ===
# FIXED: was be-test -- overridden to cbops-test per Rule 2.
# ==============================================================
namespace: cbops-test


# ==============================================================
# === Replica Count ===
# ==============================================================
replicaCount: 1


# ==============================================================
# === Image ===
# ==============================================================
image:
  repository: h06vksharbor.corp.ad.sbi/cbops/notification-service
  tag: TEST-1
  pullPolicy: Always


# ==============================================================
# === Image Pull Secrets ===
# Required: private registry h06vksharbor.corp.ad.sbi
#
# Create ONCE per namespace:
#   kubectl create secret docker-registry harbor-secret \
#     --docker-server=h06vksharbor.corp.ad.sbi \
#     --docker-username=YOUR_USERNAME \
#     --docker-password=YOUR_PASSWORD \
#     -n cbops-test --kubeconfig hpaa.conf
# ==============================================================
imagePullSecrets:
  - name: harbor-secret


# ==============================================================
# === Deployment ===
# ADDED: revisionHistoryLimit and terminationGracePeriodSeconds.
# ==============================================================
deployment:
  name: notification-deployment
  revisionHistoryLimit: 5
  terminationGracePeriodSeconds: 30


# ==============================================================
# === Container Name ===
# Preserved exactly from source.
# ==============================================================
container:
  name: notification-container


# ==============================================================
# === Service Account ===
# ADDED: not in source -- prod-grade dedicated SA.
# ==============================================================
serviceAccount:
  name: notification-sa


# ==============================================================
# === Service ===
# port 80 -> targetPort 9010 -- preserved exactly from source.
# ==============================================================
service:
  name: notification-service
  type: ClusterIP
  port: 80
  targetPort: 9010


# ==============================================================
# === Labels ===
# ==============================================================
labels:
  app: notification-backend


# ==============================================================
# === Autoscaling (HPA) ===
# ADDED: not in source -- prod-grade CPU autoscaling.
# ==============================================================
autoscaling:
  enabled: true
  name: notification-hpa
  minReplicas: 1
  maxReplicas: 3
  targetCPUUtilizationPercentage: 70
  targetMemoryUtilizationPercentage: null


# ==============================================================
# === Pod Disruption Budget ===
# ADDED: not in source -- prod-grade availability protection.
# ==============================================================
pdb:
  enabled: true
  name: notification-pdb
  minAvailable: 1


# ==============================================================
# === Network Policy ===
# FIXED: disabled -- bare policy = DENY ALL = Kafka/Redis/DB blocked.
# ==============================================================
networkPolicy:
  enabled: false
  name: notification-network-policy


# ==============================================================
# === Environment Variables ===
# DB credentials removed -- moved to database section below.
# Kafka + Redis env vars preserved exactly from source.
# SPRING_PROFILES_ACTIVE added -- loads application-dev.properties.
# ==============================================================
env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"
  - name: SPRING_DATA_REDIS_HOST
    value: "redis-service"
  - name: SPRING_DATA_REDIS_PORT
    value: "6379"
  - name: SPRING_DATA_REDIS_CLIENT_TYPE
    value: "lettuce"
  - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
    value: "kafka.cbops.svc.cluster.local:9092"
  - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
    value: "kafka.cbops.svc.cluster.local:9092"
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "notification-service-group"
  - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
    value: "earliest"


# ==============================================================
# === ConfigMap ===
# ==============================================================
configMap:
  enabled: false
  data: {}


# ==============================================================
# === Generic Secret ===
# ==============================================================
secret:
  enabled: false
  data: {}


# ==============================================================
# === Database ===
# Database type: PostgreSQL
#
# Credentials were plain env vars in source -- moved to Secret.
# Creates Kubernetes Secret: notification-deployment-db-secret
# Injected via envFrom into container as:
#   SPRING_DATASOURCE_URL               = jdbc:postgresql://postgres-db:5432/notification_db
#   SPRING_DATASOURCE_USERNAME          = notification_user
#   SPRING_DATASOURCE_PASSWORD          = notification_password
#   SPRING_DATASOURCE_DRIVER_CLASS_NAME = org.postgresql.Driver
#
# Verify PostgreSQL service exists:
#   kubectl get svc postgres-db -n cbops-test --kubeconfig hpaa.conf
#
# WARNING: Plain-text password -- move to Vault/ESO before production.
# ==============================================================
database:
  enabled: true
  existingSecret: ""
  url: "jdbc:postgresql://postgres-db:5432/notification_db"
  username: "notification_user"
  password: "notification_password"
  driverClassName: ""


# ==============================================================
# === Resources ===
# ADDED: not in source -- prod-grade baseline.
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
# ADDED: not in source -- tcpSocket probes on port 9010.
# ==============================================================
probes:
  port: 9010



  This is my file
