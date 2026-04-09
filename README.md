
D:\Pragati\HELM-Latest-0904\Deployment>helm template user ./user-service
Error: user-service/templates/serviceaccount.yaml:4:18
  executing "user-service/templates/serviceaccount.yaml" at <.Values.serviceAccount.name>:
    nil pointer evaluating interface {}.name
