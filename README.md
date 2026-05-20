
D:\Pragati\HELM-2404\Deployment\umbrella-chart>helm template micro-services-at-one-go .
Error: cannot load Chart.yaml: error converting YAML to JSON: yaml: line 12: found character that cannot start any token


i m getting this error:

if i m adding below file:

apiVersion: v2
name: umbrella-chart
description: Umbrella Chart
type: application
version: 0.1.0
appVersion: "1.0"

dependencies:
  - name: dashboard
    version: 0.1.0
    repository: "file://../dashboard"
	condition: dashboard.enabled
