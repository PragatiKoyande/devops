dashboard:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
    tag: UAT01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

journal:
  enabled: true
  image:
    tag: UAT01
	imagePullPolicy: Always
	repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

transactions:
  enabled: true
  image:
    tag: UAT01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

user-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/user-service
    tag: UAT06
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"
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
    tag: UAT16
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

enqiry-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/enquiry-service
    tag: UAT03
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

notification:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/notification-service
    tag: UAT05
	imagePullPolicy: Always
  env:
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "notification-service-group"
  - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
    value: "earliest"
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

nwsa-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/nwsa-variance-service
    tag: UAT01
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"
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
    tag: UAT33
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
    tag: UAT14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

report-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/report-service
    tag: UAT14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

template-config:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/template-config-service
    tag: UAT14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

common-master:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-master-service
    tag: UAT14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

common-request:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
    tag: UAT14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

login:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/login-service
    tag: UAT14
	imagePullPolicy: Always
  env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"
  hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"
   
  tehre is indenattion issue please fix it and send me back the entire file
