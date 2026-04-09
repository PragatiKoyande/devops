
D:\Pragati\HELM-Latest-0904\Deployment>helm template user ./user-service --debug
level=DEBUG msg="Original chart version" version=""
level=DEBUG msg="Chart path" path=D:\Pragati\HELM-Latest-0904\Deployment\user-service
level=DEBUG msg="number of dependencies in the chart" dependencies=0

Error: user-service/templates/serviceaccount.yaml:4:18
  executing "user-service/templates/serviceaccount.yaml" at <.Values.serviceAccount.name>:
    nil pointer evaluating interface {}.name
