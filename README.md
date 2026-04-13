namespace: backend

app:
  name: common-request-backend

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: DEV14
  pullPolicy: Always

serviceAccount:
  name: common-request-sa

service:
  name: common-request-service
  port: 80
  targetPort: 9000

deployment:
  name: common-request-deployment
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
    - kafka-config
    - oracle-config
  secrets:
    - oracle-secret