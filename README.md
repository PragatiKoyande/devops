namespace: backend

labels:
  app: report-builder-app

serviceAccount:
  name: report-builder-sa

deployment:
  name: report-builder-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  terminationGracePeriodSeconds: 30
  enableServiceLinks: false

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: report-builder-app

container:
  name: report-builder-container
  port: 8091
  imagePullPolicy: Always

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/report-builder-service
  tag: PR-01

envFrom:
  configMaps:
    - redis-config
    - kafka-config
    - oracle-config
  secrets:
    - oracle-secret

# keep empty here → env will come from env-specific files
env: []

# keep empty here → hostAliases will come from env-specific files
hostAliases: []

resources:
  requests:
    cpu: "3000m"
    memory: "4Gi"
  limits:
    cpu: "5000m"
    memory: "8Gi"

probes:
  port: 8091
  startup:
    failureThreshold: 30
    periodSeconds: 10
  liveness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 3
    failureThreshold: 3
  readiness:
    initialDelaySeconds: 15
    periodSeconds: 5
    timeoutSeconds: 3
    failureThreshold: 3

lifecycle:
  preStop:
    command: ["/bin/sh", "-c", "sleep 10"]

service:
  name: report-builder-service
  port: 80
  targetPort: 8091

hpa:
  name: report-builder-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70
  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

pdb:
  name: report-builder-pdb
  minAvailable: 1