dashboard:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
    tag: SIT01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

journal:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
    tag: SIT01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

transactions:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
    tag: SIT01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

user-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/user-service
    tag: SIT06
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"
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
    tag: SIT16
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

enqiry-service:
  enabled: true
  image:
    tag: SIT01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

notification:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/enquiry-service
    tag: SIT03
	imagePullPolicy: Always
  env:
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "notification-service-group"
  - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
    value: "earliest"
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

nwsa-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/nwsa-variance-service
    tag: SIT01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"
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
    tag: SIT48
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
    tag: SIT14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

report-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/report-service
    tag: SIT14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

template-config:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/template-config-service
    tag: SIT14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

common-master:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
    tag: SIT16
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

common-request:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
    tag: SIT16
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

login:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/login-service
    tag: SIT03
	imagePullPolicy: Always
  hostAliases:
  - ip: "10.189.42.90"
    hostnames:
      - "uatrootdc1.uatad.sbi"
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"


      there is indentation issue please resolve the issue and send me back the entire file:
      
