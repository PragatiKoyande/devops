namespace: backend

name: common-request

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: DEV14
  pullPolicy: Always

serviceAccount:
  name: common-request-sa
  automount: false

service:
  name: common-request-service
  port: 80
  targetPort: 9000
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
  - kafka-config
  - oracle-config

secretRefs:
  - oracle-secret

securityContext:
  runAsUser: 10001
  fsGroup: 10001

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: false

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  minAvailable: 1