enabled: true

namespace: backend

labels:
  app: voucher-enquiry-backend

serviceAccount:
  create: true
  name: voucher-enquiry-sa

deployment:
  name: voucher-enquiry-deployment
  replicas: 1

service:
  name: voucher-enquiry-service
  type: ClusterIP
  port: 80
  targetPort: 9025

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/voucher-enquiry-service
  tag: DEV-01
  imagePullPolicy: Always

container:
  name: voucher-enquiry-container

terminationGracePeriodSeconds: 60

securityContext:
  runAsNonRoot: true
  runAsUser: 1000
  runAsGroup: 1000
  fsGroup: 2000

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: false
  capabilities:
    drop:
      - ALL

strategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 0
    maxSurge: 1

topologySpreadConstraints:
  - maxSkew: 1
    topologyKey: kubernetes.io/hostname
    whenUnsatisfiable: ScheduleAnyway
    labelSelector:
      matchLabels:
        app: voucher-enquiry-backend

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

envFrom:
  - configMapRef:
      name: redis-config
  - configMapRef:
      name: oracle-config
  - secretRef:
      name: oracle-secret

ports:
  - containerPort: 9025

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "1000m"
    memory: "1Gi"

lifecycle:
  preStop:
    exec:
      command:
        - /bin/sh
        - -c
        - sleep 20

probes:
  port: 9025

startupProbe:
  tcpSocket:
    port: 9025
  periodSeconds: 10
  failureThreshold: 30

readinessProbe:
  tcpSocket:
    port: 9025
  initialDelaySeconds: 20
  periodSeconds: 10
  timeoutSeconds: 5
  failureThreshold: 3

livenessProbe:
  tcpSocket:
    port: 9025
  initialDelaySeconds: 60
  periodSeconds: 20
  timeoutSeconds: 5
  failureThreshold: 3

hpa:
  name: voucher-enquiry-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

pdb:
  name: voucher-enquiry-pdb
  minAvailable: 1





image:
  repository: h06vksharbor.corp.ad.sbi/cbops/voucher-enquiry-service
  tag: DEV-01

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"





image:
  repository: h06vksharbor.corp.ad.sbi/cbops/voucher-enquiry-service
  tag: SIT-01

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/voucher-enquiry-service
  tag: UAT-01

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"




image:
  repository: h06vksharbor.corp.ad.sbi/cbops/voucher-enquiry-service
  tag: PROD-01

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"