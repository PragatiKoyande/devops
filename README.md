namespace: backend

labels:
  app: report-builder-app

serviceAccount:
  name: report-builder-sa

deployment:
  name: report-builder-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  terminationGracePeriodSeconds: 30
  enableServiceLinks: false

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: report-builder-app

container:
  name: report-builder-container
  port: 8091
  imagePullPolicy: Always

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/report-builder-service
  tag: PR-01

envFrom:
  configMaps:
    - redis-config
    - kafka-config
    - oracle-config
  secrets:
    - oracle-secret

# keep empty here → env will come from env-specific files
env: []

# keep empty here → hostAliases will come from env-specific files
hostAliases: []

resources:
  requests:
    cpu: "3000m"
    memory: "4Gi"
  limits:
    cpu: "5000m"
    memory: "8Gi"

probes:
  port: 8091
  startup:
    failureThreshold: 30
    periodSeconds: 10
  liveness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 3
    failureThreshold: 3
  readiness:
    initialDelaySeconds: 15
    periodSeconds: 5
    timeoutSeconds: 3
    failureThreshold: 3

lifecycle:
  preStop:
    command: ["/bin/sh", "-c", "sleep 10"]

service:
  name: report-builder-service
  port: 80
  targetPort: 8091

hpa:
  name: report-builder-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70
  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

pdb:
  name: report-builder-pdb
  minAvailable: 1






_----------------
image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/report-builder-service
  tag: PR-01

hostAliases:
- ip: "10.190.224.102"
  hostnames: ["fincore"]
- ip: "10.190.224.103"
  hostnames: ["fincore"]
- ip: "10.190.224.104"
  hostnames: ["fincore"]
- ip: "10.190.224.105"
  hostnames: ["fincore"]
- ip: "10.190.224.106"
  hostnames: ["fincore"]

env:
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

----------
image:
  repository: h06vksharbor.corp.ad.sbi/cbops/report-builder-service
  tag: UAT14

hostAliases:
- ip: "10.190.224.102"
  hostnames: ["fincore"]
- ip: "10.190.224.103"
  hostnames: ["fincore"]
- ip: "10.190.224.104"
  hostnames: ["fincore"]
- ip: "10.190.224.105"
  hostnames: ["fincore"]
- ip: "10.190.224.106"
  hostnames: ["fincore"]

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"
  - name: REPORT_BATCH_HDFS_BASE_PATH
    value: "/reports"
  - name: HADOOP_FS_URI
    value: "hdfs://10.190.224.102:8022"
  - name: HADOOP_FS_USER
    value: "root"
  - name: SPRING_KAFKA_BOOTSTRAP_SERVERS
    value: "kafka.backend.svc.cluster.local:9092"