namespace: backend

serviceAccount:
  name: nwsa-sa

deployment:
  name: nwsa-variance-deployment
  replicas: 2
  revisionHistoryLimit: 5

  strategy:
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: nwsa-variance-backend

  annotations:
    prometheus:
      scrape: "true"
      port: "8093"

  container:
    name: nwsa-variance-container
    image: a2p05vksharbor.corp.ad.sbi/cbops/nwsa-variance-service:PR-03
    imagePullPolicy: Always
    port: 8093

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

    envFrom:
      configMaps:
        - redis-config
        - kafka-config
        - oracle-config
      secrets:
        - oracle-secret

    resources:
      requests:
        cpu: "200m"
        memory: "256Mi"
      limits:
        cpu: "500m"
        memory: "512Mi"

    probes:
      startup:
        port: 8093
        failureThreshold: 30
        periodSeconds: 10
      liveness:
        port: 8093
        initialDelaySeconds: 30
        periodSeconds: 10
        timeoutSeconds: 3
        failureThreshold: 3
      readiness:
        port: 8093
        initialDelaySeconds: 15
        periodSeconds: 5
        timeoutSeconds: 3
        failureThreshold: 3

    lifecycle:
      preStopSleep: 10

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

  topologySpreadConstraints:
    maxSkew: 1
    topologyKey: kubernetes.io/hostname

service:
  name: nwsa-variance-service
  port: 80
  targetPort: 8093

hpa:
  name: nwsa-variance-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70
  behavior:
    scaleUp: 60
    scaleDown: 300

pdb:
  name: nwsa-variance-pdb
  minAvailable: 1
