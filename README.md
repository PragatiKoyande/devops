apiVersion: v1
kind: ConfigMap
metadata:
  name: report-redis-config
  namespace: backend

data:
  SPRING_DATA_REDIS_HOST: "redis-service"
  SPRING_DATA_REDIS_PORT: "6379"
  SPRING_DATA_REDIS_CLIENT_TYPE: "lettuce"



kafka

apiVersion: v1
kind: ConfigMap
metadata:
  name: report-kafka-config
  namespace: backend

data:
  SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS: "kafka.backend.svc.cluster.local:9092"
  SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS: "kafka.backend.svc.cluster.local:9092"


spring


apiVersion: v1
kind: ConfigMap
metadata:
  name: report-spring-config
  namespace: backend

data:
  SPRING_DATASOURCE_URL: "jdbc:oracle:thin:@10.190.224.79:1523/fincorepdb1"
  SPRING_DATASOURCE_DRIVER_CLASS_NAME: "oracle.jdbc.OracleDriver"


Hadoop

apiVersion: v1
kind: ConfigMap
metadata:
  name: report-hadoop-config
  namespace: backend

data:
  HADOOP_FS_HA_NN1: "hdfs://10.177.224.102:8022"
  HADOOP_FS_HA_NN2: "hdfs://10.177.224.103:8022"
  HADOOP_FS_HA_NN3: "hdfs://10.177.224.104:8022"
  HADOOP_FS_HA_NN4: "hdfs://10.177.224.105:8022"
  HADOOP_FS_HA_NN5: "hdfs://10.177.224.106:8022"

  HADOOP_FS_USER: "root"
  HADOOP_FS_URI: "hdfs://fincore"
  GLIF_REPORTS_BASE_PATH: "/reports"


secrets

echo -n "fincore" | base64
echo -n "Password#1234" | base64

apiVersion: v1
kind: Secret
metadata:
  name: report-secret
  namespace: backend

type: Opaque

data:
  SPRING_DATASOURCE_USERNAME: ZmluY29yZQ==
  SPRING_DATASOURCE_PASSWORD: UGFzc3dvcmQjMTIzNA==