namespace: backend

labels:
  app: reactive-app

serviceAccount:
  name: react-app-sa

deployment:
  name: react-app-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  terminationGracePeriodSeconds: 30
  enableServiceLinks: false

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: reactive-app

container:
  name: reactive-container

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/react-service
  tag: PR-16

service:
  name: react-service
  type: ClusterIP
  port: 80
  targetPort: 80

hpa:
  name: react-app-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70
  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

pdb:
  name: react-app-pdb
  minAvailable: 1

resources:
  requests:
    cpu: "100m"
    memory: "128Mi"
  limits:
    cpu: "300m"
    memory: "256Mi"

probes:
  port: 80

  startup:
    failureThreshold: 30
    periodSeconds: 10

  liveness:
    initialDelaySeconds: 20
    periodSeconds: 10
    timeoutSeconds: 3
    failureThreshold: 3

  readiness:
    initialDelaySeconds: 10
    periodSeconds: 5
    timeoutSeconds: 3
    failureThreshold: 3

lifecycle:
  preStop:
    command: ["/bin/sh", "-c", "sleep 10"]



---


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/react-service
  tag: DEV


----

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/react-service
  tag: SIT


----


image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/react-service
  tag: UAT


-----

image:
  repository: a2p05vksharbor.corp.ad.sbi/cbops/react-service
  tag: PR-16