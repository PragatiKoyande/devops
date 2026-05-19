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
  ------------------------------------------------------

  image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/user-service
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
   
    --------------------------------------

    for all env i m aving separate values.yaml
