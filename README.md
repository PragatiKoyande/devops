D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl scale deployment loki --replicas=0 -n logging  --kubeconfig h06vksuatcbopscls.conf
deployment.apps/loki scaled

D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl get pods -n logging --kubeconfig h06vksuatcbopscls.conf
NAME                    READY   STATUS        RESTARTS   AGE
loki-7974ccfdd5-dwqvx   1/1     Terminating   0          89s

D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl delete pods --all -n logging --force --grace-period=0 --kubeconfig h06vksuatcbopscls.conf
Warning: Immediate deletion does not wait for confirmation that the running resource has been terminated. The resource may continue to run on the cluster indefinitely.
No resources found

shall i delete the deployment entirely
