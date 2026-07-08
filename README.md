
[root@fcppjump PRE-PROD-Microservices]# k get svc -n backend
NAME                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)             AGE
common-master-service     ClusterIP   10.104.29.14     <none>        80/TCP              15d
common-request-service    ClusterIP   10.106.206.254   <none>        80/TCP              15d
dashboard-service         ClusterIP   10.106.131.207   <none>        80/TCP              15d
debezium-server           ClusterIP   10.102.80.35     <none>        8080/TCP            20d
enquiry-service           ClusterIP   10.106.141.17    <none>        80/TCP              14d
kafka                     ClusterIP   None             <none>        9092/TCP,9093/TCP   20d
login-service             ClusterIP   10.99.154.171    <none>        80/TCP              15d
notification-service      ClusterIP   10.98.224.92     <none>        80/TCP              15d
nwsa-variance-service     ClusterIP   10.103.205.116   <none>        80/TCP              15d
process-status-service    ClusterIP   10.104.105.63    <none>        80/TCP              15d
redis-service             ClusterIP   10.105.64.13     <none>        6379/TCP            15d
report-builder-service    ClusterIP   10.101.253.111   <none>        80/TCP              15d
report-service            ClusterIP   10.108.71.71     <none>        80/TCP              15d
template-config-service   ClusterIP   10.103.39.55     <none>        80/TCP              15d
transactions-service      ClusterIP   10.97.77.38      <none>        80/TCP              15d
user-service              ClusterIP   10.102.246.232   <none>        80/TCP              15d
voucher-enquiry-service   ClusterIP   10.111.130.230   <none>        80/TCP              15d
[root@fcppjump PRE-PROD-Microservices]# k get endpoints -n backend
Warning: v1 Endpoints is deprecated in v1.33+; use discovery.k8s.io/v1 EndpointSlice
NAME                      ENDPOINTS                             AGE
common-master-service     192.168.6.15:2000                     15d
common-request-service    192.168.6.14:9000                     15d
dashboard-service         192.168.5.10:9015                     15d
debezium-server                                                 20d
enquiry-service           192.168.6.17:4001                     14d
kafka                     192.168.6.12:9093,192.168.6.12:9092   20d
login-service             192.168.5.16:8085                     15d
notification-service      192.168.6.20:9010                     15d
nwsa-variance-service     192.168.6.18:8093                     15d
process-status-service                                          15d
redis-service             192.168.5.14:6379                     15d
report-builder-service    192.168.5.17:8091                     15d
report-service                                                  15d
template-config-service   192.168.5.18:8090                     15d
transactions-service      192.168.5.11:4000                     15d
user-service              192.168.6.19:8087                     15d
voucher-enquiry-service   192.168.5.13:9025                     15d
[root@fcppjump PRE-PROD-Microservices]# k get pods -n backend -o wide
NAME                                          READY   STATUS             RESTARTS         AGE    IP             NODE                                                  NOMINATED NODE   READINESS GATES
common-master-deployment-545f8bf5f5-8vf4x     1/1     Running            0                75m    192.168.6.15   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-mx8k8   <none>           <none>
common-request-deployment-558c4f669f-gh6lb    1/1     Running            0                75m    192.168.6.14   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-mx8k8   <none>           <none>
dashboard-deployment-54578477d8-gtzkz         1/1     Running            0                75m    192.168.5.10   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4   <none>           <none>
debezium-server-86c8fbbbcb-g2bch              0/1     CrashLoopBackOff   29 (66s ago)     136m   192.168.5.2    h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4   <none>           <none>
enquiry-service-deployment-6cfd44ff49-rmbdt   1/1     Running            0                55m    192.168.6.17   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-mx8k8   <none>           <none>
kafka-0                                       1/1     Running            0                79m    192.168.6.12   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-mx8k8   <none>           <none>
login-deployment-669bdfc567-qtm2d             1/1     Running            0                55m    192.168.5.16   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4   <none>           <none>
notification-deployment-5bd84f5dbc-9894f      1/1     Running            0                55m    192.168.6.20   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-mx8k8   <none>           <none>
nwsa-variance-deployment-6564c885bf-thkl5     1/1     Running            0                55m    192.168.6.18   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-mx8k8   <none>           <none>
process-status-deployment-5979f469c6-6nrbg    0/1     CrashLoopBackOff   18 (42s ago)     75m    192.168.6.16   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-mx8k8   <none>           <none>
redis-deployment-57d4cb76b9-668b5             1/1     Running            0                75m    192.168.5.14   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4   <none>           <none>
report-builder-deployment-76fd9446fc-9tk8t    1/1     Running            0                55m    192.168.5.17   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4   <none>           <none>
report-deployment-6f7b45568d-cmrw7            0/1     Running            18 (5m18s ago)   75m    192.168.5.12   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4   <none>           <none>
template-config-deployment-85c6756d68-wtsdh   1/1     Running            0                55m    192.168.5.18   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4   <none>           <none>
transactions-deployment-cd9c6cd-bnp9h         1/1     Running            0                75m    192.168.5.11   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4   <none>           <none>
user-deployment-6759959958-znb8l              1/1     Running            0                55m    192.168.6.19   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-mx8k8   <none>           <none>
voucher-enquiry-deployment-5d67457c9f-4f7jq   1/1     Running            0                75m    192.168.5.13   h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4   <none>           <none>
