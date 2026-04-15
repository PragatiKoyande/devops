apiVersion: v2
name: journal-service
description: Journal Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"



name: journal-service

namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
  tag: DEV04
  pullPolicy: Always

serviceAccount:
  name: journal-sa
  automount: false

service:
  name: journal-service
  port: 80
  targetPort: 9999

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

autoscaling:
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  minAvailable: 1

envFrom:
  configMaps:
    - redis-config
    - oracle-config
  secrets:
    - oracle-secret