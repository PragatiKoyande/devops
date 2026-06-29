[root@fcprodkubjump ~]# k exec notification-deployment-fcd87f8f9-6flrv -- env | grep SPRING_KAFKA
SPRING_KAFKA_BOOTSTRAP_SERVERS=kafka.backend.svc.cluster.local:9092
SPRING_KAFKA_CONSUMER_GROUP_ID=notification-service-group
SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET=earliest
SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS=kafka.backend.svc.cluster.local:9092
SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS=kafka.backend.svc.cluster.local:9092
[root@fcprodkubjump ~]# k exec notification-deployment-fcd87f8f9-6flrv -- env | grep -i ADMIN
[root@fcprodkubjump ~]# k exec notification-deployment-fcd87f8f9-6flrv -- env | grep -i BOOTSTRAP
SPRING_KAFKA_BOOTSTRAP_SERVERS=kafka.backend.svc.cluster.local:9092
SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS=kafka.backend.svc.cluster.local:9092
SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS=kafka.backend.svc.cluster.local:9092
