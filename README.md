apiVersion: v2
name: transactions-service
description: Transactions Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"




name: transactions
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
  tag: DEV01
  pullPolicy: Always

serviceAccount:
  name: transactions-sa
  automount: false

service:
  name: transactions-service
  port: 80
  targetPort: 4000

autoscaling:
  enabled: true
  minReplicas: 1
  maxReplicas: 3
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