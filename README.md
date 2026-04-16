apiVersion: v2
name: report-builder
description: Report Builder Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"


name: report-builder-app
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/report-builder-service
  tag: latest
  pullPolicy: Always

serviceAccount:
  name: report-builder-sa

service:
  name: report-builder-service
  port: 80
  targetPort: 8091

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
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

envFrom:
  configMaps:
    - redis-config
    - oracle-config
    - hadoop-config
  secrets:
    - oracle-secret

volumes: []
volumeMounts: []
hostAliases: []

extraEnv: []
secretEnv: []