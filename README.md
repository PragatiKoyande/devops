[root@fcsitgateway SIT-Grafana]# kubectl get daemonset fluent-bit -n logging --kubeconfig h06vkssitcbopscls.conf
NAME         DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
fluent-bit   3         3         3       3            3           <none>          5d23h
[root@fcsitgateway SIT-Grafana]# kubectl get pod notification-deployment-769bcd99cd-p9qmh -o wide -n cbops --kubeconfig h06vkssitcbopscls.conf
NAME                                       READY   STATUS    RESTARTS   AGE   IP             NODE                                              NOMINATED NODE   READINESS GATES
notification-deployment-769bcd99cd-p9qmh   1/1     Running   0          43d   192.168.1.72   h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-xk62q   <none>           <none>
