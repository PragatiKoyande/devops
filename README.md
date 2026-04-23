namespace: backend

serviceAccount:
  name: report-sa

deployment:
  name: report-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: report-backend

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

  hostAliases: []

  volumes: []

  container:
    name: report-container
    image: h06vksharbor.corp.ad.sbi/cbops/report-service:DEV16
    imagePullPolicy: Always

    port: 9005

    volumeMounts: []

    env:
      - name: SPRING_PROFILES_ACTIVE
        value: "dev"

    envFrom:
      configMaps:
        - redis-config
        - oracle-config
        - kafka-config
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
        port: 9005
        failureThreshold: 60
        periodSeconds: 10

      liveness:
        port: 9005
        initialDelaySeconds: 90
        periodSeconds: 15
        timeoutSeconds: 5
        failureThreshold: 5

      readiness:
        port: 9005
        initialDelaySeconds: 30
        periodSeconds: 10
        timeoutSeconds: 5
        failureThreshold: 5

    lifecycle:
      preStopSleep: 10


service:
  name: report-service
  port: 80
  targetPort: 9005


hpa:
  name: report-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70
  behavior:
    scaleUpStabilization: 60
    scaleDownStabilization: 300


pdb:
  enabled: true
  name: report-pdb
  minAvailable: 1