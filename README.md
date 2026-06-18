dashboard-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
    tag: UAT01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"

journal-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
    tag: UAT01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"

transactions-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
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

process-status-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
    tag: UAT16
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"

enquiry-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/enquiry-service
    tag: UAT03
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"

notification-service:
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

report-builder-service:
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

template-config-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/template-config-service
    tag: UAT14
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"

common-master-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-master-service
    tag: UAT14
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"

common-request-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
    tag: UAT14
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"

login-service:
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

help-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/helpservice
    tag: UAT01
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"

ascii-generation-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
    tag: UAT-01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"

voucher-enquiry-service:
  enabled: true
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/voucher-enquiry-service
    tag: UAT01
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "uat"