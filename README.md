namespace: backend

serviceAccount:
  name: dashboard-sa
  automountServiceAccountToken: false

deployment:
  name: dashboard-deployment
  replicas: 1

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: dashboard-backend

  securityContext:
    runAsNonRoot: true
    runAsUser: 10001
    fsGroup: 10001

  terminationGracePeriodSeconds: 30

  topologySpreadConstraints:
    maxSkew: 1
    topologyKey: kubernetes.io/hostname

container:
  name: dashboard-container

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
  tag: DEV01
  pullPolicy: Always

envFrom:
  - configMapRef:
      name: redis-config
  - configMapRef:
      name: oracle-config
  - secretRef:
      name: oracle-secret

ports:
  containerPort: 9015

probes:
  port: 9015
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
  name: dashboard-service
  port: 80
  targetPort: 9015

hpa:
  name: dashboard-hpa
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  name: dashboard-pdb
  minAvailable: 1




image:
  repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
  tag: DEV01


image:
  repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
  tag: SIT01



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
  tag: UAT01


image:
  repository: h06vksharbor.corp.ad.sbi/cbops/dashboard-service
  tag: PROD01