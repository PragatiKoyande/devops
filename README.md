D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl run loki-fix --rm -it --image=busybox --overrides='{"spec":{"volumes":[{"name":"storage","persistentVolumeClaim":{"claimName":"loki-pvc"}}],"containers":[{"name":"loki-fix","image":"busybox","command":["sh"],"stdin":true,"tty":true,"volumeMounts":[{"name":"storage","mountPath":"/var/loki"}]}]}}'
E0406 12:16:33.078996   12924 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"http://localhost:8080/api?timeout=32s\": dial tcp [::1]:8080: connectex: No connection could be made because the target machine actively refused it."
Unable to connect to the server: dial tcp [::1]:8080: connectex: No connection could be made because the target machine actively refused it.


I m using one kubeconfig file may be because of that i m getting this issue could you please add the command for that file --kubeconfig  h06vksuatcbopscls.conf
