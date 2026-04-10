namespace: backend

serviceAccountName: report-builder-sa
deploymentName: report-builder-deployment
serviceName: report-builder-service

appLabel: report-builder-app
containerName: report-builder-container

replicaCount: 1
containerPort: 8091
servicePort: 80

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/report-builder-service
  tag: DEV01
  pullPolicy: Always

# ✅ Existing configs & secrets (NOT created by Helm)
env:
  configMaps:
    redis: redis-config
    oracle: oracle-config
    hadoop: hadoop-config
  secrets:
    oracle: oracle-secret

# ✅ Security (important - kept from your manifest)
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

hpaName: report-builder-hpa

pdb:
  enabled: true

pdbName: report-builder-pdb