name: dashboard
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
  tag: DEV01
  pullPolicy: Always

serviceAccount:
  name: dashboard-sa

service:
  name: dashboard-service
  port: 80
  targetPort: 9015
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
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  minAvailable: 1