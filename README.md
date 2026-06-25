[root@fcsitgateway Network]# k get pod -A | grep debezium
cbops                          debezium-server-77df5c5c9b-pchfz                                  1/1     Running             0                40d
[root@fcsitgateway Network]# k get svc -A | grep kafka
backend                   kafka                               ClusterIP      None             <none>           9092/TCP,9093/TCP            80d
cbops                     kafka                               ClusterIP      None             <none>           9092/TCP,9093/TCP            152d
[root@fcsitgateway Network]# k get netpol -A
NAMESPACE   NAME                               POD-SELECTOR                  AGE
cbops       allow-dns                          app=voucher-service-backend   2d1h
cbops       allow-dns-notification             app=notification-backend      147m
cbops       allow-egress-to-oracle             app=voucher-service-backend   6d20h
cbops       allow-kafka-notification           app=notification-backend      147m
cbops       allow-oracle                       app=voucher-service-backend   6d20h
cbops       allow-oracle-db-egress             app=fincore-app               185d
cbops       allow-postgres-db-egress           app=fincore-app               175d
cbops       allow-postgres-notification        app=notification-backend      71m
cbops       allow-redis                        app=voucher-service-backend   2d1h
cbops       allow-redis-notification-service   app=notification-backend      66m
