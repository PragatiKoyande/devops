namespace: backend

serviceAccountName: template-config-sa
deploymentName: template-config-deployment
serviceName: template-config-service

appLabel: template-app
containerName: template-config-container

replicaCount: 1
containerPort: 8090
servicePort: 80

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/template-config-service
  tag: DEV01
  pullPolicy: Always

# Existing configs & secrets
env:
  configMaps:
    redis: redis-config
    oracle: oracle-config
  secrets:
    oracle: oracle-secret

# Security
securityContext:
  runAsUser: 1000
  runAsGroup: 1000
  fsGroup: 2000

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

startupProbe:
  failureThreshold: 30
  periodSeconds: 10

livenessProbe:
  initialDelaySeconds: 30
  periodSeconds: 10
  timeoutSeconds: 3
  failureThreshold: 3

readinessProbe:
  initialDelaySeconds: 15
  periodSeconds: 5
  timeoutSeconds: 3
  failureThreshold: 3

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

hpaName: template-config-hpa

pdb:
  enabled: true

pdbName: template-config-pdb