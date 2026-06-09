[root@fcuatgateway Network]# kc get svc redis-service -n uat-cbops1
NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
redis-service   ClusterIP   10.98.173.199   <none>        6379/TCP   157d
[root@fcuatgateway Network]# kc get endpoints redis-service -n uat-cbops1
NAME            ENDPOINTS          AGE
redis-service   192.168.3.6:6379   157d
[root@fcuatgateway Network]# kgp -n uat-cbops1
NAME                                          READY   STATUS             RESTARTS           AGE
airflow-api-server-bdff76796-tvbb8            1/1     Running            0                  24d
airflow-dag-processor-6fc5d5968-dftcx         2/2     Running            1204 (106s ago)    24d
airflow-redis-0                               1/1     Running            0                  24d
airflow-scheduler-789759f886-f2kl4            1/2     Running            1313 (6m36s ago)   24d
airflow-statsd-848cff7966-nfztl               1/1     Running            0                  24d
airflow-triggerer-0                           2/2     Running            1209 (4m23s ago)   24d
airflow-worker-0                              2/2     Running            1139               24d
airflow-worker-1                              2/2     Running            1136 (42s ago)     24d
airflow-worker-2                              2/2     Running            1145 (42s ago)     24d
akhq-64c59669df-9gnn4                         1/1     Running            0                  24d
common-master-deployment-5c5dfb47fb-cq2k2     1/1     Running            0                  7d1h
common-request-deployment-54549b9c9c-jxpr9    1/1     Running            0                  24d
dashboard-deployment-84c599f54-jtn8h          1/1     Running            0                  7d21h
debezium-server-5cf9f6bb84-4tqzm              0/1     CrashLoopBackOff   830 (3m30s ago)    7d20h
finny-deployment-7755b5dcbb-g7kws             1/1     Running            0                  14d
grafana-5b4f7d6789-ndjwq                      1/1     Running            0                  24d
help-service-deployment-5cf79bccb4-7r5d8      1/1     Running            0                  4d3h
journal-deployment-644dd4cc85-gdxns           1/1     Running            0                  24d
kafka-0                                       1/1     Running            0                  24d
login-deployment-655df65bfd-f4mzb             1/1     Running            0                  20m
notification-deployment-58c7d9fd4f-l6lxz      1/1     Running            0                  24d
postgres-db-5b694b94f6-9wx6r                  1/1     Running            0                  24d
process-status-deployment-67c4ccf5bd-gtphz    1/1     Running            0                  24d
react-app-deployment-6c77b7bb67-kbdqx         1/1     Running            0                  5d23h
redis-deployment-7948b65c64-hgbhr             1/1     Running            0                  24d
redis-vector-deployment-984d5cddd-mckcf       1/1     Running            0                  14d
report-builder-deployment-85d748f48b-95nt7    1/1     Running            0                  24d
report-deployment-59678b7bdc-wsm9g            1/1     Running            0                  24d
spark-operator-controller-84567b7b4-g8m2p     1/1     Running            8 (16d ago)        24d
spark-operator-webhook-c9d8d7676-t2v48        1/1     Running            7 (16d ago)        24d
template-config-deployment-5d69bff69f-9jkv2   1/1     Running            0                  24d
transactions-deployment-778695c7cb-l4kp5      1/1     Running            0                  14d
user-deployment-596fc775dc-b9z7t              1/1     Running            0                  7d
