
D:\Pragati\HELM-Latest-0904\Deployment\nwsa-variance>helm install nwsa . -f values.yaml -n backend --kubeconfig h06vksuatcbopscls.conf
Error: INSTALLATION FAILED: failed to create typed patch object (backend/nwsa-variance-hpa; autoscaling/v2, Kind=HorizontalPodAutoscaler): errors:
  .spec.behavior.scaleDown: expected map, got &{300}
  .spec.behavior.scaleUp: expected map, got &{60}


  
