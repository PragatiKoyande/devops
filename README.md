namespace: backend

serviceAccount:
  name: transactions-sa
  automountServiceAccountToken: false

deployment:
  name: transactions-deployment
  replicas: 1

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: transactions-backend

  terminationGracePeriodSeconds: 30

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: transactions-backend

  securityContext:
    runAsNonRoot: true
    runAsUser: 10001
    fsGroup: 10001

container:
  name: transactions-container

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
  tag: DEV01
  imagePullPolicy: Always

envFrom:
  - configMapRef:
      name: redis-config
  - configMapRef:
      name: oracle-config
  - secretRef:
      name: oracle-secret

service:
  name: transactions-service
  port: 80
  targetPort: 4000

probes:
  port: 4000

  startup:
    port: 4000
    failureThreshold: 60
    periodSeconds: 10

  liveness:
    port: 4000
    initialDelaySeconds: 90
    periodSeconds: 15
    timeoutSeconds: 5
    failureThreshold: 5

  readiness:
    port: 4000
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 5

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

hpa:
  name: transactions-hpa
  minReplicas: 1
  maxReplicas: 3
  cpu: 70

pdb:
  name: transactions-pdb
  minAvailable: 1



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
  tag: DEV01



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
  tag: SIT01




image:
  repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
  tag: UAT01



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
  tag: PROD01


