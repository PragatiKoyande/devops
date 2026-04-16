apiVersion: v2
name: template-config-service
description: Template Config Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"



name: template-config
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/template-config-service
  tag: DEV01
  pullPolicy: Always

serviceAccount:
  name: template-config-sa

service:
  name: template-config-service
  port: 80
  targetPort: 8090

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
  secrets:
    - oracle-secret

extraEnv: []
secretEnv: []

hostAliases: []
volumes: []
volumeMounts: []