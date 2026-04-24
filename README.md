namespace: backend

serviceAccount:
  enabled: true
  name: common-request-sa
  automountServiceAccountToken: false

deployment:
  name: common-request-deployment
  replicas: 1

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: common-request-backend

  serviceAccountName: common-request-sa
  terminationGracePeriodSeconds: 30

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: common-request-backend

  securityContext:
    runAsNonRoot: true
    runAsUser: 10001
    fsGroup: 10001

container:
  name: common-request-container

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: PR-02
  pullPolicy: Always

service:
  name: common-request-service
  type: ClusterIP
  port: 80
  targetPort: 9000

probes:
  port: 9000

  startup:
    failureThreshold: 60
    periodSeconds: 10

  liveness:
    initialDelaySeconds: 90
    periodSeconds: 15
    timeoutSeconds: 5
    failureThreshold: 5

  readiness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 5

resources:
  requests:
    cpu: "200m"
    memory: "256Mi"
  limits:
    cpu: "500m"
    memory: "512Mi"

envFrom:
  configMaps:
    - redis-config
    - kafka-config
    - oracle-config
  secrets:
    - oracle-secret

lifecycle:
  preStop:
    command: ["/bin/sh", "-c", "sleep 10"]

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: false
  capabilities:
    drop:
      - ALL

hpa:
  enabled: true
  name: common-request-hpa
  minReplicas: 1
  maxReplicas: 3

  metrics:
    cpu:
      targetAverageUtilization: 70

pdb:
  enabled: true
  name: common-request-pdb
  minAvailable: 1

labels:
  app: common-request-backend



--------

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: PR-02-dev


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: PR-02-sit


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: PR-02-uat


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: PR-02



