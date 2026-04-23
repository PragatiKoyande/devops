namespace: backend

serviceAccount:
  name: user-sa

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

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

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

  container:
    name: user-container
    image: h06vksharbor.corp.ad.sbi/cbops/user-service:DEV06
    imagePullPolicy: Always
    port: 8087

    volumeMounts:
      - name: truststore-volume
        mountPath: /etc/fincore/secrets
        readOnly: true

    env:
      - name: SPRING_PROFILES_ACTIVE
        value: dev
      - name: JAVA_TOOL_OPTIONS
        value: "-Djava.net.preferIPv4Stack=true"
      - name: SPRING_KAFKA_CONSUMER_GROUP_ID
        value: "rbac-cache-group"

    envFrom:
      configMaps:
        - oracle-config
        - kafka-config
        - redis-config
        - ldap-config
      secrets:
        - oracle-secret

    resources:
      requests:
        cpu: "250m"
        memory: "512Mi"
      limits:
        cpu: "500m"
        memory: "1Gi"

    probes:
      startup:
        port: 8087
        failureThreshold: 60
        periodSeconds: 10

      liveness:
        port: 8087
        initialDelaySeconds: 90
        periodSeconds: 15
        timeoutSeconds: 5
        failureThreshold: 5

      readiness:
        port: 8087
        initialDelaySeconds: 30
        periodSeconds: 10
        timeoutSeconds: 5
        failureThreshold: 5

    lifecycle:
      preStopSleep: 10

service:
  name: user-service
  port: 80
  targetPort: 8087

hpa:
  name: user-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70
  behavior:
    scaleUpStabilization: 60
    scaleDownStabilization: 300

pdb:
  enabled: true
  name: user-pdb
  minAvailable: 1