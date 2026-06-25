2026-06-25 11:03:28 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = key
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = true

2026-06-25 11:03:28 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = value
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = true

2026-06-25 11:03:28 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = header
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = true

2026-06-25 11:03:28 INFO  [io.debezium.server.DebeziumServer] (main) Engine executor started
2026-06-25 11:03:29 INFO  [io.debezium.config.CommonConnectorConfig] (pool-7-thread-1) Loading the custom source info struct maker plugin: io.debezium.connector.oracle.OracleSourceInfoStructMaker
2026-06-25 11:03:29 INFO  [io.quarkus] (main) debezium-server-dist 2.5.4.Final on JVM (powered by Quarkus 3.2.10.Final) started in 2.184s. Listening on: http://0.0.0.0:8080
2026-06-25 11:03:29 INFO  [io.quarkus] (main) Profile prod activated.
2026-06-25 11:03:29 INFO  [io.quarkus] (main) Installed features: [cdi, kubernetes-client, resteasy-jackson, smallrye-context-propagation, smallrye-health, vertx]
2026-06-25 11:03:29 INFO  [org.apache.kafka.clients.Metadata] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-06-25 11:03:29 INFO  [org.apache.kafka.clients.producer.internals.TransactionManager] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] ProducerId set to 8002 with epoch 0
2026-06-25 11:05:39 ERROR [io.debezium.connector.oracle.OracleConnector] (pool-7-thread-1) Failed testing connection for {connector.class=io.debezium.connector.oracle.OracleConnector, schema.history.internal.kafka.key.serializer=org.apache.kafka.common.serialization.StringSerializer, heartbeat.topics.prefix=heartbeat, errors.retry.delay.initial.ms=300, key.converter=org.apache.kafka.connect.json.JsonConverter, database.dbname=fincorepdb1, database.user=c##debezium, offset.storage=org.apache.kafka.connect.storage.FileOffsetBackingStore, header.converter.key=json, schema.history.internal.kafka.bootstrap.servers=kafka.cbops.svc.cluster.local:9092, heartbeat.interval.ms=2000, schema.history.internal.kafka.producer.value.serializer=org.apache.kafka.common.serialization.StringSerializer , errors.max.retries=-1, database.password=********, name=kafka, tasks.max=1, log.mining.strategy=online_catalog, schema.history.internal.kafka.producer.key.serializer=org.apache.kafka.common.serialization.StringSerializer, database.sid=fincorepdb1, topic.prefix=fincore, decimal.handling.mode=string, offset.storage.file.filename=/debezium/data/offsets.dat, schema.history.internal.kafka.topic=schema-changes.oracle, log.mining.continuous.mine=false, log.mining.sleep.time.max=2000, log.mining.sleep.time.default=50, value.converter=org.apache.kafka.connect.json.JsonConverter, offset.storage.kafka.producer.value.serializer=org.apache.kafka.common.serialization.StringSerializer , schema.history.internal.kafka.producer.bootstrap.servers=kafka.cbops.svc.cluster.local:9092, header.converter.value=json, offset.storage.kafka.key.serializer=org.apache.kafka.common.serialization.StringSerializer, log.mining.batch.size.max=100000, database.pdb.name=fincorepdb1, database.connection.adapter=logminer, key.converter.value=json, database.server.name=fincorepdb1, offset.flush.timeout.ms=5000, errors.retry.delay.max.ms=10000, offset.storage.kafka.value.serializer=org.apache.kafka.common.serialization.StringSerializer, value.converter.value=json, database.port=1523, offset.flush.interval.ms=60000, offset.storage.kafka.producer.bootstrap.servers=kafka.cbops.svc.cluster.local:9092, database.hostname=10.177.179.46, log.mining.batch.size.default=50000, table.include.list=fincore.NOTIFICATIONS,fincore.USER_ROLES,fincore.PROCESS_STATUS,fincore.PERMISSIONS,fincore.ROLE_PERMISSIONS, value.converter.key=json, offset.storage.kafka.producer.key.serializer=org.apache.kafka.common.serialization.StringSerializer, key.converter.key=json, schema.history.internal.kafka.value.serializer=org.apache.kafka.common.serialization.StringSerializer} with user '[database.user,null,[],[],true]': org.apache.kafka.connect.errors.RetriableException: Failed to resolve Oracle database version
        at io.debezium.connector.oracle.OracleConnection.resolveOracleDatabaseVersion(OracleConnection.java:188)
        at io.debezium.connector.oracle.OracleConnection.<init>(OracleConnection.java:97)
        at io.debezium.connector.oracle.OracleConnection.<init>(OracleConnection.java:80)
        at io.debezium.connector.oracle.OracleConnector.validateConnection(OracleConnector.java:78)
        at io.debezium.connector.common.RelationalBaseSourceConnector.validate(RelationalBaseSourceConnector.java:42)
        at io.debezium.embedded.EmbeddedEngine.getConnectorConfig(EmbeddedEngine.java:521)
        at io.debezium.embedded.EmbeddedEngine.run(EmbeddedEngine.java:431)
        at io.debezium.embedded.ConvertingEngineBuilder$1.run(ConvertingEngineBuilder.java:248)
        at io.debezium.server.DebeziumServer.lambda$start$1(DebeziumServer.java:170)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)
