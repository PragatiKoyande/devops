# SIT: moderate security, basic limits, network policies enabled.
replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/voucher-service
  pullPolicy: Always
  tag: "SIT01"

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "sit"

envFrom:
  configMaps:
    - name: config-hive

features:
  enableHPA: false
  enablePodDisruptionBudget: false
  enableTopologySpread: false
  enableStrictSecurity: true
  enableReadOnlyRoot: true
  enableResourceLimits: true
  enableNetworkPolicy: true

podDisruptionBudget:
  minAvailable: 1

resources:
  requests:
    cpu: 200m
    memory: 256Mi
  limits:
    cpu: 750m
    memory: 768Mi

updateStrategy:
  rollingUpdate:
    maxUnavailable: 1
    maxSurge: 1