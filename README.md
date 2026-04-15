apiVersion: v2
name: login-service
description: Login Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"


name: login-service

namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/login-service
  tag: DEV13
  pullPolicy: Always

serviceAccount:
  name: login-sa
  automount: false

service:
  name: login-service
  port: 80
  targetPort: 8085

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

autoscaling:
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  minAvailable: 1

envFrom:
  configMaps:
    - redis-config
    - oracle-config
    - ldap-config
  secrets:
    - oracle-secret

extraEnv:
  - name: SPRING_PROFILES_ACTIVE
    value: dev
  - name: JAVA_TOOL_OPTIONS
    value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"

secretEnv:
  - name: LDAP_TRUSTSTORE_PASSWORD
    secretName: ldap-creds
    key: truststore-password

volumes:
  - name: truststore-volume
    secret:
      secretName: ldap-truststore-file

  - name: logs-volume
    emptyDir: {}

volumeMounts:
  - name: truststore-volume
    mountPath: /etc/fincore/secrets
    readOnly: true

  - name: logs-volume
    mountPath: /logs

hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"