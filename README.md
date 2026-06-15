enabled: true

namespace: backend

labels:
  app: help-service-backend

serviceAccount:
  create: true
  name: help-service-sa

deployment:
  name: help-service-deployment
  replicas: 1

service:
  name: help-service
  type: ClusterIP
  port: 80
  targetPort: 9099

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/helpservice
  tag: DEV-01
  imagePullPolicy: Always

container:
  name: help-service-container

terminationGracePeriodSeconds: 30

strategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 0
    maxSurge: 1

securityContext:
  runAsNonRoot: true
  runAsUser: 1000
  runAsGroup: 1000
  fsGroup: 1000
  seccompProfile:
    type: RuntimeDefault

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: false
  capabilities:
    drop:
      - ALL

topologySpreadConstraints:
  - maxSkew: 1
    topologyKey: kubernetes.io/hostname
    whenUnsatisfiable: ScheduleAnyway
    labelSelector:
      matchLabels:
        app: help-service-backend

envFrom:
  - configMapRef:
      name: oracle-config
  - secretRef:
      name: oracle-secret
  - configMapRef:
      name: redis-config

ports:
  - containerPort: 9099

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "1000m"
    memory: "1024Mi"

lifecycle:
  preStop:
    exec:
      command:
        - /bin/sh
        - -c
        - sleep 15

probes:
  port: 9099

startupProbe:
  tcpSocket:
    port: 9099
  failureThreshold: 30
  periodSeconds: 10

readinessProbe:
  tcpSocket:
    port: 9099
  initialDelaySeconds: 20
  periodSeconds: 10
  timeoutSeconds: 2
  failureThreshold: 3
  successThreshold: 1

livenessProbe:
  tcpSocket:
    port: 9099
  initialDelaySeconds: 60
  periodSeconds: 20
  timeoutSeconds: 2
  failureThreshold: 3

hpa:
  name: help-service-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

pdb:
  name: help-service-pdb
  minAvailable: 1






image:
  repository: h06vksharbor.corp.ad.sbi/cbops/helpservice
  tag: DEV-01


