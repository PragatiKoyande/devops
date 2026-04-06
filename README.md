D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl run loki-fix --rm -it --image=busybox --kubeconfig h06vksuatcbopscls.conf --overrides='{"spec":{"volumes":[{"name":"storage","persistentVolumeClaim":{"claimName":"loki-pvc"}}],"containers":[{"name":"loki-fix","image":"busybox","command":["sh"],"stdin":true,"tty":true,"volumeMounts":[{"name":"storage","mountPath":"/var/loki"}]}]}}' -n logging
error: Invalid JSON Patch

getting this error
