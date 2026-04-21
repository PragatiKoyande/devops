name: login
namespace: backend

replicaCount: 1

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/login-service
  tag: PR-03
  pullPolicy: Always

serviceAccount:
  name: login-sa
  automount: false

service:
  name: login-service
  port: 80
  targetPort: 8085

pdb:
  name: login-pdb
  minAvailable: 1

autoscaling:
  name: login-hpa
  enabled: true
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

envFrom:
  configMaps:
    - redis-config
    - oracle-config
    - ldap-config
  secrets:
    - oracle-secret
    - ldap-secret

extraEnv:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"
  - name: JAVA_TOOL_OPTIONS
    value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"

secretEnv: []

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

volumes:
  - name: truststore-volume
    secret:
      secretName: ldap-truststore-file
      items:
        - key: ad-truststore.jks
          path: ad-truststore.jks

  - name: logs-volume
    emptyDir: {}

volumeMounts:
  - name: truststore-volume
    mountPath: /etc/fincore/secrets
    readOnly: true

  - name: logs-volume
    mountPath: /logs

probes:
  readiness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 5

  liveness:
    initialDelaySeconds: 90
    periodSeconds: 15
    timeoutSeconds: 5
    failureThreshold: 5

  startup:
    failureThreshold: 60
    periodSeconds: 10