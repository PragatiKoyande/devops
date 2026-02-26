this is my values.yaml file:

# ==============================================================
# SERVICE:     login-service
# ENVIRONMENT: dev
# CHART:       charts/backend-service/
# DEPLOY:      helm upgrade --install login charts/backend-service/ \
#                -f login-service-dev.yaml \
#                -n cbops-test \
#                --kubeconfig hpaa.conf
#
# DRY RUN:     helm upgrade --install login charts/backend-service/ \
#                -f login-service-dev.yaml \
#                -n cbops-test \
#                --dry-run --debug \
#                --kubeconfig hpaa.conf
#
# VERIFY:      kubectl get all -n cbops-test --kubeconfig hpaa.conf
# ==============================================================
# PROD-GRADE UPGRADES APPLIED (source was bare -- missing features):
#   ADDED: ServiceAccount (login-sa)
#   ADDED: HPA -- CPU autoscaling 1-3 replicas at 70%
#   ADDED: PDB -- 1 pod always available during maintenance
#   ADDED: resources requests/limits -- prevents OOMKill/starvation
#   ADDED: tcpSocket probes -- startup, liveness, readiness on port 8085
#   ADDED: revisionHistoryLimit: 5 -- rollback support
#   ADDED: terminationGracePeriodSeconds: 30 -- graceful shutdown
#
# GAPS FROM SOURCE YAML:
#
# [GAP 1] -- volumes/volumeMounts NOT IN CHART SCHEMA -- DROPPED
#   Source mounts LDAP truststore as a file volume:
#     Secret ldap-truststore-file -> /etc/fincore/secrets/ad-truststore.jks
#   Chart deployment.yaml does not support volumes or volumeMounts.
#   Impact: LDAP SSL truststore file will NOT exist in the pod.
#   The service will fail LDAP SSL handshake on startup without it.
#   Action: Extend chart deployment.yaml to support volumes/volumeMounts.
#   Manual patch after deploy (run this IMMEDIATELY after helm install):
#     kubectl patch deployment login-deployment -n cbops-test \
#       --kubeconfig hpaa.conf --type=json -p='[
#         {"op":"add","path":"/spec/template/spec/volumes","value":[
#           {"name":"truststore-volume","secret":{"secretName":"ldap-truststore-file",
#            "items":[{"key":"ad-truststore.jks","path":"ad-truststore.jks"}]}}
#         ]},
#         {"op":"add","path":"/spec/template/spec/containers/0/volumeMounts","value":[
#           {"name":"truststore-volume","mountPath":"/etc/fincore/secrets","readOnly":true}
#         ]}
#       ]'
#
# [GAP 2] -- hostAliases NOT IN CHART SCHEMA -- DROPPED
#   Source adds: 10.189.42.83 -> uatrootdc1.uatad.sbi
#   Required for LDAP DNS resolution inside the pod.
#   Impact: LDAP connection fails if cluster DNS cannot resolve this hostname.
#   Action: Extend chart deployment.yaml to support hostAliases.
#   Manual patch after deploy:
#     kubectl patch deployment login-deployment -n cbops-test \
#       --kubeconfig hpaa.conf --type=json -p='[
#         {"op":"add","path":"/spec/template/spec/hostAliases","value":[
#           {"ip":"10.189.42.83","hostnames":["uatrootdc1.uatad.sbi"]}
#         ]}
#       ]'
#
# [GAP 3] -- secretKeyRef ENV VAR PARTIALLY MAPPED
#   Source reads LDAP_TRUSTSTORE_PASSWORD from:
#     secretKeyRef: name=ldap-creds, key=truststore-password
#   Chart env block only supports plain value -- not valueFrom/secretKeyRef.
#   Workaround: password placed in secret.data below.
#   Chart injects secret.data as a Secret via envFrom.
#   Replace REPLACE_WITH_REAL_PASSWORD with the actual truststore password.
#
# [GAP 4] -- NETWORK POLICY DISABLED INTENTIONALLY
#   Bare NetworkPolicy with no rules = DENY ALL egress.
#   DENY ALL = LDAP and Redis unreachable = service crash on startup.
#
# [GAP 5] -- NAMESPACE OVERRIDDEN
#   FIXED: Source namespace was be-test. Overridden to cbops-test per Rule 2.
#
# [GAP 6] -- REDIS DNS UPDATED
#   FIXED: Source used redis-service.be-test.svc.cluster.local (be-test namespace).
#   Changed to redis-service (short DNS for cbops-test namespace).
#   If Redis is still in be-test, revert to: redis-service.be-test.svc.cluster.local
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
  repository: h06vksharbor.corp.ad.sbi/cbops/login-service
  tag: DEV09
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
# ADDED: revisionHistoryLimit and terminationGracePeriodSeconds
# not present in source -- added for prod-grade rollback and shutdown.
# ==============================================================
deployment:
  name: login-deployment
  revisionHistoryLimit: 5
  terminationGracePeriodSeconds: 30


# ==============================================================
# === Container Name ===
# Preserved exactly from source.
# ==============================================================
container:
  name: login-backend-container


