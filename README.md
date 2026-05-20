dashboard:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
    tag: DEV01
	imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

journal:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
    tag: DEV04
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

transactions:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
    tag: DEV01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

user-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/user-service
    tag: DEV06
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"
  - name: JAVA_TOOL_OPTIONS
    value: "-Djava.net.preferIPv4Stack=true"
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "rbac-cache-group"
  hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"

process-status:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
    tag: SV16
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

enqiry-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/enquiry-service
    tag: DEV05
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

notification:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/notification-service
    tag: TEST-1
	imagePullPolicy: Always
  env:
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "notification-service-group"
  - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
    value: "earliest"
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

nwsa-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/nwsa-variance-service
    tag: DEV01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"
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
    repository: h06vksharbor.corp.ad.sbi/cbops/react-service
    tag: DEV46
	imagePullPolicy: Always

redis-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/redis-server
    tag: latest
	imagePullPolicy: Always

report-builder:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/report-builder-service
    tag: DEV01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

report-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/report-service
    tag: DEV14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

template-config:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/template-config-service
    tag: DEV01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

common-master:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-master-service
    tag: DEV05
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

common-request:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
    tag: DEV14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

login:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/login-service
    tag: DEV13
	imagePullPolicy: Always
  hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"


    this file is having indentation issue can you please correct it and send me back
