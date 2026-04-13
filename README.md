namespace: backend

app:
  name: common-master-backend

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/common-master-service
  tag: DEV02   # default (overridden per env)
  pullPolicy: Always

serviceAccount:
  name: common-master-sa

service:
  name: common-master-service
  port: 80
  targetPort: 2000

deployment:
  name: common-master-deployment
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
  maxReplicas: 5
  cpu: 70

envFrom:
  configMaps:
    - redis-config
    - oracle-config
  secrets:
    - oracle-secret