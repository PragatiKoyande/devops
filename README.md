namespace: backend

serviceAccountName: transactions-sa
deploymentName: transactions-deployment
serviceName: transactions-service

appLabel: transactions-backend
containerName: transactions-container

replicaCount: 1
containerPort: 4000
servicePort: 80

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
  tag: DEV01
  pullPolicy: Always

# Existing configs & secrets
env:
  configMaps:
    redis: redis-config
    oracle: oracle-config
  secrets:
    oracle: oracle-secret

# Pod security
securityContext:
  runAsUser: 10001
  fsGroup: 10001

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

startupProbe:
  failureThreshold: 60
  periodSeconds: 10

livenessProbe:
  initialDelaySeconds: 90
  periodSeconds: 15
  timeoutSeconds: 5
  failureThreshold: 5

readinessProbe:
  initialDelaySeconds: 30
  periodSeconds: 10
  timeoutSeconds: 5
  failureThreshold: 5

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

hpaName: transactions-hpa

pdb:
  enabled: true

pdbName: transactions-pdb