
D:\Pragati\HELM-Latest-0904\Deployment\common-master>helm install common-master . -f values-dev.yaml -n backend --kubeconfig h06vksuatcbopscls.conf
Error: INSTALLATION FAILED: common-master/templates/hpa.yaml:13:25
  executing "common-master/templates/hpa.yaml" at <.Values.autoscaling.minReplicas>:
    nil pointer evaluating interface {}.minReplicas
