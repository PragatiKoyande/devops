namespace: backend

serviceAccountName: user-sa
deploymentName: user-deployment
serviceName: user-service

appLabel: user-backend
containerName: user-container

replicaCount: 1
containerPort: 8087
servicePort: 80

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service
  tag: DEV06
  pullPolicy: Always

# Configs & Secrets
env:
  configMaps:
    oracle: oracle-config
    kafka: kafka-config
    redis: redis-config
    ldap: ldap-config
  secrets:
    oracle: oracle-secret

# Extra env
springProfile: "dev"
javaOpts: "-Djava.net.preferIPv4Stack=true"
kafkaGroup: "rbac-cache-group"

ldapSecret:
  name: ldap-creds
  key: truststore-password

# Host alias
hostAliases:
  ip: "10.189.42.83"
  hostname: "uatrootdc1.uatad.sbi"

# Volume config
volumes:
  truststore:
    secretName: ldap-truststore-file
    key: ad-truststore.jks
    path: ad-truststore.jks

volumeMounts:
  mountPath: /etc/fincore/secrets

# Security
securityContext:
  runAsUser: 1000
  runAsGroup: 1000
  fsGroup: 2000

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

startupProbe:
  failureThreshold: 60
  periodSeconds: 10

livenessProbe:
  initialDelaySeconds: 90
  periodSeconds: 15
  timeoutSeconds: 5
  failureThreshold: 5

readinessProbe:
  initialDelaySeconds: 30
  periodSeconds: 10
  timeoutSeconds: 5
  failureThreshold: 5

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

hpaName: user-hpa

pdb:
  enabled: true

pdbName: user-pdb