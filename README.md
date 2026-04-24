namespace: backend

serviceAccount:
  enabled: true
  name: common-master-sa

deployment:
  name: common-master-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: common-master-backend

  annotations:
    prometheus.io/scrape: "true"
    prometheus.io/port: "2000"

  serviceAccountName: common-master-sa
  terminationGracePeriodSeconds: 30
  enableServiceLinks: false

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: common-master-backend

container:
  name: common-master-container

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-master-service
  tag: PR-02
  pullPolicy: Always

service:
  name: common-master-service
  type: ClusterIP
  port: 80
  targetPort: 2000

probes:
  port: 2000

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
    - oracle-config
  secrets:
    - oracle-secret

lifecycle:
  preStop:
    command: ["/bin/sh", "-c", "sleep 10"]

hpa:
  enabled: true
  name: common-master-hpa

  minReplicas: 1
  maxReplicas: 5

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

  metrics:
    cpu:
      targetAverageUtilization: 70

pdb:
  enabled: true
  name: common-master-pdb
  minAvailable: 1

labels:
  app: common-master-backend



_---------

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-master-service
  tag: PR-02-dev


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-master-service
  tag: PR-02-sit




image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-master-service
  tag: PR-02-uat


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-master-service
  tag: PR-02