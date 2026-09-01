# UAT: prod-like config, HPA enabled, topology spread, read-only root.
replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/voucher-service
  pullPolicy: Always
  tag: "UAT01"

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "uat"

features:
  enableHPA: true
  enablePodDisruptionBudget: true
  enableTopologySpread: true
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