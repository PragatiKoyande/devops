namespace: backend

serviceAccount:
  name: user-sa

pdb:
  name: user-pdb
  minAvailable: 1

deployment:
  name: user-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: user-backend

  serviceAccountName: user-sa
  terminationGracePeriodSeconds: 30
  enableServiceLinks: false

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

  volumes:
    - name: truststore-volume
      secret:
        secretName: ldap-truststore-file
        items:
          - key: ad-truststore.jks
            path: ad-truststore.jks

  container:
    name: user-container

    ports:
      - containerPort: 8087

    volumeMounts:
      - name: truststore-volume
        mountPath: /etc/fincore/secrets
        readOnly: true

    envFrom:
      - configMapRef:
          name: oracle-config
      - secretRef:
          name: oracle-secret
      - configMapRef:
          name: kafka-config
      - configMapRef:
          name: redis-config
      - configMapRef:
          name: ldap-config

    resources:
      requests:
        cpu: "250m"
        memory: "512Mi"
      limits:
        cpu: "500m"
        memory: "1Gi"

    probes:
      port: 8087

      startup:
        failureThreshold: 60
        periodSeconds: 10

      liveness:
        initialDelaySeconds: 90
        periodSeconds: 15
        timeoutSeconds: 5
        failureThreshold: 5

      readiness:
        initialDelaySeconds: 30
        periodSeconds: 10
        timeoutSeconds: 5
        failureThreshold: 5

    lifecycle:
      preStop:
        command: ["/bin/sh", "-c", "sleep 10"]

service:
  name: user-service
  type: ClusterIP
  port: 80
  targetPort: 8087

hpa:
  name: user-hpa
  minReplicas: 1
  maxReplicas: 5

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

  cpu:
    averageUtilization: 70




image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service
  tag: DEV06

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"
  - name: JAVA_TOOL_OPTIONS
    value: "-Djava.net.preferIPv4Stack=true"
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "rbac-cache-group"
  - name: LDAP_TRUSTSTORE_PASSWORD
    valueFrom:
      secretKeyRef:
        name: ldap-creds
        key: truststore-password

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





image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service
  tag: SIT

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

hostAliases: []



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service
  tag: UAT

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

hostAliases: []




image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service
  tag: PROD

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"

hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"