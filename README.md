You just need to add --kubeconfig h06vksuatcbopscls.conf to the command. Here it is:
kubectl run loki-fix --rm -it --image=busybox --kubeconfig h06vksuatcbopscls.conf --overrides='{"spec":{"volumes":[{"name":"storage","persistentVolumeClaim":{"claimName":"loki-pvc"}}],"containers":[{"name":"loki-fix","image":"busybox","command":["sh"],"stdin":true,"tty":true,"volumeMounts":[{"name":"storage","mountPath":"/var/loki"}]}]}}' -n logging
Once you're inside the shell, run:
rm -rf /var/loki/index/index_20549
exit