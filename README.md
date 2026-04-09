namespace: backend

name: common-master

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/common-master-service
  tag: DEV02
  pullPolicy: Always

serviceAccount:
  name: common-master-sa

service:
  name: common-master-service
  port: 80
  targetPort: 2000
  type: ClusterIP

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

configMaps:
  - redis-config
  - oracle-config

secretRefs:
  - oracle-secret

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

pdb:
  minAvailable: 1