apiVersion: v1
kind: ConfigMap
metadata:
  name: hadoop-config
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


containers:
  - name: your-container

    image: your-image

    envFrom:
      - configMapRef:
          name: hadoop-config
      - configMapRef:
          name: redis-config
      - configMapRef:
          name: kafka-config