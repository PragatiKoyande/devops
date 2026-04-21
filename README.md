name: common-request
namespace: backend

replicaCount: 1

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: PR-02
  pullPolicy: Always

serviceAccount:
  name: common-request-sa

service:
  name: common-request-service
  port: 80
  targetPort: 9000

autoscaling:
  enabled: true
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  enabled: true
  minAvailable: 1

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

extraEnv: []
secretEnv: []

volumes: []
volumeMounts: []
hostAliases: []

topologySpreadConstraints:
  - maxSkew: 1
    topologyKey: kubernetes.io/hostname
    whenUnsatisfiable: ScheduleAnyway
    labelSelector:
      matchLabels:
        app: common-request-backend