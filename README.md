dashboard-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
    tag: SIT01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

journal-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
    tag: SIT01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

transactions-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
    tag: SIT01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

user-service:
  enabled: true
  namespace: test-sit
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

process-status-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
    tag: SIT16
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

enquiry-service:
  enabled: true
  namespace: test-sit
  image:
    tag: SIT01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

notification-service:
  enabled: true
  namespace: test-sit
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
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/nwsa-variance-service
    tag: SIT01
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"
    - name: HADOOP_FS_USER
      value: "root"
    - name: GLIF_REPORTS_BASE_PATH
      value: "/reports"
  hostAliases:
  - ip: "10.189.42.83"
    hostnames:
    - "uatrootdc1.uatad.sbi"
  
react-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/react-service
    tag: SIT48
    imagePullPolicy: Always

redis-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/redis-server
    tag: latest
    imagePullPolicy: Always

report-builder-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/report-builder-service
    tag: SIT14
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

report-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/report-service
    tag: SIT14
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

template-config-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/template-config-service
    tag: SIT14
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

common-master-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
    tag: SIT16
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

common-request-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
    tag: SIT16
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"

login-service:
  enabled: true
  namespace: test-sit
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
	  
help-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/helpservice
    tag: SIT01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"
  
ascii-generation-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
    tag: SIT-01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"
  
voucher-enquiry-service:
  enabled: true
  namespace: test-sit
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/voucher-enquiry-service
    tag: SIT01
	imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "sit"


indentation issue please dont alter any values only resolve the error and send me back entire correct file
