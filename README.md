name: process-status
namespace: backend

replicaCount: 1

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/process-status-service
  tag: PR-05
  pullPolicy: Always

serviceAccount:
  name: process-status-sa

service:
  name: process-status-service
  port: 80
  targetPort: 3000

pdb:
  name: process-status-pdb
  minAvailable: 1

autoscaling:
  name: process-status-hpa
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

resources:
  requests:
    cpu: "200m"
    memory: "256Mi"
  limits:
    cpu: "500m"
    memory: "512Mi"

volumes:
  - name: tmp-dir
    emptyDir:
      medium: Memory
      sizeLimit: 64Mi

volumeMounts:
  - name: tmp-dir
    mountPath: /tmp

envFrom:
  configMaps:
    - redis-config
    - oracle-config
    - kafka-config
  secrets:
    - oracle-secret
    - airflow-env-credentials

extraEnv:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"

secretEnv: []

hostAliases: []

topologySpreadConstraints:
  enabled: true

probes:
  readiness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 5

  liveness:
    initialDelaySeconds: 90
    periodSeconds: 15
    timeoutSeconds: 5
    failureThreshold: 5

  startup:
    failureThreshold: 60
    periodSeconds: 10