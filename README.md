dashboard-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
    tag: DEV01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

journal-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
    tag: DEV04
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

transactions-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
    tag: DEV01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

user-service:
  enabled: true
  namespace: test-dev
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

process-status-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
    tag: SV16
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

enquiry-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/enquiry-service
    tag: DEV05
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

notification-service:
  enabled: true
  namespace: test-dev
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
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/nwsa-variance-service
    tag: DEV01
	image:
	  repository: h06vksharbor.corp.ad.sbi/cbops/nwsa-variance-service
      tag: DEV01
      imagePullPolicy: Always
    env:
      - name: SPRING_PROFILES_ACTIVE
        value: "dev"
      - name: NWSA_GENERATED_REPORT_ROOT
        value: "/reports"
      - name: NWSA_REPORT_ROOT
        value: "/reports"

    hostAliases:
      - ip: "10.189.42.83"
        hostnames:
          - "uatrootdc1.uatad.sbi"

react-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/react-service
    tag: DEV46
    imagePullPolicy: Always

redis-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/redis-server
    tag: latest
    imagePullPolicy: Always

report-builder-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/report-builder-service
    tag: DEV01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

report-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/report-service
    tag: DEV14
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

template-config-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/template-config-service
    tag: DEV01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

common-master-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-master-service
    tag: DEV05
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

common-request-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
    tag: DEV14
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"

login-service:
  enabled: true
  namespace: test-dev
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
	  
help-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/helpservice
    tag: DEV01
	imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"
  
ascii-generation-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
    tag: DEV-01
    imagePullPolicy: Always
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"
    
voucher-enquiry-service:
  enabled: true
  namespace: test-dev
  image:
    repository: h06vksharbor.corp.ad.sbi/cbops/voucher-enquiry-service
    tag: DEV01  
  env:
    - name: SPRING_PROFILES_ACTIVE
      value: "dev"  

  resolve indentation issue please dont alter anything else and send me back entire correct file
