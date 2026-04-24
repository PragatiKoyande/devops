namespace: backend

serviceAccount:
  name: login-sa
  automountServiceAccountToken: false

deployment:
  name: login-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: login-backend

  pod:
    serviceAccountName: login-sa
    terminationGracePeriodSeconds: 30
    enableServiceLinks: false

    securityContext:
      runAsNonRoot: true
      runAsUser: 10001
      fsGroup: 10001

    hostAliases: []   # overridden per env

    volumes:
      - name: truststore-volume
        secret:
          secretName: ldap-truststore-file
          items:
            - key: ad-truststore.jks
              path: ad-truststore.jks

      - name: logs-volume
        emptyDir: {}

container:
  name: login-backend-container

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/login-service
  tag: PR-03

ports:
  containerPort: 8085

volumeMounts:
  - name: truststore-volume
    mountPath: /etc/fincore/secrets
    readOnly: true
  - name: logs-volume
    mountPath: /logs

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"

envFrom:
  configMaps:
    - redis-config
    - oracle-config
    - ldap-config
  secrets:
    - oracle-secret
    - ldap-secret

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

probes:
  port: 8085

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

lifecycle:
  preStop:
    command: ["/bin/sh", "-c", "sleep 10"]

securityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: false
  capabilities:
    drop:
      - ALL

service:
  name: login-service
  port: 80
  targetPort: 8085

hpa:
  name: login-hpa
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  name: login-pdb
  minAvailable: 1


-------


image:
  repository: h06vksharbor.corp.ad.sbi/cbops/login-service
  tag: DEV13

hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"


-------

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/login-service
  tag: SIT01

hostAliases:
  - ip: "10.189.42.90"
    hostnames:
      - "sitdc1.sitad.sbi"

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"


------

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/login-service
  tag: UAT01

hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

-----

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/login-service
  tag: PR-03

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

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"