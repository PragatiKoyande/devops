---
# =========================================================
# KAFKA HEADLESS SERVICE (REQUIRED FOR KRaft)
# =========================================================
apiVersion: v1
kind: Service
metadata:
  name: kafka
  namespace: backend
  labels:
    app: kafka
spec:
  clusterIP: None
  selector:
    app: kafka
  ports:
    - name: broker
      port: 9092
    - name: controller
      port: 9093

---
# =========================================================
# KAFKA STATEFULSET (Confluent cp-kafka, KRaft mode)
# =========================================================
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: kafka
  namespace: backend
spec:
  serviceName: kafka
  replicas: 1
  selector:
    matchLabels:
      app: kafka
  template:
    metadata:
      labels:
        app: kafka
    spec:
      securityContext:
        fsGroup: 1000
      containers:
        - name: kafka
          image: h06vksharbor.corp.ad.sbi/cbops/cp-kafka:v1
          ports:
            - name: broker
              containerPort: 9092
            - name: controller
              containerPort: 9093

          resources:
            requests:
              cpu: "500m"
              memory: "2Gi"
            limits:
              cpu: "2"
              memory: "4Gi"

          env:
            - name: CLUSTER_ID
              value: "jgQjUybBSACbAFjwpKFQiA"

            - name: KAFKA_NODE_ID
              value: "1"

            - name: KAFKA_PROCESS_ROLES
              value: "broker,controller"

            - name: KAFKA_CONTROLLER_LISTENER_NAMES
              value: "CONTROLLER"

            - name: KAFKA_CONTROLLER_QUORUM_VOTERS
              value: "1@kafka-0.kafka.cbops.svc.cluster.local:9093"

            - name: KAFKA_LISTENERS
              value: "INTERNAL://0.0.0.0:9092,CONTROLLER://0.0.0.0:9093"

            - name: KAFKA_ADVERTISED_LISTENERS
              value: "INTERNAL://kafka-0.kafka.cbops.svc.cluster.local:9092"

            - name: KAFKA_LISTENER_SECURITY_PROTOCOL_MAP
              value: "INTERNAL:PLAINTEXT,EXTERNAL:PLAINTEXT,CONTROLLER:PLAINTEXT"

            - name: KAFKA_INTER_BROKER_LISTENER_NAME
              value: "INTERNAL"

            - name: KAFKA_LOG_DIRS
              value: "/var/lib/kafka/data/kafka"

            - name: KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR
              value: "1"

            - name: KAFKA_TRANSACTION_STATE_LOG_REPLICATION_FACTOR
              value: "1"

            - name: KAFKA_TRANSACTION_STATE_LOG_MIN_ISR
              value: "1"

          volumeMounts:
            - name: kafka-data
              mountPath: /var/lib/kafka/data

  volumeClaimTemplates:
    - metadata:
        name: kafka-data
      spec:
        storageClassName: h06-vks-sp-6
        accessModes:
          - ReadWriteOnce
        resources:
          requests:
            storage: 5Gi
            -----------------------------------------------------------
            apiVersion: apps/v1
