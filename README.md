namespace: backend

serviceAccount:
  name: template-config-sa

deployment:
  name: template-config-deployment
  replicas: 2
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: template-app

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
          app: template-app

container:
  name: template-config-container
  port: 8090

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/template-config-service
  tag: PR-06

envFrom:
  configMaps:
    - redis-config
    - oracle-config
  secrets:
    - oracle-secret

resources:
  requests:
    cpu: "200m"
    memory: "256Mi"
  limits:
    cpu: "500m"
    memory: "512Mi"

probes:
  port: 8090
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
  preStop: ["sleep 10"]

service:
  name: template-config-service
  type: ClusterIP
  port: 80
  targetPort: 8090

hpa:
  name: template-config-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70
  behavior:
    scaleUp: 60
    scaleDown: 300

pdb:
  name: template-config-pdb
  minAvailable: 1




image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/template-config-service
  tag: DEV14

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"




image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/template-config-service
  tag: SIT14

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"



image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/template-config-service
  tag: UAT14

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"




image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/template-config-service
  tag: PR-06

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"