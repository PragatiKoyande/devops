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


getting this error:

D:\pragati\HELM_LATEST_26082026\voucher-service>helm template . -f ./environments/values-sit.yaml -f ./values.yaml
Error: failed to parse ./environments/values-sit.yaml: cannot unmarshal yaml document: error converting YAML to JSON: yaml: line 36: found a tab character that violates indentation


Please correct the file and send me back entire file properly please dont alter any vales
