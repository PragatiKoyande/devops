apiVersion: v2
name: react-service
description: React Frontend Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"



name: reactive-app
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/react-service
  tag: latest
  pullPolicy: Always

serviceAccount:
  name: react-app-sa

service:
  name: react-service
  port: 80
  targetPort: 80

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

# No envFrom, volumes for this service
envFrom:
  configMaps: []
  secrets: []

volumes: []
volumeMounts: []
hostAliases: []

extraEnv: []
secretEnv: []