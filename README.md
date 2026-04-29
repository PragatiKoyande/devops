namespace: backend

serviceAccount:
  name: nwsa-sa

deployment:
  name: nwsa-variance-deployment
  replicas: 2
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: nwsa-variance-backend

  serviceAccountName: nwsa-sa
  terminationGracePeriodSeconds: 30
  enableServiceLinks: false

  annotations:
    prometheus.io/scrape: "true"
    prometheus.io/port: "8093"

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: nwsa-variance-backend

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/nwsa-variance-service
  tag: PR-03

container:
  name: nwsa-variance-container
  port: 8093

resources:
  requests:
    cpu: "200m"
    memory: "256Mi"
  limits:
    cpu: "500m"
    memory: "512Mi"

probes:
  port: 8093

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

envFrom:
  - configMapRef:
      name: redis-config
  - configMapRef:
      name: kafka-config
  - configMapRef:
      name: oracle-config
  - secretRef:
      name: oracle-secret

service:
  name: nwsa-variance-service
  port: 80
  targetPort: 8093
  type: ClusterIP

hpa:
  name: nwsa-variance-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

pdb:
  name: nwsa-variance-pdb
  minAvailable: 1




image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/nwsa-variance-service
  tag: PR-03

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"
  - name: HADOOP_FS_HA_NN1
    value: "hdfs://10.190.224.102:8022"
  - name: HADOOP_FS_HA_NN2
    value: "hdfs://10.190.224.103:8022"
  - name: HADOOP_FS_HA_NN3
    value: "hdfs://10.190.224.104:8022"
  - name: HADOOP_FS_HA_NN4
    value: "hdfs://10.190.224.105:8022"
  - name: HADOOP_FS_HA_NN5
    value: "hdfs://10.190.224.106:8022"
  - name: NWSA_GENERATED_REPORT_ROOT
    value: "/reports"
  - name: NWSA_REPORT_ROOT
    value: "/reports"
  - name: HADOOP_FS_URI
    value: "hdfs://fincore:8022"
  - name: HADOOP_FS_USER
    value: "root"

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