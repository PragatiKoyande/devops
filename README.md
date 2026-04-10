namespace: backend

serviceAccountName: react-app-sa
deploymentName: react-app-deployment
serviceName: react-service

appLabel: reactive-app
containerName: reactive-container

replicaCount: 1
containerPort: 80
servicePort: 80

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/react-service
  tag: DEV46
  pullPolicy: Always

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

startupProbe:
  failureThreshold: 30
  periodSeconds: 10

livenessProbe:
  initialDelaySeconds: 20
  periodSeconds: 10
  timeoutSeconds: 3
  failureThreshold: 3

readinessProbe:
  initialDelaySeconds: 10
  periodSeconds: 5
  timeoutSeconds: 3
  failureThreshold: 3

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

hpaName: react-app-hpa

pdb:
  enabled: true

pdbName: react-app-pdb