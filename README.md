apiVersion: v1
kind: ConfigMap
metadata:
  name: debezium-server-config
  namespace: backend
data:
  application.properties: |
    debezium.source.connector.class=io.debezium.connector.oracle.OracleConnector
    debezium.source.tasks.max=1

    debezium.source.database.hostname=10.177.103.192
    debezium.source.database.port=1523
    debezium.source.database.user=c##debezium
    debezium.source.database.password=Debe#123
    debezium.source.database.dbname=fincorepdb1
    debezium.source.database.pdb.name=fincorepdb1
    debezium.source.database.sid=fincorepdb1
    debezium.source.database.server.name=fincorepdb1

    debezium.source.topic.prefix=fincore
    debezium.source.table.include.list=fincore.NOTIFICATIONS,fincore.USER_ROLES,fincore.PROCESS_STATUS,fincore.PERMISSIONS,fincore.ROLE_PERMISSIONS

    debezium.source.decimal.handling.mode=string
    debezium.source.database.connection.adapter=logminer
    debezium.source.schema.history.internal.kafka.topic=schema-changes.oracle.fresh

    debezium.source.schema.history.internal.kafka.bootstrap.servers=kafka.backend.svc.cluster.local:9092
    debezium.source.schema.history.internal.kafka.topic=schema-changes.oracle
    debezium.source.schema.history.internal.skip.unparseable.ddl=true
    debezium.source.offset.storage.file.filename=/debezium/data/offsets_fresh.dat

    debezium.source.log.mining.strategy=online_catalog
    debezium.source.log.mining.continuous.mine=false
    debezium.source.log.mining.batch.size.default=50000
    debezium.source.log.mining.batch.size.max=100000
    debezium.source.log.mining.sleep.time.default=50
    debezium.source.log.mining.sleep.time.max=2000

    debezium.source.heartbeat.interval.ms=2000
    debezium.source.heartbeat.topics.prefix=heartbeat

    debezium.sink.type=kafka
    debezium.sink.kafka.producer.bootstrap.servers=kafka.backend.svc.cluster.local:9092
    debezium.sink.kafka.key.serializer=org.apache.kafka.common.serialization.StringSerializer
    debezium.sink.kafka.value.serializer=org.apache.kafka.common.serialization.StringSerializer
    debezium.sink.kafka.producer.key.serializer=org.apache.kafka.common.serialization.StringSerializer
    debezium.sink.kafka.producer.value.serializer=org.apache.kafka.common.serialization.StringSerializer
    debezium.source.snapshot.mode=initial

    debezium.format.key=json
    debezium.format.value=json

    debezium.source.offset.storage.file.filename=/debezium/data/offsets.dat
    debezium.source.offset.flush.interval.ms=60000

    quarkus.log.level=INFO
    quarkus.log.console.json=false
    quarkus.log.console.format=%d{yyyy-MM-dd HH:mm:ss} %-5p [%c] (%t) %s%e%n

---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: debezium-pvc
  namespace: backend
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: h06-vks-sp-6
  resources:
    requests:
      storage: 5Gi

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: debezium-server
  namespace: backend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: debezium-server
  template:
    metadata:
      labels:
        app: debezium-server
    spec:
      securityContext:
        fsGroup: 1000
      containers:
        - name: debezium-server
          image: h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1
          imagePullPolicy: IfNotPresent

          securityContext:
            runAsUser: 1000
            runAsGroup: 1000

          env:
            - name: JAVA_OPTS
              value: "-Xms512m -Xmx2g"

          ports:
            - containerPort: 8080

          volumeMounts:
            - name: config-volume
              mountPath: /debezium/conf
            - name: data-volume
              mountPath: /debezium/data

          resources:
            requests:
              cpu: "500m"
              memory: "1Gi"
            limits:
              cpu: "2"
              memory: "3Gi"

      volumes:
        - name: config-volume
          configMap:
            name: debezium-server-config

        - name: data-volume
          persistentVolumeClaim:
            claimName: debezium-pvc

---
apiVersion: v1
kind: Service
metadata:
  name: debezium-server
  namespace: backend
spec:
  selector:
    app: debezium-server
  ports:
    - name: http
      port: 8080
      targetPort: 8080
  type: ClusterIP