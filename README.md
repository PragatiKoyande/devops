apiVersion: v2
name: report-service
description: Report Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"



name: report
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/report-service
  tag: DEV16
  pullPolicy: Always

serviceAccount:
  name: report-sa

service:
  name: report-service
  port: 80
  targetPort: 9005

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
    - kafka-config
  secrets:
    - oracle-secret

extraEnv:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

secretEnv: []

hostAliases: []
volumes: []
volumeMounts: []