Caused by: java.sql.SQLRecoverableException: IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=8bX279z/SsS0meqWgBf1BA==)
        at oracle.jdbc.driver.T4CConnection.handleLogonNetException(T4CConnection.java:904)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:710)
        at oracle.jdbc.driver.PhysicalConnection.connect(PhysicalConnection.java:1095)
        at oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:90)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:733)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:649)
        at java.sql/java.sql.DriverManager.getConnection(DriverManager.java:677)
        at java.sql/java.sql.DriverManager.getConnection(DriverManager.java:189)
        at io.debezium.jdbc.JdbcConnection.lambda$patternBasedFactory$0(JdbcConnection.java:191)
        at io.debezium.jdbc.JdbcConnection$ConnectionFactoryDecorator.connect(JdbcConnection.java:129)
        at io.debezium.jdbc.JdbcConnection.connection(JdbcConnection.java:875)
        at io.debezium.jdbc.JdbcConnection.connection(JdbcConnection.java:870)
        at io.debezium.jdbc.JdbcConnection.queryAndMap(JdbcConnection.java:623)
        at io.debezium.jdbc.JdbcConnection.queryAndMap(JdbcConnection.java:497)
        at io.debezium.connector.oracle.OracleConnection.resolveOracleDatabaseVersion(OracleConnection.java:157)
        ... 11 more
Caused by: oracle.net.ns.NetException: The Network Adapter could not establish the connection (CONNECTION_ID=8bX279z/SsS0meqWgBf1BA==)
        at oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:741)
        at oracle.net.resolver.AddrResolution.resolveAndExecute(AddrResolution.java:632)
        at oracle.net.ns.NSProtocol.establishConnection(NSProtocol.java:965)
        at oracle.net.ns.NSProtocol.connect(NSProtocol.java:351)
        at oracle.jdbc.driver.T4CConnection.connect(T4CConnection.java:2652)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:669)
        ... 24 more
Caused by: java.io.IOException: Connection timed out, socket connect lapse 129617 ms. 10.177.179.46 1523  0 (1/1) true
        at oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:507)
        at oracle.net.nt.TcpNTAdapter.doLocalDNSLookupConnect(TcpNTAdapter.java:313)
        at oracle.net.nt.TcpNTAdapter.connect(TcpNTAdapter.java:275)
        at oracle.net.nt.ConnOption.connect(ConnOption.java:234)
        at oracle.net.nt.ConnStrategy.executeConnOption(ConnStrategy.java:1047)
        at oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:697)
        ... 29 more
Caused by: java.net.ConnectException: Connection timed out
        at java.base/sun.nio.ch.Net.connect0(Native Method)
        at java.base/sun.nio.ch.Net.connect(Net.java:483)
        at java.base/sun.nio.ch.Net.connect(Net.java:472)
        at java.base/sun.nio.ch.SocketChannelImpl.connect(SocketChannelImpl.java:692)
        at java.base/java.nio.channels.SocketChannel.open(SocketChannel.java:194)
        at oracle.net.nt.TimeoutSocketChannel.connect(TimeoutSocketChannel.java:208)
        at oracle.net.nt.TimeoutSocketChannel.<init>(TimeoutSocketChannel.java:181)
        at oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:467)
        ... 34 more

2026-06-25 11:05:39 ERROR [io.debezium.server.ConnectorLifecycle] (pool-7-thread-1) Connector completed: success = 'false', message = 'Connector configuration is not valid. Unable to connect: Failed to resolve Oracle database version', error = 'null'
2026-06-25 11:05:39 INFO  [io.debezium.server.DebeziumServer] (main) Received request to stop the engine
2026-06-25 11:05:39 INFO  [io.debezium.embedded.EmbeddedEngine] (main) Stopping the embedded engine
2026-06-25 11:05:39 INFO  [io.debezium.server.kafka.KafkaChangeConsumer] (main) consumer destroyed...
2026-06-25 11:05:39 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Closing the Kafka producer with timeoutMillis = 5000 ms.
2026-06-25 11:05:39 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics scheduler closed
2026-06-25 11:05:39 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-06-25 11:05:39 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics reporters closed
2026-06-25 11:05:39 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) App info kafka.producer for producer-1 unregistered
2026-06-25 11:05:39 INFO  [io.quarkus] (main) debezium-server-dist stopped in 0.041s
