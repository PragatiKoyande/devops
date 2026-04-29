namespace: backend

serviceAccount:
  name: process-status-sa

deployment:
  name: process-status-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: process-status-backend

  serviceAccountName: process-status-sa
  terminationGracePeriodSeconds: 30
  enableServiceLinks: false

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

  volumeMounts:
    - name: tmp-dir
      mountPath: /tmp

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: process-status-backend

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
  tag: SV16
  imagePullPolicy: Always

container:
  name: process-status-container
  port: 3000

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

probes:
  port: 3000

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

envFrom:
  - configMapRef:
      name: redis-config
  - configMapRef:
      name: oracle-config
  - secretRef:
      name: oracle-secret

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: true
  capabilities:
    drop:
      - ALL

service:
  name: process-status-service
  port: 80
  targetPort: 3000
  type: ClusterIP

hpa:
  name: process-status-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

pdb:
  name: process-status-pdb
  minAvailable: 1



image:
  repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
  tag: SV16
  imagePullPolicy: Always





image:
  repository: h06vksharbor.corp.ad.sbi/cbops/process-status-service
  tag: <SIT / UAT / PROD TAG>
  imagePullPolicy: Always