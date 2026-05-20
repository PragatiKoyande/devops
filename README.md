dashboard:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/dashboard-service
    tag: PROD01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"

journal:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/journal-service
    tag: PROD01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"

transactions:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/transactions-service
    tag: PR-01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"

user-service:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/user-servic
    tag: PR-05
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"
    - name: JAVA_TOOL_OPTIONS
      value: "-Djava.net.preferIPv4Stack=true"
    - name: SPRING_KAFKA_CONSUMER_GROUP_ID
      value: "rbac-cache-group"
  hostAliases:
    - ip: "10.176.53.145"
      hostnames:
        - "corp.ad.sbi"
        - "corpdcmdgbl01.corp.ad.sbi"
    - ip: "10.176.54.30"
      hostnames:
        - "corpdcmdgbl02.corp.ad.sbi"
    - ip: "10.176.54.31"
      hostnames:
        - "corpdcmdgbl03.corp.ad.sbi"
    - ip: "10.176.54.32"
      hostnames:
        - "corpdcmdgbl04.corp.ad.sbi"
    - ip: "10.189.37.135"
      hostnames:
        - "corpdcmdrbl01.corp.ad.sbi"
    - ip: "10.189.37.136"
      hostnames:
        - "corpdcmdrbl02.corp.ad.sbi"
    - ip: "10.189.37.137"
      hostnames:
        - "corpdcmdrbl03.corp.ad.sbi"
    - ip: "10.189.37.138"
      hostnames:
        - "corpdcmdrbl04.corp.ad.sbi"

process-status:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/process-status-service
    tag: PR-07
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"

enqiry-service:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/enquiry-service
    tag: PR-01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"

notification:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/notification-service
    tag: PR-01
    imagePullPolicy: Always
  env:
    - name: SPRING_KAFKA_CONSUMER_GROUP_ID
      value: "notification-service-group"
    - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
      value: "earliest"
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"

nwsa-service:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/nwsa-variance-service
    tag: PR-03
    imagePullPolicy: Always
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

react-service:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/react-service
    tag: PR-16
    imagePullPolicy: Always

redis-service:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/redis/redis-stack-server
    tag: latest
    imagePullPolicy: Always

report-builder:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/report-builder-service
    tag: PR-01
    imagePullPolicy: Always
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

report-service:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/report-service
    tag: PR-11
    imagePullPolicy: Always
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
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"
    - name: HADOOP_FS_URI
      value: "hdfs://10.190.224.102:8022"
    - name: HADOOP_FS_USER
      value: "root"
    - name: JAVA_OPTS
      value: "-Xms16g -Xmx16g -XX:+UseG1GC -XX:MaxDirectMemorySize=6g"

template-config:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/template-config-service
    tag: PR-06
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"

common-master:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/common-master-service
    tag: PR-02
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"

common-request:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/common-request-service
    tag: PR-02
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"

login:
  enabled: true
  image:
    repository: a2p05vksharbor.corp.ad.sbi/cbops/login-service
    tag: PR-03
    imagePullPolicy: Always
  hostAliases:
    - ip: "10.176.53.145"
      hostnames:
        - "corp.ad.sbi"
        - "corpdcmdgbl01.corp.ad.sbi"
    - ip: "10.176.54.30"
      hostnames:
        - "corpdcmdgbl02.corp.ad.sbi"
    - ip: "10.176.54.31"
      hostnames:
        - "corpdcmdgbl03.corp.ad.sbi"
    - ip: "10.176.54.32"
      hostnames:
        - "corpdcmdgbl04.corp.ad.sbi"
    - ip: "10.189.37.135"
      hostnames:
        - "corpdcmdrbl01.corp.ad.sbi"
    - ip: "10.189.37.136"
      hostnames:
        - "corpdcmdrbl02.corp.ad.sbi"
    - ip: "10.189.37.137"
      hostnames:
        - "corpdcmdrbl03.corp.ad.sbi"
    - ip: "10.189.37.138"
      hostnames:
        - "corpdcmdrbl04.corp.ad.sbi"
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "prod"