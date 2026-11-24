D:\pragati\HELM_LATEST_26082026>k get cm
NAME                     DATA   AGE
config-airflow           1      115d
config-druid             1      115d
config-hdfs              6      113d
config-kafka             3      109d
config-ldap              5      115d
config-oracle            4      109d
config-postgres          4      67d
config-redis             2      110d
config-sftp              3      98d
debezium-server-config   1      130d
kube-root-ca.crt         1      181d

D:\pragati\HELM_LATEST_26082026>k describe cm debezium-server-config
Name:         debezium-server-config
Namespace:    backend
Labels:       <none>
Annotations:  <none>

Data
====
application.properties:
----
debezium.source.connector.class=io.debezium.connector.oracle.OracleConnector
debezium.source.tasks.max=1

debezium.source.database.hostname=10.177.103.192
debezium.source.database.port=1523
debezium.source.database.user=c##debezium
debezium.source.database.password=Debe#123
debezium.source.database.dbname=fincorepdb1
debezium.source.database.pdb.name=fincorepdb1
debezium.source.database.server.name=fincorepdb1

debezium.source.topic.prefix=fincore
debezium.source.table.include.list=fincore.NOTIFICATIONS,fincore.USER_ROLES,fincore.PROCESS_STATUS,fincore.PERMISSIONS,fincore.ROLE_PERMISSIONS

debezium.source.decimal.handling.mode=string
debezium.source.database.connection.adapter=logminer

debezium.source.schema.history.internal.kafka.bootstrap.servers=kafka.backend.svc.cluster.local:9092
debezium.source.schema.history.internal.kafka.topic=schema-changes.oracle

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

debezium.format.key=json
debezium.format.value=json

debezium.source.offset.storage.file.filename=/debezium/data/offsets.dat
debezium.source.offset.flush.interval.ms=60000

quarkus.log.level=INFO
quarkus.log.console.json=false
quarkus.log.console.format=%d{yyyy-MM-dd HH:mm:ss} %-5p [%c] (%t) %s%e%n



BinaryData
====

Events:  <none>
