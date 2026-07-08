[root@fcppjump PRE-PROD-Microservices]# k get networkpolicy allow-egress-to-oracle -n backend -o yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"networking.k8s.io/v1","kind":"NetworkPolicy","metadata":{"annotations":{},"name":"allow-egress-to-oracle","namespace":"backend"},"spec":{"egress":[{"ports":[{"port":1523,"protocol":"TCP"}],"to":[{"ipBlock":{"cidr":"10.177.179.145/32"}}]}],"podSelector":{"matchLabels":{"app":"debezium-server"}},"policyTypes":["Egress"]}}
  creationTimestamp: "2026-06-17T09:07:09Z"
  generation: 1
  name: allow-egress-to-oracle
  namespace: backend
  resourceVersion: "59135489"
  uid: 5a7beae3-496b-40d2-813a-d403dc70214e
spec:
  egress:
  - ports:
    - port: 1523
      protocol: TCP
    to:
    - ipBlock:
        cidr: 10.177.179.145/32
  podSelector:
    matchLabels:
      app: debezium-server
  policyTypes:
  - Egress
[root@fcppjump PRE-PROD-Microservices]# k get cm -n backend
NAME                     DATA   AGE
debezium-server-config   1      20d
hadoop-config            5      15d
kafka-config             2      15d
kube-root-ca.crt         1      21d
ldap-config              3      15d
oracle-config            3      15d
postgres-config          5      15d
redis-config             3      15d
[root@fcppjump PRE-PROD-Microservices]# k get cm debezium-server-config -n backende -o yaml
Error from server (NotFound): namespaces "backende" not found
[root@fcppjump PRE-PROD-Microservices]# k get cm debezium-server-config -n backend -o yaml
apiVersion: v1
data:
  application.properties: "debezium.source.connector.class=io.debezium.connector.oracle.OracleConnector\ndebezium.source.tasks.max=1\n\ndebezium.source.database.hostname=10.177.179.145\ndebezium.source.database.port=1523\ndebezium.source.database.user=c##debezium\ndebezium.source.database.password=Debe#123\ndebezium.source.database.dbname=fincorepdb1\ndebezium.source.database.pdb.name=fincorepdb1\ndebezium.source.database.sid=fincorepdb1\ndebezium.source.database.server.name=fincorepdb1\n\ndebezium.source.topic.prefix=fincore\ndebezium.source.table.include.list=fincore.NOTIFICATIONS,fincore.USER_ROLES,fincore.PROCESS_STATUS,fincore.PERMISSIONS,fincore.ROLE_PERMISSIONS\n\ndebezium.source.decimal.handling.mode=string\ndebezium.source.database.connection.adapter=logminer\n\ndebezium.source.schema.history.internal.kafka.bootstrap.servers=kafka.backend.svc.cluster.local:9092\ndebezium.source.schema.history.internal.kafka.topic=schema-changes.oracle\n\ndebezium.source.log.mining.strategy=online_catalog\ndebezium.source.log.mining.continuous.mine=false\ndebezium.source.log.mining.batch.size.default=50000\ndebezium.source.log.mining.batch.size.max=100000\ndebezium.source.log.mining.sleep.time.default=50\ndebezium.source.log.mining.sleep.time.max=2000\n\ndebezium.source.heartbeat.interval.ms=2000\ndebezium.source.heartbeat.topics.prefix=heartbeat\n\ndebezium.sink.type=kafka\ndebezium.sink.kafka.producer.bootstrap.servers=kafka.backend.svc.cluster.local:9092\ndebezium.sink.kafka.key.serializer=org.apache.kafka.common.serialization.StringSerializer\ndebezium.sink.kafka.value.serializer=org.apache.kafka.common.serialization.StringSerializer\ndebezium.sink.kafka.producer.key.serializer=org.apache.kafka.common.serialization.StringSerializer\ndebezium.sink.kafka.producer.value.serializer=org.apache.kafka.common.serialization.StringSerializer
    \n\ndebezium.format.key=json\ndebezium.format.value=json\n\ndebezium.source.offset.storage.file.filename=/debezium/data/offsets.dat\ndebezium.source.offset.flush.interval.ms=60000\n\nquarkus.log.level=INFO\nquarkus.log.console.json=false\nquarkus.log.console.format=%d{yyyy-MM-dd
    HH:mm:ss} %-5p [%c] (%t) %s%e%n\n"
kind: ConfigMap
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"v1","data":{"application.properties":"debezium.source.connector.class=io.debezium.connector.oracle.OracleConnector\ndebezium.source.tasks.max=1\n\ndebezium.source.database.hostname=10.177.179.145\ndebezium.source.database.port=1523\ndebezium.source.database.user=c##debezium\ndebezium.source.database.password=Debe#123\ndebezium.source.database.dbname=fincorepdb1\ndebezium.source.database.pdb.name=fincorepdb1\ndebezium.source.database.sid=fincorepdb1\ndebezium.source.database.server.name=fincorepdb1\n\ndebezium.source.topic.prefix=fincore\ndebezium.source.table.include.list=fincore.NOTIFICATIONS,fincore.USER_ROLES,fincore.PROCESS_STATUS,fincore.PERMISSIONS,fincore.ROLE_PERMISSIONS\n\ndebezium.source.decimal.handling.mode=string\ndebezium.source.database.connection.adapter=logminer\n\ndebezium.source.schema.history.internal.kafka.bootstrap.servers=kafka.backend.svc.cluster.local:9092\ndebezium.source.schema.history.internal.kafka.topic=schema-changes.oracle\n\ndebezium.source.log.mining.strategy=online_catalog\ndebezium.source.log.mining.continuous.mine=false\ndebezium.source.log.mining.batch.size.default=50000\ndebezium.source.log.mining.batch.size.max=100000\ndebezium.source.log.mining.sleep.time.default=50\ndebezium.source.log.mining.sleep.time.max=2000\n\ndebezium.source.heartbeat.interval.ms=2000\ndebezium.source.heartbeat.topics.prefix=heartbeat\n\ndebezium.sink.type=kafka\ndebezium.sink.kafka.producer.bootstrap.servers=kafka.backend.svc.cluster.local:9092\ndebezium.sink.kafka.key.serializer=org.apache.kafka.common.serialization.StringSerializer\ndebezium.sink.kafka.value.serializer=org.apache.kafka.common.serialization.StringSerializer\ndebezium.sink.kafka.producer.key.serializer=org.apache.kafka.common.serialization.StringSerializer\ndebezium.sink.kafka.producer.value.serializer=org.apache.kafka.common.serialization.StringSerializer \n\ndebezium.format.key=json\ndebezium.format.value=json\n\ndebezium.source.offset.storage.file.filename=/debezium/data/offsets.dat\ndebezium.source.offset.flush.interval.ms=60000\n\nquarkus.log.level=INFO\nquarkus.log.console.json=false\nquarkus.log.console.format=%d{yyyy-MM-dd HH:mm:ss} %-5p [%c] (%t) %s%e%n\n"},"kind":"ConfigMap","metadata":{"annotations":{},"name":"debezium-server-config","namespace":"backend"}}
  creationTimestamp: "2026-06-17T06:49:59Z"
  name: debezium-server-config
  namespace: backend
  resourceVersion: "59098747"
  uid: 1f969723-b172-48a1-b404-f59c80d1d132
