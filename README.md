namespace: backend

serviceAccount:
  name: notification-sa

deployment:
  name: notification-deployment
  replicas: 2
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: notification-backend

  serviceAccountName: notification-sa
  enableServiceLinks: false
  terminationGracePeriodSeconds: 30

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

  volumes:
    - name: tmp-dir
      emptyDir:
        medium: Memory
        sizeLimit: 64Mi

container:
  name: notification-container

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/notification-service
  tag: PR-01
  pullPolicy: Always

service:
  name: notification-service
  type: ClusterIP
  port: 80
  targetPort: 9010

probes:
  port: 9010

  startup:
    failureThreshold: 30
    periodSeconds: 10

  liveness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 3

  readiness:
    initialDelaySeconds: 15
    periodSeconds: 5

resources:
  requests:
    cpu: "200m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

volumeMounts:
  - name: tmp-dir
    mountPath: /tmp

envFrom:
  configMaps:
    - postgres-config
    - redis-config
    - kafka-config
  secrets:
    - postgres-secret

env:
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "notification-service-group"
  - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
    value: "earliest"
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"

lifecycle:
  preStop:
    command: ["/bin/sh","-c","sleep 10"]

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: true
  capabilities:
    drop:
      - ALL

hpa:
  name: notification-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70

pdb:
  name: notification-pdb
  minAvailable: 1

labels:
  app: notification-backend

-------

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/notification-service
  tag: DEV01

env:
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "notification-service-group"
  - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
    value: "earliest"
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

--------

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/notification-service
  tag: SIT01
--------

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/notification-service
  tag: UAT01

_---_------

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/notification-service
  tag: PR-01