namespace: backend

app:
  name: dashboard-backend

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
  tag: DEV01
  pullPolicy: Always

serviceAccount:
  name: dashboard-sa

service:
  name: dashboard-service
  port: 80
  targetPort: 9015

deployment:
  name: dashboard-deployment
  replicas: 1

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

autoscaling:
  enabled: true
  minReplicas: 1
  maxReplicas: 3
  cpu: 70

envFrom:
  configMaps:
    - redis-config
    - oracle-config
  secrets:
    - oracle-secret