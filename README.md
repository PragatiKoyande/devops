namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
  tag: SV16
  pullPolicy: Always

service:
  port: 80
  targetPort: 3000

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

hpa:
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

redis:
  host: redis-service
  port: "6379"

oracle:
  url: jdbc:oracle:thin:@10.177.179.85:1523/fincorepdb1
  driver: oracle.jdbc.OracleDriver
  username: fincore
  password: Password#1234