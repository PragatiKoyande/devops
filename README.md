apiVersion: v2
name: process-status
description: Process Status Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"


name: process-status
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
  tag: latest
  pullPolicy: Always

serviceAccount:
  name: process-status-sa

service:
  name: process-status-service
  port: 80
  targetPort: 3000

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

volumes:
  - name: tmp-dir
    emptyDir:
      medium: Memory
      sizeLimit: 64Mi

volumeMounts:
  - name: tmp-dir
    mountPath: /tmp

extraEnv: []
secretEnv: []

hostAliases: []