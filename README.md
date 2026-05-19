---
# Source: umbrella-chart/charts/common-master/templates/hpa.yaml

apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: common-master-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: common-master-deployment

  minReplicas: 1
  maxReplicas: 5

  behavior:
    scaleDown:
      stabilizationWindowSeconds: 300
    scaleUp:
      stabilizationWindowSeconds: 60

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
---
# Source: umbrella-chart/charts/template-config/templates/serviceaccount.yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: template-config-sa
  namespace: backend
---
# Source: umbrella-chart/charts/process-status/templates/pdb.yaml
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: process-status-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: process-status-backend
---
# Source: umbrella-chart/charts/login/templates/serviceaccount.yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: login-sa
  namespace: backend
automountServiceAccountToken: false
Error: YAML parse error on umbrella-chart/charts/user-service/templates/deployment.yaml: error converting YAML to JSON: yaml: line 81: mapping values are not allowed in this context
