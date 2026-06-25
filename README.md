[root@fcsitgateway Network]# k exec -it notification-deployment-cbd8bbfbd-v675j -- nslookup kafka.cbops.svc.cluster.local
Server:         10.96.0.10
Address:        10.96.0.10:53

Name:   kafka.cbops.svc.cluster.local
Address: 192.168.7.12


[root@fcsitgateway Network]# k get svc -A | grep kafka
backend                   kafka                               ClusterIP      None             <none>           9092/TCP,9093/TCP            80d
cbops                     kafka                               ClusterIP      None             <none>           9092/TCP,9093/TCP            152d
[root@fcsitgateway Network]# kgp
NAME                                                  READY   STATUS    RESTARTS        AGE
airflow-api-server-588b95b9fc-f5brp                   1/1     Running   0               40d
airflow-dag-processor-5c6f9f65fb-nb6rf                2/2     Running   104 (44m ago)   40d
airflow-redis-0                                       1/1     Running   0               40d
airflow-scheduler-658884d69c-hxtfl                    2/2     Running   132 (42m ago)   40d
airflow-statsd-848cff7966-ccmr9                       1/1     Running   0               40d
airflow-triggerer-0                                   2/2     Running   105 (44m ago)   39d
airflow-worker-0                                      2/2     Running   18 (42m ago)    40d
airflow-worker-1                                      2/2     Running   3 (43m ago)     6d6h
akhq-64c59669df-rtm9f                                 1/1     Running   0               6d6h
common-master-deployment-7b798566cc-r7jcm             1/1     Running   0               33d
common-request-deployment-579cb9b47-xccnz             1/1     Running   0               33d
dashboard-deployment-7d97f6df78-2hj6r                 1/1     Running   0               33d
debezium-server-77df5c5c9b-pchfz                      1/1     Running   0               40d
enquiry-service-deployment-66756f499b-58d62           1/1     Running   0               10d
grafana-758f498965-52ddd                              1/1     Running   0               40d
kafka-0                                               1/1     Running   0               6d6h
login-deployment-5bf4f7bfc6-vplhc                     1/1     Running   0               31d
notification-deployment-cbd8bbfbd-v675j               1/1     Running   0               36m
postgres-db-7b865dd6fc-v94qc                          1/1     Running   0               40d
process-status-deployment-75cd4b5fdf-kl2c4            1/1     Running   0               33d
react-app-deployment-7bf8f85696-4czb2                 1/1     Running   0               26h
redis-deployment-54599c456d-vcxfb                     1/1     Running   0               40d
report-builder-deployment-78f9c7bd66-dr4q4            1/1     Running   0               33d
report-deployment-7f6d89db8c-l7xh5                    1/1     Running   0               33d
spark-operator-controller-55f6d78556-sfnmg            1/1     Running   4 (21h ago)     6d6h
spark-operator-webhook-7677dd468d-rmxcc               1/1     Running   4 (30h ago)     6d6h
spark-thrift-78bf5cd48-d4tlr                          1/1     Running   0               40d
template-config-deployment-67757d565b-pddzl           1/1     Running   0               33d
transactions-deployment-67d78b694d-zk47v              1/1     Running   0               7d22h
user-deployment-79db8b448d-67dq7                      1/1     Running   0               46h
voucher-enquiry-service-deployment-5cf5ff5cd7-6mfxz   1/1     Running   0               6d23h
voucher-service-deployment-5bb89b5f54-r7zlw           1/1     Running   0               23h
[root@fcsitgateway Network]# k exec -it notification-deployment-cbd8bbfbd-v675j -- nslookup kafka.cbops.svc.cluster.local
Server:         10.96.0.10
Address:        10.96.0.10:53

Name:   kafka.cbops.svc.cluster.local
Address: 192.168.7.12


[root@fcsitgateway Network]# k exec -it debezium-server-77df5c5c9b-pchfz -- nc -vz 10.177.179.46 1523
error: Internal error occurred: error executing command in container: failed to exec in container: failed to start exec "f54b537df6af6b31f39fb4ad9bd03cebba8f1b1fdafe03c147c5230ce9fe6f6c": OCI runtime exec failed: exec failed: unable to start container process: exec: "nc": executable file not found in $PATH: unknown
[root@fcsitgateway Network]# k get svc -A | grep kafka
backend                   kafka                               ClusterIP      None             <none>           9092/TCP,9093/TCP            80d
cbops                     kafka                               ClusterIP      None             <none>           9092/TCP,9093/TCP            152d
[root@fcsitgateway Network]# k get networkpolicy -A
NAMESPACE   NAME                               POD-SELECTOR                  AGE
cbops       allow-dns                          app=voucher-service-backend   2d
cbops       allow-dns-notification             app=notification-backend      120m
cbops       allow-egress-to-oracle             app=voucher-service-backend   6d20h
cbops       allow-kafka-notification           app=notification-backend      120m
cbops       allow-oracle                       app=voucher-service-backend   6d20h
cbops       allow-oracle-db-egress             app=fincore-app               185d
cbops       allow-postgres-db-egress           app=fincore-app               175d
cbops       allow-postgres-notification        app=notification-backend      44m
cbops       allow-redis                        app=voucher-service-backend   2d
cbops       allow-redis-notification-service   app=notification-backend      39m
[root@fcsitgateway Network]# k get pods -A -o wide | grep -E "kafka|notification|debezium"
backend                        kafka-0                                                           1/1     Running             0                6d6h    192.168.7.13    h06vkssitcbopscls-node-pool-1-2nb6d-7bpww-zgvt8   <none>           <none>
cbops                          debezium-server-77df5c5c9b-pchfz                                  1/1     Running             0                40d     192.168.8.25    h06vkssitcbopscls-node-pool-1-2nb6d-whk6z-z995p   <none>           <none>
cbops                          kafka-0                                                           1/1     Running             0                6d6h    192.168.7.12    h06vkssitcbopscls-node-pool-1-2nb6d-7bpww-zgvt8   <none>           <none>
cbops                          notification-deployment-cbd8bbfbd-v675j                           1/1     Running             0                43m     192.168.7.46    h06vkssitcbopscls-node-pool-1-2nb6d-7bpww-zgvt8   <none>           <none>
