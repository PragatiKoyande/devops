[root@fcsitgateway ~]# k get endpoints -n logging loki
Warning: v1 Endpoints is deprecated in v1.33+; use discovery.k8s.io/v1 EndpointSlice
NAME   ENDPOINTS           AGE
loki   192.168.4.20:3100   108d
[root@fcsitgateway ~]# k get pods -n logging -o wide
NAME                    READY   STATUS    RESTARTS   AGE   IP             NODE                                              NOMINATED NODE   READINESS GATES
loki-86c678b849-rfczr   1/1     Running   0          19d   192.168.4.20   h06vkssitcbopscls-node-pool-1-2nb6d-qhtlx-ggdcx   <none>           <none>
[root@fcsitgateway ~]# k get networkpolicy -n logging
NAME                  POD-SELECTOR   AGE
loki-network-policy   app=loki       25d
[root@fcsitgateway ~]# k describe svc loki -n logging
Warning: v1 Endpoints is deprecated in v1.33+; use discovery.k8s.io/v1 EndpointSlice
Name:              loki
Namespace:         logging
Labels:            <none>
Annotations:       <none>
Selector:          app=loki
Type:              ClusterIP
IP Family Policy:  SingleStack
IP Families:       IPv4
IP:                10.104.67.221
IPs:               10.104.67.221
Port:              <unset>  3100/TCP
TargetPort:        3100/TCP
Endpoints:         192.168.4.20:3100
Session Affinity:  None
Events:            <none>
