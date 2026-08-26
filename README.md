# =====================================================================
# BASE values.yaml
# This file holds the SECURE, PRODUCTION-LEANING defaults shared by all
# 20 services. Each environment overlay in environments/ only overrides
# what actually differs (replica count, resource sizes, feature flags).
# Each SERVICE only overrides values.yaml (name, image repo, port, etc.)
# via its own service-level values file - never edit templates/.
#
# GitLab CI usage (image tag passed at deploy time, not baked into any file):
#   helm upgrade --install ${SERVICE_NAME} ./chart \
#     -f ./chart/values.yaml \
#     -f ./chart/environments/values-${ENV}.yaml \
#     -f ./services/${SERVICE_NAME}/values.yaml \
#     --set image.tag=${CI_COMMIT_SHORT_SHA} \
#     --namespace ${ENV} --install --atomic --timeout 5m
# =====================================================================

# REQUIRED - set this per service in that service's own values file, e.g.
# services/login/values.yaml -> serviceName: login
# This single value drives every resource name in the chart - nothing else
# to edit, nothing hardcoded in any template:
#   Deployment               -> login-deployment
#   Service                  -> login-service
#   PodDisruptionBudget      -> login-pdb
#   HorizontalPodAutoscaler  -> login-hpa
#   ServiceAccount           -> login-sa
serviceName: "login"

replicaCount: 2
revisionHistoryLimit: 5
terminationGracePeriodSeconds: 30

image:
  repository: registry.example.com/myorg/myapp   # override per-service
  pullPolicy: Always
  tag: ""      # overridden by --set image.tag=$CI_COMMIT_SHORT_SHA in CI
  digest: ""   # optional: pin by digest instead of tag for prod

imagePullSecrets: []
  # - name: regcred

priorityClassName: ""

# ---------------------------------------------------------------------
# FEATURE TOGGLES - the entire point of this chart. Environments turn
# these on/off; templates never need to change.
# ---------------------------------------------------------------------
features:
  enableHPA: false
  enablePodDisruptionBudget: false
  enableTopologySpread: false
  enableStrictSecurity: true      # non-root, seccomp, etc.
  enableReadOnlyRoot: true        # read-only root filesystem
  enableResourceLimits: true

serviceAccount:
  create: true
  name: ""
  automountServiceAccountToken: false
  annotations: {}

securityContext:
  runAsUser: 10001
  runAsGroup: 10001
  fsGroup: 10001

updateStrategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 0    # zero downtime by default
    maxSurge: 1

service:
  type: ClusterIP
  port: 80
  targetPort: 8085
  clusterIP: ""
  sessionAffinity: ""
  nodePort: ""
  annotations: {}
  extraPorts: []
  # - name: metrics
  #   port: 8085
  #   targetPort: metrics

resources:
  requests:
    cpu: 100m
    memory: 128Mi
  limits:
    cpu: 500m
    memory: 512Mi

autoscaling:
  minReplicas: 2
  maxReplicas: 6
  targetCPUUtilizationPercentage: 70
  targetMemoryUtilizationPercentage: 80
  behavior:
    scaleDown:
      stabilizationWindowSeconds: 300
      policies:
        - type: Pods
          value: 1
          periodSeconds: 60
    scaleUp:
      stabilizationWindowSeconds: 0
      policies:
        - type: Pods
          value: 2
          periodSeconds: 60

podDisruptionBudget:
  minAvailable: 1
  maxUnavailable: ""

topologySpreadConstraints:
  - maxSkew: 1
    topologyKey: topology.kubernetes.io/zone
    whenUnsatisfiable: ScheduleAnyway
    labelSelector:
      matchLabels: {}   # populated automatically via selectorLabels in a future iteration if needed

probes:
  startup:
    enabled: false
    path: /healthz
    initialDelaySeconds: 0
    periodSeconds: 5
    failureThreshold: 30
  liveness:
    path: /healthz
    initialDelaySeconds: 10
    periodSeconds: 10
    timeoutSeconds: 3
    failureThreshold: 3
  readiness:
    path: /ready
    initialDelaySeconds: 5
    periodSeconds: 10
    timeoutSeconds: 3
    failureThreshold: 3

lifecycle:
  preStopSleep: 5   # gives the LB time to deregister the pod before SIGTERM

envFrom:
   configMaps:
     - name: config-kafka
     - name: config-redis
     - name: config-oracle
     - name: config-hdfs
	 - name: config-ldap
   secrets:
     - name: oracle-secret
     - name: kafka-aes-secret
     - name: rsa-private-secret
     - name: rsa-public-secret
     - name: jwt-secret
	 - name: secret-ldap
	 - name: blocked-login-ip

env: []
  # - name: LOG_LEVEL
  #   value: "info"

volumes: []
volumeMounts: []
initContainers: []
extraContainers: []

hostAliases: []

podAnnotations: {}
podLabels: {}
deploymentAnnotations: {}
commonLabels: {}



D:\pragati\ALL\login-service>helm template cm . -f ./environments/values-dev.yaml
Error: cannot load values.yaml: cannot unmarshal yaml document: error converting YAML to JSON: yaml: line 153: found a tab character that violates indentation


getting this above issue can you please make proper format of file and send me back entire correct file please dont alter any values and send me back the correct file



