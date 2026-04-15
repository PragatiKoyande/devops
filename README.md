apiVersion: v2
name: notification-service
description: Notification Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"




name: notification
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/notification-service
  tag: DEV01
  pullPolicy: Always

serviceAccount:
  name: notification-sa

service:
  name: notification-service
  port: 80
  targetPort: 8080   # change if your actual port differs

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

volumes: []
volumeMounts: []
hostAliases: []
