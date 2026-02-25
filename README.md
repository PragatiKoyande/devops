# ==============================================================
# SERVICE:     common-request-service
# ENVIRONMENT: dev
# CHART:       charts/backend-service/
# DEPLOY:      helm upgrade --install common-request charts/backend-service/ \
#                -f common-request-service-dev.yaml \
#                -n cbops-test \
#                --kubeconfig hpaa.conf
#
# DRY RUN:     helm upgrade --install common-request charts/backend-service/ \
#                -f common-request-service-dev.yaml \
#                -n cbops-test \
#                --dry-run --debug \
#                --kubeconfig hpaa.conf
# ==============================================================
# FIXES APPLIED IN THIS VERSION:
#   FIX 1: env: block was completely missing -- restored with Redis vars
#   FIX 2: networkPolicy.enabled corrected to false (no rules yet)
#   FIX 3: database.enabled: true with Oracle credentials confirmed
# ==============================================================


# ==============================================================
# === Namespace ===
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
  repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: DEV08
  pullPolicy: Always


# ==============================================================
# === Image Pull Secrets ===
# Required for private Harbor registry.
# Create once per namespace:
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
# ==============================================================
deployment:
  name: common-request-deployment
  revisionHistoryLimit: 5
  terminationGracePeriodSeconds: 30


# ==============================================================
# === Container Name ===
# ==============================================================
container:
  name: common-request-container


# ==============================================================
# === Service Account ===
# ==============================================================
serviceAccount:
  name: common-request-sa


# ==============================================================
# === Service ===
# ==============================================================
service:
  name: common-request-service
  type: ClusterIP
  port: 80
  targetPort: 9000


# ==============================================================
# === Labels ===
# ==============================================================
labels:
  app: common-request-backend


# ==============================================================
# === Autoscaling (HPA) ===
# ==============================================================
autoscaling:
  enabled: true
  name: common-request-hpa
  minReplicas: 1
  maxReplicas: 3
  targetCPUUtilizationPercentage: 70
  targetMemoryUtilizationPercentage: null


# ==============================================================
# === Pod Disruption Budget ===
# ==============================================================
pdb:
  enabled: true
  name: common-request-pdb
  minAvailable: 1


# ==============================================================
# === Network Policy ===
# Disabled until ingress/egress rules are added to chart template.
# ==============================================================
networkPolicy:
  enabled: false
  name: common-request-network-policy


# ==============================================================
# === Environment Variables ===
# FIX 1: This entire block was MISSING in the previous deployed version.
# Without it the pod had NO env vars injected at all.
# Redis connection was missing and Spring context failed to initialize.
#
# NOTE: DB credentials are NOT set here.
# They are injected automatically via envFrom from the DB secret below:
#   SPRING_DATASOURCE_URL
#   SPRING_DATASOURCE_USERNAME
#   SPRING_DATASOURCE_PASSWORD
#   SPRING_DATASOURCE_DRIVER_CLASS_NAME
# ==============================================================
env:
  - name: SPRING_DATA_REDIS_HOST
    value: "redis-service"
  - name: SPRING_DATA_REDIS_PORT
    value: "6379"
  - name: SPRING_DATA_REDIS_CLIENT_TYPE
    value: "lettuce"
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"


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
# Database type: Oracle
#
# database.enabled: true creates Kubernetes Secret:
#   common-request-deployment-db-secret
#
# Injected into container via envFrom as:
#   SPRING_DATASOURCE_URL               = jdbc:oracle:thin:@10.177.103.192:1523/fincorepdb1
#   SPRING_DATASOURCE_USERNAME          = fincore
#   SPRING_DATASOURCE_PASSWORD          = Password#1234
#   SPRING_DATASOURCE_DRIVER_CLASS_NAME = oracle.jdbc.OracleDriver
#
# Spring Boot relaxed binding maps these to:
#   spring.datasource.url, username, password, driver-class-name
#
# Hibernate 6 uses the URL to auto-detect OracleDialect.
#
# WARNING: Plain-text password -- move to Vault/ESO before production.
# ==============================================================
database:
  enabled: true
  existingSecret: ""
  url: "jdbc:oracle:thin:@10.177.103.192:1523/fincorepdb1"
  username: "fincore"
  password: "Password#1234"
  driverClassName: "oracle.jdbc.OracleDriver"


# ==============================================================
# === Resources ===
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
# ==============================================================
probes:
  port: 9000