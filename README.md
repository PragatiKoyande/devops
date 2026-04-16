apiVersion: v2
name: user-service
description: User Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"



name: user
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service
  tag: DEV06
  pullPolicy: Always

serviceAccount:
  name: user-sa

service:
  name: user-service
  port: 80
  targetPort: 8087

autoscaling:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

pdb:
  enabled: true
  minAvailable: 1

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

envFrom:
  configMaps:
    - oracle-config
    - kafka-config
    - redis-config
    - ldap-config
  secrets:
    - oracle-secret

extraEnv:
  - name: SPRING_PROFILES_ACTIVE
    value: dev
  - name: JAVA_TOOL_OPTIONS
    value: "-Djava.net.preferIPv4Stack=true"
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "rbac-cache-group"

secretEnv:
  - name: LDAP_TRUSTSTORE_PASSWORD
    secretName: ldap-creds
    key: truststore-password

hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"

volumes:
  - name: truststore-volume
    secret:
      secretName: ldap-truststore-file
      items:
        - key: ad-truststore.jks
          path: ad-truststore.jks

volumeMounts:
  - name: truststore-volume
    mountPath: /etc/fincore/secrets
    readOnly: true