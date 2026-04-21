name: react-app
namespace: prod-cbops

replicaCount: 1

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/react-service
  tag: PR-13
  pullPolicy: Always

serviceAccount:
  name: react-app-sa

service:
  name: react-service
  port: 80
  targetPort: 80

pdb:
  name: react-app-pdb
  minAvailable: 1

autoscaling:
  name: react-app-hpa
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

resources:
  requests:
    cpu: "100m"
    memory: "128Mi"
  limits:
    cpu: "300m"
    memory: "256Mi"

envFrom:
  configMaps: []
  secrets: []

extraEnv: []
secretEnv: []

hostAliases: []

volumes: []
volumeMounts: []

topologySpreadConstraints:
  enabled: true

probes:
  readiness:
    initialDelaySeconds: 10
    periodSeconds: 5
    timeoutSeconds: 3
    failureThreshold: 3

  liveness:
    initialDelaySeconds: 20
    periodSeconds: 10
    timeoutSeconds: 3
    failureThreshold: 3

  startup:
    failureThreshold: 30
    periodSeconds: 10