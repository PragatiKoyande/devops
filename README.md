namespace: backend

serviceAccountName: report-sa
deploymentName: report-deployment
serviceName: report-service

appLabel: report-backend
containerName: report-container

replicaCount: 1
containerPort: 9005
servicePort: 80

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/report-service
  tag: DEV16
  pullPolicy: Always

# Existing configs & secrets
env:
  configMaps:
    redis: redis-config
    oracle: oracle-config
    kafka: kafka-config
  secrets:
    oracle: oracle-secret

# Spring profile
springProfile: "dev"

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
  maxReplicas: 5
  cpuUtilization: 70

hpaName: report-hpa

pdb:
  enabled: true

pdbName: report-pdb