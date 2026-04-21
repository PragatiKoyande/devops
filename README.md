name: common-master
namespace: backend

replicaCount: 1

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/common-master-service
  tag: PR-02
  pullPolicy: Always

serviceAccount:
  name: common-master-sa

service:
  name: common-master-service
  port: 80
  targetPort: 2000

autoscaling:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
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
    - oracle-config
  secrets:
    - oracle-secret

extraEnv: []
secretEnv: []

volumes: []
volumeMounts: []
hostAliases: []

podAnnotations:
  prometheus.io/scrape: "true"
  prometheus.io/port: "2000"

topologySpreadConstraints:
  - maxSkew: 1
    topologyKey: kubernetes.io/hostname
    whenUnsatisfiable: ScheduleAnyway
    labelSelector:
      matchLabels:
        app: common-master-backend