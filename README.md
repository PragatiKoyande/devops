
D:\Pragati\HELM-2404\Deployment\umbrella-chart>helm template micro-services-at-one-go .
Error: umbrella-chart/charts/template-config/templates/deployment.yaml:89:42
  executing "umbrella-chart/charts/template-config/templates/deployment.yaml" at <.Values.lifecycle.preStop.command>:
    can't evaluate field command in type interface {}
