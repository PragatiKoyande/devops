namespace: backend

serviceAccountName: process-status-sa
deploymentName: process-status-deployment
serviceName: process-status-service

appLabel: process-status-backend
containerName: process-status-container

replicaCount: 1
containerPort: 3000
servicePort: 80

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
  tag: SV16
  pullPolicy: Always

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

# only references (no creation)
redisConfigName: redis-config
oracleConfigName: oracle-config
oracleSecretName: oracle-secret

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

hpaName: process-status-hpa

pdb:
  enabled: true

pdbName: process-status-pdb