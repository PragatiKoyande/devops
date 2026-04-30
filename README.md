namespace: backend

serviceAccount:
  name: journal-sa
  automountServiceAccountToken: false

deployment:
  name: journal-deployment
  replicas: 1

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: journal-app

  terminationGracePeriodSeconds: 30

  securityContext:
    runAsNonRoot: true
    runAsUser: 10001
    fsGroup: 10001

  topologySpreadConstraints:
    maxSkew: 1
    topologyKey: kubernetes.io/hostname

container:
  name: journal-app-container

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
  tag: DEV04
  pullPolicy: Always

envFrom:
  - configMapRef:
      name: redis-config
  - configMapRef:
      name: oracle-config
  - secretRef:
      name: oracle-secret

ports:
  containerPort: 9999

probes:
  port: 9999
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

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: false
  capabilities:
    drop:
      - ALL

service:
  name: journal-service
  port: 80
  targetPort: 9999

hpa:
  name: journal-hpa
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  name: journal-pdb
  minAvailable: 1





image:
  repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
  tag: DEV04



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
  tag: SIT01



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
  tag: UAT01



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/journal-service
  tag: PROD01