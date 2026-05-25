---
# =========================================================
# KAFKA HEADLESS SERVICE (REQUIRED FOR KRaft)
# =========================================================
apiVersion: v1
kind: Service
metadata:
  name: kafka
  namespace: be-test
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
  namespace: be-test
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
              value: "1@kafka-0.kafka.be-test.svc.cluster.local:9093"

            - name: KAFKA_LISTENERS
              value: "INTERNAL://0.0.0.0:9092,EXTERNAL://0.0.0.0:29092,CONTROLLER://0.0.0.0:9093"

            - name: KAFKA_ADVERTISED_LISTENERS
              value: "INTERNAL://kafka-0.kafka.be-test.svc.cluster.local:9092,EXTERNAL://localhost:29092"

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
