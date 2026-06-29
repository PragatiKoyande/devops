[root@fcsitgateway SIT-Grafana]# k get networkpolicy -A
NAMESPACE   NAME                               POD-SELECTOR                  AGE
cbops       allow-debezium-kafka               app=debezium-server           3d19h
cbops       allow-debezium-oracle              app=debezium-server           3d19h
cbops       allow-dns                          app=voucher-service-backend   5d21h
cbops       allow-dns-debezium                 app=debezium-server           3d20h
cbops       allow-dns-notification             app=notification-backend      3d22h
cbops       allow-egress-to-oracle             app=voucher-service-backend   10d
cbops       allow-kafka-notification           app=notification-backend      3d22h
cbops       allow-oracle                       app=voucher-service-backend   10d
cbops       allow-oracle-db-egress             app=fincore-app               189d
cbops       allow-postgres-db-egress           app=fincore-app               179d
cbops       allow-postgres-notification        app=notification-backend      3d21h
cbops       allow-redis                        app=voucher-service-backend   5d21h
cbops       allow-redis-notification-service   app=notification-backend      3d21h
[root@fcsitgateway SIT-Grafana]# k get pods -n kube-system
NAME                                                              READY   STATUS    RESTARTS     AGE
antrea-agent-94w9m                                                2/2     Running   0            44d
antrea-agent-cnzqr                                                2/2     Running   0            10d
antrea-agent-h64mq                                                2/2     Running   0            43d
antrea-agent-jtf58                                                2/2     Running   0            208d
antrea-agent-k7dm2                                                2/2     Running   0            208d
antrea-agent-ltczz                                                2/2     Running   0            11d
antrea-agent-pwh95                                                2/2     Running   0            44d
antrea-agent-smgvt                                                2/2     Running   0            11d
antrea-agent-th5hv                                                2/2     Running   0            11d
antrea-controller-6b7485899d-nrtbj                                1/1     Running   0            11d
coredns-57db7b44f5-cjcwr                                          1/1     Running   0            11d
coredns-57db7b44f5-rgzkm                                          1/1     Running   0            11d
docker-registry-h06vkssitcbopscls-bmjtp-22dct                     1/1     Running   0            11d
docker-registry-h06vkssitcbopscls-bmjtp-dskks                     1/1     Running   0            11d
docker-registry-h06vkssitcbopscls-bmjtp-g48kt                     1/1     Running   0            11d
docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-7bpww-zgvt8   1/1     Running   0            10d
docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-bc5v4   1/1     Running   0            208d
docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-xk62q   1/1     Running   0            208d
docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-whk6z-rqs4z   1/1     Running   0            44d
docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-whk6z-xt7fl   1/1     Running   0            43d
docker-registry-h06vkssitcbopscls-node-pool-1-2nb6d-whk6z-z995p   1/1     Running   0            44d
etcd-h06vkssitcbopscls-bmjtp-22dct                                1/1     Running   0            11d
etcd-h06vkssitcbopscls-bmjtp-dskks                                1/1     Running   0            11d
etcd-h06vkssitcbopscls-bmjtp-g48kt                                1/1     Running   0            11d
kube-apiserver-h06vkssitcbopscls-bmjtp-22dct                      1/1     Running   0            11d
kube-apiserver-h06vkssitcbopscls-bmjtp-dskks                      1/1     Running   0            11d
kube-apiserver-h06vkssitcbopscls-bmjtp-g48kt                      1/1     Running   0            11d
kube-controller-manager-h06vkssitcbopscls-bmjtp-22dct             1/1     Running   0            11d
kube-controller-manager-h06vkssitcbopscls-bmjtp-dskks             1/1     Running   1 (9d ago)   11d
kube-controller-manager-h06vkssitcbopscls-bmjtp-g48kt             1/1     Running   0            11d
kube-proxy-67rz7                                                  1/1     Running   0            10d
kube-proxy-7bkf8                                                  1/1     Running   0            44d
kube-proxy-89lm8                                                  1/1     Running   0            43d
kube-proxy-bxpvq                                                  1/1     Running   0            208d
kube-proxy-d7qbj                                                  1/1     Running   0            44d
kube-proxy-k29sq                                                  1/1     Running   0            11d
kube-proxy-n9gkd                                                  1/1     Running   0            208d
kube-proxy-rkd57                                                  1/1     Running   0            11d
kube-proxy-xwm6d                                                  1/1     Running   0            11d
kube-scheduler-h06vkssitcbopscls-bmjtp-22dct                      1/1     Running   1 (8d ago)   11d
kube-scheduler-h06vkssitcbopscls-bmjtp-dskks                      1/1     Running   1 (9d ago)   11d
kube-scheduler-h06vkssitcbopscls-bmjtp-g48kt                      1/1     Running   0            11d
metrics-server-8494fddddc-v5hzk                                   1/1     Running   0            11d
snapshot-controller-75bb7555d-hfrtt                               1/1     Running   0            11d
[root@fcsitgateway SIT-Grafana]# k exec -it grafana-758f498965-52ddd -n cbops -- nslookup raw.githubusercontent.com
Server:         10.96.0.10
Address:        10.96.0.10:53

Non-authoritative answer:

** server can't find raw.githubusercontent.com: NXDOMAIN

command terminated with exit code 1
[root@fcsitgateway SIT-Grafana]# k exec -it grafana-758f498965-52ddd -n cbops -- cat /etc/resolv.conf
search cbops.svc.cluster.local svc.cluster.local cluster.local
nameserver 10.96.0.10
options ndots:5


my cluster is running on tanzu server
