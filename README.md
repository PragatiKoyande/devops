namespace: backend

labels:
  app: redis-server

serviceAccount:
  name: redis-sa

deployment:
  name: redis-deployment
  replicas: 2
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  terminationGracePeriodSeconds: 30
  enableServiceLinks: false

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: redis-server

container:
  name: redis-container

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/redis/redis-stack-server
  tag: latest

env:
  - name: ALLOW_EMPTY_PASSWORD
    value: "yes"

service:
  name: redis-service
  type: ClusterIP
  port: 6379
  targetPort: 6379

hpa:
  name: redis-hpa
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70
  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

pdb:
  name: redis-pdb
  minAvailable: 1

resources:
  requests:
    cpu: "100m"
    memory: "128Mi"
  limits:
    cpu: "300m"
    memory: "512Mi"

probes:
  port: 6379

  startup:
    failureThreshold: 30
    periodSeconds: 10

  liveness:
    initialDelaySeconds: 20
    periodSeconds: 10
    timeoutSeconds: 3
    failureThreshold: 3

  readiness:
    initialDelaySeconds: 10
    periodSeconds: 5
    timeoutSeconds: 3
    failureThreshold: 3

lifecycle:
  preStop:
    command: ["/bin/sh", "-c", "sleep 10"]




image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/redis/redis-stack-server
  tag: DEV


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/redis/redis-stack-server
  tag: SIT


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/redis/redis-stack-server
  tag: UAT


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/redis/redis-stack-server
  tag: latest