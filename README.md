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
[root@fcsitgateway ~]# k get networkpolicy loki-network-policy -n logging -o yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"networking.k8s.io/v1","kind":"NetworkPolicy","metadata":{"annotations":{},"name":"loki-network-policy","namespace":"logging"},"spec":{"egress":[{"to":[{"namespaceSelector":{}}]}],"ingress":[{"from":[{"namespaceSelector":{}}],"ports":[{"port":3100,"protocol":"TCP"}]}],"podSelector":{"matchLabels":{"app":"loki"}},"policyTypes":["Ingress","Egress"]}}
  creationTimestamp: "2026-06-29T09:16:40Z"
  generation: 1
  name: loki-network-policy
  namespace: logging
  resourceVersion: "84536799"
  uid: 93259b3d-fa00-4290-96ac-4cf25ed75b6b
spec:
  egress:
  - to:
    - namespaceSelector: {}
  ingress:
  - from:
    - namespaceSelector: {}
    ports:
    - port: 3100
      protocol: TCP
  podSelector:
    matchLabels:
      app: loki
  policyTypes:
  - Ingress
  - Egress
[root@fcsitgateway ~]# kgp
NAME                                                 READY   STATUS    RESTARTS   AGE
analytics-deployment-769b667b87-qbk8b                1/1     Running   0          46h
common-master-deployment-7f699cc8f4-wclwx            1/1     Running   0          18d
common-request-deployment-6bb4cf6489-fjbnd           1/1     Running   0          18d
dashboard-deployment-5586fc6986-xr2vt                1/1     Running   0          18d
debezium-server-86c8fbbbcb-4b622                     1/1     Running   0          13d
enquiry-service-deployment-555454c8d5-gdv77          1/1     Running   0          43h
grafana-758f498965-w9p8m                             1/1     Running   0          19d
kafka-0                                              1/1     Running   0          19d
login-deployment-68db87f7f7-sshgh                    1/1     Running   0          4d1h
notification-deployment-984c7b87d-tfnz6              1/1     Running   0          18d
postgres-db-7b865dd6fc-42ltl                         1/1     Running   0          19d
process-status-deployment-7b9c58c589-grds5           1/1     Running   0          18d
react-app-deployment-57b89ddbd9-bnsfj                1/1     Running   0          19h
redis-deployment-c976889fb-4prm6                     1/1     Running   0          2d2h
report-builder-deployment-7d76f8864c-6z2qs           1/1     Running   0          18d
report-deployment-79b8874495-t4gpd                   1/1     Running   0          18d
spark-thrift-5bdb599dc-ftnwf                         1/1     Running   0          18d
template-config-deployment-64d667cf55-lzj2q          1/1     Running   0          18d
transactions-deployment-869c8c55f9-mtltg             1/1     Running   0          18d
user-deployment-8695b59675-nzjfr                     1/1     Running   0          2d1h
voucher-enquiry-service-deployment-f558755b5-frzpm   1/1     Running   0          13d
voucher-service-deployment-85d49755f7-x9c82          1/1     Running   0          13d
[root@fcsitgateway ~]# k exec -it grafana-758f498965-w9p8m -- sh
/usr/share/grafana $ curl -v --connect-timeout 5 http://10.104.67.221:3100/ready
*   Trying 10.104.67.221:3100...
* ipv4 connect timeout after 5000ms, move on!
* Failed to connect to 10.104.67.221 port 3100 after 5002 ms: Timeout was reached
* Closing connection
curl: (28) Failed to connect to 10.104.67.221 port 3100 after 5002 ms: Timeout was reached
