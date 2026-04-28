namespace: backend

serviceAccount:
  name: report-sa

deployment:
  name: report-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: report-backend

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
          app: report-backend

container:
  name: report-container
  port: 9005

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/report-service
  tag: PR-11

envFrom:
  configMaps:
    - redis-config
    - kafka-config
    - oracle-config
  secrets:
    - oracle-secret

resources:
  requests:
    memory: "20Gi"
    cpu: "2000m"
  limits:
    memory: "24Gi"
    cpu: "4000m"

probes:
  port: 9005
  startup:
    failureThreshold: 60
    periodSeconds: 10
  liveness:
    initialDelaySeconds: 90
    periodSeconds: 15
    timeoutSeconds: 5
    failureThreshold: 5
  readiness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 5

lifecycle:
  preStop: ["sleep 10"]

service:
  name: report-service
  type: ClusterIP
  port: 80
  targetPort: 9005

hpa:
  name: report-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70
  behavior:
    scaleUp: 60
    scaleDown: 300

pdb:
  name: report-pdb
  minAvailable: 1


-------

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/report-service
  tag: DEV14

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
    value: "dev"
  - name: HADOOP_FS_URI
    value: "hdfs://10.190.224.102:8022"
  - name: HADOOP_FS_USER
    value: "root"
  - name: JAVA_OPTS
    value: "-Xms16g -Xmx16g -XX:+UseG1GC -XX:MaxDirectMemorySize=6g"

-----

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/report-service
  tag: PR-11

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
  - name: HADOOP_FS_URI
    value: "hdfs://10.190.224.102:8022"
  - name: HADOOP_FS_USER
    value: "root"
  - name: JAVA_OPTS
    value: "-Xms16g -Xmx16g -XX:+UseG1GC -XX:MaxDirectMemorySize=6g"


