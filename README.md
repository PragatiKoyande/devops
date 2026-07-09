
D:\Pragati\Kubernetes-Deployment-Working\DEV-Deployment\Kafka>k get svc -n be-test
NAME                       TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)             AGE
akhq                       ClusterIP   10.98.24.1       <none>        8080/TCP            119d
ascii-generation-service   ClusterIP   10.96.160.251    <none>        80/TCP              31d
common-master-service      ClusterIP   10.98.77.168     <none>        80/TCP              181d
common-request-service     ClusterIP   10.98.122.44     <none>        80/TCP              181d
connect                    ClusterIP   10.110.105.120   <none>        8083/TCP            178d
dashboard-service          ClusterIP   10.103.171.178   <none>        80/TCP              181d
debezium-server            ClusterIP   10.108.219.27    <none>        8080/TCP            93d
druid-service              ClusterIP   10.109.79.182    <none>        80/TCP              44d
enquiry-service            ClusterIP   10.108.10.187    <none>        80/TCP              65d
kafka                      ClusterIP   None             <none>        9092/TCP,9093/TCP   178d
login-service              ClusterIP   10.104.155.75    <none>        80/TCP              181d
notification-service       ClusterIP   10.107.59.82     <none>        80/TCP              181d
nwsa-variance-service      ClusterIP   10.104.189.53    <none>        80/TCP              100d
postgres-db                ClusterIP   10.104.54.96     <none>        5432/TCP            161d
process-status-service     ClusterIP   10.100.224.145   <none>        80/TCP              181d
react-service              ClusterIP   10.100.206.6     <none>        80/TCP              155d
redis-service              ClusterIP   10.111.179.21    <none>        6379/TCP            181d
report-builder-service     ClusterIP   10.102.195.205   <none>        80/TCP              181d
report-service             ClusterIP   10.104.144.31    <none>        80/TCP              181d
template-config-service    ClusterIP   10.111.254.173   <none>        80/TCP              181d
transactions-service       ClusterIP   10.110.206.166   <none>        80/TCP              181d
user-service               ClusterIP   10.100.228.230   <none>        80/TCP              181d
voucher-enquiry-service    ClusterIP   10.110.120.48    <none>        80/TCP              30d
voucher-service            ClusterIP   10.111.217.119   <none>        80/TCP              4h8m

D:\Pragati\Kubernetes-Deployment-Working\DEV-Deployment\Kafka>kgp -n be-test
NAME                                           READY   STATUS             RESTARTS        AGE
akhq-5b45d78f84-ll8st                          1/1     Running            0               5h3m
ascii-generation-deployment-7fffffd99c-nsdvz   1/1     Running            0               5h3m
common-master-deployment-7f54b468d9-qrdrn      1/1     Running            0               4h36m
common-request-deployment-785df7859b-kpkpq     1/1     Running            0               4h55m
dashboard-deployment-58cf5f5f8b-mm5cq          1/1     Running            0               5h3m
debezium-server-5697cf7d76-2mpmv               1/1     Running            0               17m
druid-service-deployment-65758645dd-pmg5q      1/1     Running            0               5h3m
enquiry-service-deployment-677bc6b94-nzrg9     1/1     Running            0               3h56m
kafka-0                                        0/1     CrashLoopBackOff   3 (20s ago)     4h55m
login-deployment-69f966b645-pdtgn              1/1     Running            0               4h55m
notification-deployment-5dfbdb7d5-5d5n8        1/1     Running            0               38m
nwsa-variance-deployment-855977dbfb-tkg8l      1/1     Running            2 (4h53m ago)   4h55m
postgres-db-7b865dd6fc-zzb5p                   1/1     Running            0               4h55m
process-status-deployment-597cbc59c8-q6pfh     1/1     Running            0               4h55m
redis-deployment-6dfd54846d-9bb6c              1/1     Running            0               5h3m
report-builder-deployment-7bf687ccf9-srflq     1/1     Running            0               5h3m
report-deployment-7b467d488-kt9sc              1/1     Running            1 (4h54m ago)   4h55m
template-config-deployment-5dcb6457b7-78zrb    1/1     Running            0               4h55m
transactions-deployment-54fd65fc76-n547s       1/1     Running            0               4h36m
user-deployment-d9fcc5c7d-xgmv2                1/1     Running            1 (4h53m ago)   4h55m
voucher-enquiry-deployment-6d994c5b94-772c9    1/1     Running            0               4h55m
voucher-service-deployment-64f6749d58-ght9z    1/1     Running            0               3h45m

D:\Pragati\Kubernetes-Deployment-Working\DEV-Deployment\Kafka>k get endpoints kafka -n be-test
Warning: v1 Endpoints is deprecated in v1.33+; use discovery.k8s.io/v1 EndpointSlice
NAME    ENDPOINTS   AGE
kafka               178d

D:\Pragati\Kubernetes-Deployment-Working\DEV-Deployment\Kafka>k get networkpolicy -A
NAMESPACE   NAME                          POD-SELECTOR               AGE
be-test     allow-be-test-to-druid        <none>                     44d
be-test     allow-debezium-kafka          app=debezium-server        29m
be-test     allow-debezium-oracle         app=debezium-server        29m
be-test     allow-egress-to-redis         <none>                     20d
be-test     allow-jfrog-cluster-egress    <none>                     30d
be-test     allow-kafka-notification      app=notification-backend   40m
be-test     allow-oracle-db-egress        <none>                     30d
be-test     allow-postgres-notification   app=notification-backend   44m
cbops       allow-egress-druid            app=fincore-app            233d
cbops       allow-hdfs-db-egress          app=fincore-app            189d
cbops       allow-postgress-db-egress     app=fincore-app            198d
logging     loki-network-policy           app=loki                   139d



I dont have networkpolicy written can you please write one for me send back
