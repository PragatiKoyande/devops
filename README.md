name: report-builder
namespace: backend

replicaCount: 1

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/report-builder-service
  tag: PR-01
  pullPolicy: Always

serviceAccount:
  name: report-builder-sa

service:
  name: report-builder-service
  port: 80
  targetPort: 8091

pdb:
  name: report-builder-pdb
  minAvailable: 1

autoscaling:
  name: report-builder-hpa
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

resources:
  requests:
    cpu: "3000m"
    memory: "4Gi"
  limits:
    cpu: "5000m"
    memory: "8Gi"

envFrom:
  configMaps:
    - redis-config
    - kafka-config
    - oracle-config
  secrets:
    - oracle-secret

extraEnv:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"
  - name: REPORT_BATCH_HDFS_BASE_PATH
    value: "/reports"
  - name: HADOOP_FS_URI
    value: "hdfs://10.190.224.102:8022"
  - name: HADOOP_FS_USER
    value: "root"
  - name: SPRING_KAFKA_BOOTSTRAP_SERVERS
    value: "kafka.backend.svc.cluster.local:9092"

secretEnv: []

hostAliases:
  - ip: "10.190.224.102"
    hostnames:
      - "fincore"
  - ip: "10.190.224.103"
    hostnames:
      - "fincore"
  - ip: "10.190.224.104"
    hostnames:
      - "fincore"
  - ip: "10.190.224.105"
    hostnames:
      - "fincore"
  - ip: "10.190.224.106"
    hostnames:
      - "fincore"

volumes: []
volumeMounts: []

topologySpreadConstraints:
  enabled: true

probes:
  readiness:
    initialDelaySeconds: 15
    periodSeconds: 5
    timeoutSeconds: 3
    failureThreshold: 3

  liveness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 3
    failureThreshold: 3

  startup:
    failureThreshold: 30
    periodSeconds: 10