kind: Deployment
metadata:
  name: connect
  namespace: backend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: connect
  template:
    metadata:
      labels:
        app: connect
    spec:
      containers:
        - name: connect
          image: h06vksharbor.corp.ad.sbi/cbops/kafka-connect:x1
          ports:
            - containerPort: 8083
              name: rest

          env:
            # ========= REQUIRED =========
            - name: CONNECT_BOOTSTRAP_SERVERS
              value: "kafka.be-test.svc.cluster.local:9092"

            - name: CONNECT_GROUP_ID
              value: "connect-cluster"

            - name: CONNECT_CONFIG_STORAGE_TOPIC
              value: "_connect-configs"

            - name: CONNECT_OFFSET_STORAGE_TOPIC
              value: "_connect-offsets"

            - name: CONNECT_STATUS_STORAGE_TOPIC
              value: "_connect-status"

            - name: CONNECT_CONFIG_STORAGE_REPLICATION_FACTOR
              value: "1"

            - name: CONNECT_OFFSET_STORAGE_REPLICATION_FACTOR
              value: "1"

            - name: CONNECT_STATUS_STORAGE_REPLICATION_FACTOR
              value: "1"

            # ========= CONVERTERS =========
            - name: CONNECT_KEY_CONVERTER
              value: "org.apache.kafka.connect.json.JsonConverter"

            - name: CONNECT_VALUE_CONVERTER
              value: "org.apache.kafka.connect.json.JsonConverter"

            - name: CONNECT_INTERNAL_KEY_CONVERTER
              value: "org.apache.kafka.connect.json.JsonConverter"

            - name: CONNECT_INTERNAL_VALUE_CONVERTER
              value: "org.apache.kafka.connect.json.JsonConverter"

            - name: CONNECT_KEY_CONVERTER_SCHEMAS_ENABLE
              value: "true"

            - name: CONNECT_VALUE_CONVERTER_SCHEMAS_ENABLE
              value: "true"

            - name: CONNECT_INTERNAL_KEY_CONVERTER_SCHEMAS_ENABLE
              value: "false"

            - name: CONNECT_INTERNAL_VALUE_CONVERTER_SCHEMAS_ENABLE
              value: "false"

            # ========= REST =========
            - name: CONNECT_REST_PORT
              value: "8083"

            - name: CONNECT_REST_ADVERTISED_HOST_NAME
              value: "connect.be-test.svc.cluster.local"

            - name: CONNECT_REST_ADVERTISED_PORT
              value: "8083"

            # ========= PLUGINS =========
            - name: CONNECT_PLUGIN_PATH
              value: "/usr/share/java,/usr/share/java/debezium-connector-oracle"

            # ========= LOGGING =========
            - name: CONNECT_LOG4J_ROOT_LOGLEVEL
              value: "INFO"

          readinessProbe:
            httpGet:
              path: /connectors
              port: 8083
            initialDelaySeconds: 20
            periodSeconds: 10

---
apiVersion: v1
kind: Service
metadata:
  name: connect
  namespace: backend
spec:
  selector:
    app: connect
  ports:
    - name: rest
      port: 8083
      targetPort: 8083
  type: ClusterIP
-------------------------------------------------------------------------------------------
apiVersion: v1
data:
  oracle-connector.json: |
    {
      "name": "fincore-connector-final",
      "config": {
        "connector.class": "io.debezium.connector.oracle.OracleConnector",
        "tasks.max": "1",

        "database.hostname": "10.177.103.192",
        "database.port": "1523",
        "database.user": "c##debezium",
        "database.password": "Debe#123",
        "database.dbname": "fincorepdb1",
        "database.pdb.name": "fincorepdb1",
        "database.sid": "fincorepdb1",
        "database.servername": "fincorepdb1",

        "topic.prefix": "fincore",
        "table.include.list": "fincore.NOTIFICATIONS, fincore.USER_ROLES, fincore.PROCESS_STATUS, fincore.PERMISSIONS, fincore.ROLE_PERMISSIONS",

        "decimal.handling.mode": "string",
        "database.connection.adapter": "logminer",

        "database.history": "io.debezium.relational.history.KafkaDatabaseHistory",

        "database.history.kafka.bootstrap.servers": "kafka.cbops.svc.cluster.local:9092",
        "schema.history.internal.kafka.bootstrap.servers": "kafka.cbops.svc.cluster.local:9092",
        "schema.history.internal.kafka.topic": "schema-changes.oracle",

        "log.mining.strategy": "online_catalog",
        "log.mining.continuous.mine": "true",
        "log.mining.batch.size.default": "50000",
        "log.mining.batch.size.max": "100000",
        "log.mining.sleep.time.default": "50",
        "log.mining.sleep.time.max": "2000",

        "heartbeat.interval.ms": "2000",
        "heartbeat.topics.prefix": "heartbeat",

        "openlineage.integration.enabled": "true"
      }
    }
