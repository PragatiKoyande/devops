The compactor is still timing out which means the corrupt index files are still on the PVC — they were never deleted. The config change alone won't fix it until we clean the data.
Let's directly exec into the crashing pod before it dies — but since it crashes too fast, we need to override the command so it doesn't start Loki, just gives us a shell.
Step 1 — Scale down Loki:
kubectl scale deployment loki --replicas=0 -n logging --kubeconfig h06vksuatcbopscls.conf
Step 2 — Run a debug pod using your internal registry image with sleep so it stays alive:
kubectl run loki-fix --rm -it --image=h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4 --kubeconfig h06vksuatcbopscls.conf -n logging --overrides="{\"spec\":{\"volumes\":[{\"name\":\"storage\",\"persistentVolumeClaim\":{\"claimName\":\"loki-pvc\"}}],\"containers\":[{\"name\":\"loki-fix\",\"image\":\"h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4\",\"command\":[\"sleep\",\"3600\"],\"volumeMounts\":[{\"name\":\"storage\",\"mountPath\":\"/var/loki\"}]}]}}"
Note: using sleep 3600 instead of sh — this keeps the pod alive without starting Loki.
Step 3 — Open a second terminal and exec into it:
kubectl exec -it loki-fix -n logging --kubeconfig h06vksuatcbopscls.conf -- sh
Step 4 — Inside the shell, wipe the corrupt index and compactor directories:
ls /var/loki/index/
rm -rf /var/loki/index/
rm -rf /var/loki/compactor/
mkdir -p /var/loki/index
mkdir -p /var/loki/compactor
exit
Step 5 — Scale Loki back up:
kubectl scale deployment loki --replicas=1 -n logging --kubeconfig h06vksuatcbopscls.conf
Step 6 — Check logs:
kubectl logs -f $(kubectl get pod -n logging -l app=loki -o jsonpath='{.items[0].metadata.name}' --kubeconfig h06vksuatcbopscls.conf) -n logging --kubeconfig h06vksuatcbopscls.conf
The index will be rebuilt automatically from the chunks — you won't lose your log data, only the index which Loki regenerates on startup.