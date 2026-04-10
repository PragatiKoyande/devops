name: login
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/login-service
  tag: DEV13
  pullPolicy: Always

serviceAccount:
  name: login-sa

service:
  name: login-service
  port: 80
  targetPort: 8085
  type: ClusterIP

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

configMaps:
  - redis-config
  - oracle-config
  - ldap-config

secretRefs:
  - oracle-secret

extraSecrets:
  ldapCreds:
    name: ldap-creds
    key: truststore-password

volumes:
  truststore:
    secretName: ldap-truststore-file
    mountPath: /etc/fincore/secrets
    fileName: ad-truststore.jks

  logs:
    mountPath: /logs

hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"

env:
  SPRING_PROFILES_ACTIVE: dev
  JAVA_TOOL_OPTIONS: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  minAvailable: 1