kind: ConfigMap
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"v1","data":{"oracle-connector.json":"{\n  \"name\": \"fincore-connector-final\",\n  \"config\": {\n    \"connector.class\": \"io.debezium.connector.oracle.OracleConnector\",\n    \"tasks.max\": \"1\",\n\n    \"database.hostname\": \"10.177.103.192\",\n    \"database.port\": \"1523\",\n    \"database.user\": \"c##debezium\",\n    \"database.password\": \"Debe#123\",\n    \"database.dbname\": \"fincorepdb1\",\n    \"database.pdb.name\": \"fincorepdb1\",\n    \"database.sid\": \"fincorepdb1\",\n    \"database.servername\": \"fincorepdb1\",\n\n    \"topic.prefix\": \"fincore\",\n    \"table.include.list\": \"fincore.NOTIFICATIONS, fincore.USER_ROLES, fincore.PROCESS_STATUS, fincore.PERMISSIONS, fincore.ROLE_PERMISSIONS\",\n\n    \"decimal.handling.mode\": \"string\",\n    \"database.connection.adapter\": \"logminer\",\n\n    \"database.history\": \"io.debezium.relational.history.KafkaDatabaseHistory\",\n\n    \"database.history.kafka.bootstrap.servers\": \"kafka.cbops.svc.cluster.local:9092\",\n    \"schema.history.internal.kafka.bootstrap.servers\": \"kafka.cbops.svc.cluster.local:9092\",\n    \"schema.history.internal.kafka.topic\": \"schema-changes.oracle\",\n\n    \"log.mining.strategy\": \"online_catalog\",\n    \"log.mining.continuous.mine\": \"true\",\n    \"log.mining.batch.size.default\": \"50000\",\n    \"log.mining.batch.size.max\": \"100000\",\n    \"log.mining.sleep.time.default\": \"50\",\n    \"log.mining.sleep.time.max\": \"2000\",\n\n    \"heartbeat.interval.ms\": \"2000\",\n    \"heartbeat.topics.prefix\": \"heartbeat\",\n\n    \"openlineage.integration.enabled\": \"true\"\n  }\n}\n"},"kind":"ConfigMap","metadata":{"annotations":{},"name":"oracle-connector-config","namespace":"cbops"}}
  creationTimestamp: "2025-12-10T10:16:10Z"
  name: oracle-connector-config
  namespace: backend
  resourceVersion: "46613478"
  uid: d4abbc42-98d9-4883-bd30-4553baa9bb87
 ---------------------------------------------------------------------------
 apiVersion: batch/v1
kind: Job
metadata:
  name: register-oracle-connector
  namespace: backend
spec:
  backoffLimit: 3
  template:
    spec:
      restartPolicy: OnFailure
      containers:
        - name: register
          image: h06vksharbor.corp.ad.sbi/cbops/curlimages/curl:v1
          command: ["/bin/sh", "-c"]
          args:
            - |
              echo "Waiting for Kafka Connect..."

              # Wait until Connect REST is up
              until curl -sf http://connect.be-test.svc.cluster.local:8083/connectors ; do
                echo "Connect not ready yet..."
                sleep 5
              done

              echo "Sleeping 30s for worker + plugins to fully init..."
              sleep 30

              echo "Posting connector config from /config/oracle-connector.json ..."
              HTTP_CODE=$(curl -s -o /tmp/out.txt -w "%{http_code}" \
                -X POST \
                -H "Content-Type: application/json" \
                --data "@/config/oracle-connector.json" \
                http://connect.be-test.svc.cluster.local:8083/connectors)

              echo "HTTP_CODE=$HTTP_CODE"
              echo "Response body:"
              cat /tmp/out.txt || true

              # 201 = created, 200 = ok, 409 = already exists
              if [ "$HTTP_CODE" != "201" ] && [ "$HTTP_CODE" != "200" ] && [ "$HTTP_CODE" != "409" ]; then
                echo "Registration failed (HTTP $HTTP_CODE)"
                exit 1
              fi

              echo "Connector registration succeeded (or already existed)."
          volumeMounts:
            - name: connector-config
              mountPath: /config

      volumes:
        - name: connector-config
          configMap:
            name: oracle-connector-config
