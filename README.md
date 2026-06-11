namespace: backend

serviceAccount:
  name: ascii-generation-sa
  automountServiceAccountToken: false

deployment:
  name: ascii-generation-deployment
  replicas: 1
  revisionHistoryLimit: 10
  terminationGracePeriodSeconds: 60

  labels:
    app: ascii-generation-backend

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: ascii-generation-backend

container:
  name: ascii-generation-container
  port: 8084

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
  tag: DEV-01
  imagePullPolicy: Always

envFrom:
  - configMapRef:
      name: kafka-config
  - configMapRef:
      name: redis-config
  - configMapRef:
      name: oracle-config
  - secretRef:
      name: oracle-secret
  - configMapRef:
      name: hadoop-config

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "1000m"
    memory: "1Gi"

probes:
  port: 8084

  startup:
    failureThreshold: 30
    periodSeconds: 10

  readiness:
    initialDelaySeconds: 20
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 3

  liveness:
    initialDelaySeconds: 60
    periodSeconds: 20
    timeoutSeconds: 5
    failureThreshold: 3

lifecycle:
  preStop:
    exec:
      command:
        - /bin/sh
        - -c
        - sleep 20

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: false
  capabilities:
    drop:
      - ALL

service:
  name: ascii-generation-service
  type: ClusterIP
  port: 80
  targetPort: 8084

hpa:
  name: ascii-generation-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

pdb:
  name: ascii-generation-pdb
  minAvailable: 1






image:
  repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
  tag: DEV-01
  imagePullPolicy: Always



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
  tag: SIT-01
  imagePullPolicy: Always




image:
  repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
  tag: UAT-01
  imagePullPolicy: Always




image:
  repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
  tag: PROD-01
  imagePullPolicy: Always