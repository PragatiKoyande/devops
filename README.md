[root@fcprodkubjump prod-configmaps-secrets]# k exec notification-deployment-6fff9d966b-9257m -- env | grep SPRING_KAFKA_BOOTSTRAP
[root@fcprodkubjump prod-configmaps-secrets]# cat kafka-config.yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: kafka-config
  namespace: backend

data:
  SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS: "kafka.backend.svc.cluster.local:9092"
  SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS: "kafka.backend.svc.cluster.local:9092"
