enabled: true

namespace: backend

labels:
  app: ascii-generation-backend

serviceAccount:
  create: true
  name: ascii-generation-sa

deployment:
  name: ascii-generation-deployment
  replicas: 1

service:
  name: ascii-generation-service
  type: ClusterIP
  port: 80
  targetPort: 8084

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
  tag: DEV-01
  imagePullPolicy: Always

container:
  name: ascii-generation-container

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
        app: ascii-generation-backend

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

ports:
  - containerPort: 8084

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
  port: 8084

startupProbe:
  tcpSocket:
    port: 8084
  failureThreshold: 30
  periodSeconds: 10

readinessProbe:
  tcpSocket:
    port: 8084
  initialDelaySeconds: 20
  periodSeconds: 10
  timeoutSeconds: 5
  failureThreshold: 3

livenessProbe:
  tcpSocket:
    port: 8084
  initialDelaySeconds: 60
  periodSeconds: 20
  timeoutSeconds: 5
  failureThreshold: 3

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