# ==============================================================
# === Service Account ===
# ADDED: not in source -- prod-grade dedicated SA.
# ==============================================================
serviceAccount:
  name: login-sa


# ==============================================================
# === Service ===
# port 80 -> targetPort 8085 -- preserved exactly from source.
# ==============================================================
service:
  name: login-service
  type: ClusterIP
  port: 80
  targetPort: 8085


# ==============================================================
# === Labels ===
# ==============================================================
labels:
  app: login-backend


# ==============================================================
# === Autoscaling (HPA) ===
# ADDED: not in source -- prod-grade CPU autoscaling.
# ==============================================================
autoscaling:
  enabled: true
  name: login-hpa
  minReplicas: 1
  maxReplicas: 3
  targetCPUUtilizationPercentage: 70
  targetMemoryUtilizationPercentage: null


# ==============================================================
# === Pod Disruption Budget ===
# ADDED: not in source -- ensures 1 pod available during maintenance.
# ==============================================================
pdb:
  enabled: true
  name: login-pdb
  minAvailable: 1


# ==============================================================
# === Network Policy ===
# FIXED: disabled -- bare NetworkPolicy = DENY ALL egress.
# LDAP + Redis both unreachable if enabled. See GAP 4.
# ==============================================================
networkPolicy:
  enabled: false
  name: login-network-policy


# ==============================================================
# === Environment Variables ===
# All env vars preserved exactly from source.
# SPRING_PROFILES_ACTIVE already present in source -- kept.
# LDAP_TRUSTSTORE_PASSWORD removed from here -- moved to secret.data.
# FIXED: Redis host changed to short DNS. See GAP 6.
# ==============================================================
env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"
  - name: SPRING_LDAP_URLS
    value: "ldaps://uatrootdc1.uatad.sbi:3269"
  - name: JAVA_TOOL_OPTIONS
    value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"
  - name: SPRING_DATA_REDIS_HOST
    value: "redis-service"
  - name: SPRING_DATA_REDIS_PORT
    value: "6379"
  - name: SPRING_DATA_REDIS_CLIENT_TYPE
    value: "lettuce"
  - name: LDAP_TRUSTSTORE_PATH
    value: "file:/etc/fincore/secrets/ad-truststore.jks"


# ==============================================================
# === ConfigMap ===
# ==============================================================
configMap:
  enabled: false
  data: {}


# ==============================================================
# === Generic Secret ===
# secret.enabled: true -- LDAP truststore password stored here.
# Injected into pod via envFrom as env var LDAP_TRUSTSTORE_PASSWORD.
# Source read this from secretKeyRef (ldap-creds/truststore-password).
# See GAP 3 for full context.
#
# IMPORTANT: Replace REPLACE_WITH_REAL_PASSWORD before deploying.
# WARNING: Move to Vault/ESO before production go-live.
# ==============================================================
secret:
  enabled: true
  data:
    LDAP_TRUSTSTORE_PASSWORD: "REPLACE_WITH_REAL_PASSWORD"


# ==============================================================
# === Database ===
# No JDBC database. Uses LDAP for authentication + Redis for cache.
# SPRING_PROFILES_ACTIVE=dev loads any profile config from JAR.
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
# ADDED: not in source -- prod-grade baseline for stable scheduling.
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
# ADDED: not in source -- tcpSocket probes on port 8085.
# ==============================================================
probes:
  port: 8085

  And later I have created these secrets:

  D:\Pragati\Helm-Deployment>kubectl create secret generic ldap-truststore-file --from-file=ad-truststore.jks=./ad-truststore.jks --namespace=cbops-test  --kubeconfig h06vksuatcbopscls.conf
secret/ldap-truststore-file created

D:\Pragati\Helm-Deployment>kubectl create secret generic ldap-creds --from-literal=truststore-password=changeit --namespace=cbops-test  --kubeconfig h06vksuatcbopscls.conf
secret/ldap-creds created

Now I am getting this issue:

Topology Spread Constraints:  kubernetes.io/hostname:ScheduleAnyway when max skew 1 is exceeded for selector app=login-backend
Events:
  Type     Reason                           Age                From               Message
  ----     ------                           ----               ----               -------
  Normal   Scheduled                        31s                default-scheduler  Successfully assigned cbops-test/login-deployment-76df5875ff-j8xc9 to h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-bcssn
  Normal   Pulled                           28s                kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/login-service:DEV09" in 2.266s (2.266s including waiting). Image size: 259887358 bytes.
  Normal   Pulled                           27s                kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/login-service:DEV09" in 390ms (390ms including waiting). Image size: 259887358 bytes.
  Warning  FailedToRetrieveImagePullSecret  13s (x3 over 30s)  kubelet            Unable to retrieve some image pull secrets (harbor-secret); attempting to pull the image may not succeed.
  Normal   Pulling                          13s (x3 over 30s)  kubelet            Pulling image "h06vksharbor.corp.ad.sbi/cbops/login-service:DEV09"
  Warning  Failed                           13s (x3 over 28s)  kubelet            Error: secret "login-deployment-secret" not found
  Normal   Pulled                           13s                kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/login-service:DEV09" in 180ms (180ms including waiting). Image size: 259887358 bytes.

  could you help me making from yaml file
