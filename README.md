[root@fcsitgateway Network]# k get svc -A | grep -i kafka
backend                   kafka                               ClusterIP      None             <none>           9092/TCP,9093/TCP            80d
cbops                     kafka                               ClusterIP      None             <none>           9092/TCP,9093/TCP            152d
[root@fcsitgateway Network]# kgp
NAME                                                  READY   STATUS    RESTARTS          AGE
airflow-api-server-588b95b9fc-f5brp                   1/1     Running   0                 40d
airflow-dag-processor-5c6f9f65fb-nb6rf                2/2     Running   101 (6d15h ago)   40d
airflow-redis-0                                       1/1     Running   0                 40d
airflow-scheduler-658884d69c-hxtfl                    2/2     Running   126 (6d15h ago)   40d
airflow-statsd-848cff7966-ccmr9                       1/1     Running   0                 40d
airflow-triggerer-0                                   2/2     Running   102 (6d15h ago)   39d
airflow-worker-0                                      2/2     Running   15 (6d18h ago)    40d
airflow-worker-1                                      2/2     Running   0                 6d4h
akhq-64c59669df-rtm9f                                 1/1     Running   0                 6d4h
common-master-deployment-7b798566cc-r7jcm             1/1     Running   0                 33d
common-request-deployment-579cb9b47-xccnz             1/1     Running   0                 33d
dashboard-deployment-7d97f6df78-2hj6r                 1/1     Running   0                 33d
debezium-server-77df5c5c9b-pchfz                      1/1     Running   0                 40d
enquiry-service-deployment-66756f499b-58d62           1/1     Running   0                 10d
grafana-758f498965-52ddd                              1/1     Running   0                 40d
kafka-0                                               1/1     Running   0                 6d4h
login-deployment-5bf4f7bfc6-vplhc                     1/1     Running   0                 31d
notification-deployment-6487d9d495-p4kth              1/1     Running   2 (30s ago)       2m32s
postgres-db-7b865dd6fc-v94qc                          1/1     Running   0                 40d
process-status-deployment-75cd4b5fdf-kl2c4            1/1     Running   0                 33d
react-app-deployment-7bf8f85696-4czb2                 1/1     Running   0                 24h
redis-deployment-54599c456d-vcxfb                     1/1     Running   0                 40d
report-builder-deployment-78f9c7bd66-dr4q4            1/1     Running   0                 33d
report-deployment-7f6d89db8c-l7xh5                    1/1     Running   0                 33d
spark-operator-controller-55f6d78556-sfnmg            1/1     Running   4 (19h ago)       6d4h
spark-operator-webhook-7677dd468d-rmxcc               1/1     Running   4 (28h ago)       6d4h
spark-thrift-78bf5cd48-d4tlr                          1/1     Running   0                 40d
template-config-deployment-67757d565b-pddzl           1/1     Running   0                 33d
transactions-deployment-67d78b694d-zk47v              1/1     Running   0                 7d21h
user-deployment-79db8b448d-67dq7                      1/1     Running   0                 44h
voucher-enquiry-service-deployment-5cf5ff5cd7-6mfxz   1/1     Running   0                 6d21h
voucher-service-deployment-5bb89b5f54-r7zlw           1/1     Running   0                 21h
[root@fcsitgateway Network]# k exec -it notification-deployment-6487d9d495-p4kth -n cbops -- env | grep -i kafka
SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS=kafka.cbops.svc.cluster.local:9092
SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS=kafka.cbops.svc.cluster.local:9092
SPRING_KAFKA_CONSUMER_GROUP_ID=notification-service-group
SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET=earliest
