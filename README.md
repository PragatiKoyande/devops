This is a Windows command prompt issue — single quotes don't work in cmd.exe for JSON. You need to escape the JSON differently. Try this:
kubectl run loki-fix --rm -it --image=busybox --kubeconfig h06vksuatcbopscls.conf -n logging --overrides="{\"spec\":{\"volumes\":[{\"name\":\"storage\",\"persistentVolumeClaim\":{\"claimName\":\"loki-pvc\"}}],\"containers\":[{\"name\":\"loki-fix\",\"image\":\"busybox\",\"command\":[\"sh\"],\"stdin\":true,\"tty\":true,\"volumeMounts\":[{\"name\":\"storage\",\"mountPath\":\"/var/loki\"}]}]}}"
All single quotes replaced with escaped double quotes \" which is what Windows CMD requires.
Once you get the shell prompt, run:
rm -rf /var/loki/index/index_20549
exit
If you're using PowerShell instead of CMD, the command would be different — let me know which terminal you're using if this still fails.