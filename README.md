namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service
  tag: UAT10
  pullPolicy: Always

serviceAccount:
  name: user-sa

service:
  name: user-service
  port: 80
  targetPort: 8087
  type: ClusterIP

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

env:
  SPRING_PROFILES_ACTIVE: uat
  JAVA_TOOL_OPTIONS: "-Djava.net.preferIPv4Stack=true"
  SPRING_KAFKA_CONSUMER_GROUP_ID: "rbac-cache-group"

secrets:
  ldapTruststoreSecret: ldap-truststore-file
  ldapCredsSecret: ldap-creds

configMaps:
  - oracle-config
  - kafka-config
  - redis-config
  - ldap-config

secretRefs:
  - oracle-secret
  - ldap-secret

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

pdb:
  minAvailable: 1
