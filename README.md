        # -----------------------------
        # Hadoop
        # -----------------------------
          - name: HADOOP_FS_HA_NN1
            value: "hdfs://10.177.224.102:8022"
          - name: HADOOP_FS_HA_NN2
            value: "hdfs://10.177.224.103:8022"
          - name: HADOOP_FS_HA_NN3
            value: "hdfs://10.177.224.104:8022"
          - name: HADOOP_FS_HA_NN4
            value: "hdfs://10.177.224.105:8022"
          - name: HADOOP_FS_HA_NN5
            value: "hdfs://10.177.224.106:8022"
          - name: HADOOP_FS_USER
            value: "root"
          - name: HADOOP_FS_URI
            value: "hdfs://fincore"
          - name: GLIF_REPORTS_BASE_PATH
            value: "/reports"



            I want to amke config map for above configuration please guide me with this and also tell me how to refer in manifest
