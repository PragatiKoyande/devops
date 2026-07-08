
       __       __                 _
  ____/ /___   / /_   ___  ____   (_)__  __ ____ ___
 / __  // _ \ / __ \ / _ \/_  /  / // / / // __ `__ \
/ /_/ //  __// /_/ //  __/ / /_ / // /_/ // / / / / /
\__,_/ \___//_.___/ \___/ /___//_/ \__,_//_/ /_/ /_/



                      Powered by Quarkus 3.2.10.Final
2026-07-08 06:25:51 INFO  [io.debezium.server.BaseChangeConsumer] (main) Using 'io.debezium.server.BaseChangeConsumer$$Lambda$232/0x000000084030bc40@716e431d' stream name mapper
2026-07-08 06:25:51 INFO  [org.apache.kafka.clients.producer.ProducerConfig] (main) ProducerConfig values:
        acks = -1
        auto.include.jmx.reporter = true
        batch.size = 16384
        bootstrap.servers = [kafka.backend.svc.cluster.local:9092]
        buffer.memory = 33554432
        client.dns.lookup = use_all_dns_ips
        client.id = producer-1
        compression.type = none
        connections.max.idle.ms = 540000
        delivery.timeout.ms = 120000
        enable.idempotence = true
        interceptor.classes = []
        key.serializer = class org.apache.kafka.common.serialization.StringSerializer
        linger.ms = 0
        max.block.ms = 60000
        max.in.flight.requests.per.connection = 5
        max.request.size = 1048576
        metadata.max.age.ms = 300000
        metadata.max.idle.ms = 300000
        metric.reporters = []
        metrics.num.samples = 2
        metrics.recording.level = INFO
        metrics.sample.window.ms = 30000
        partitioner.adaptive.partitioning.enable = true
        partitioner.availability.timeout.ms = 0
        partitioner.class = null
        partitioner.ignore.keys = false
        receive.buffer.bytes = 32768
        reconnect.backoff.max.ms = 1000
        reconnect.backoff.ms = 50
        request.timeout.ms = 30000
        retries = 2147483647
        retry.backoff.ms = 100
        sasl.client.callback.handler.class = null
        sasl.jaas.config = null
        sasl.kerberos.kinit.cmd = /usr/bin/kinit
        sasl.kerberos.min.time.before.relogin = 60000
        sasl.kerberos.service.name = null
        sasl.kerberos.ticket.renew.jitter = 0.05
        sasl.kerberos.ticket.renew.window.factor = 0.8
        sasl.login.callback.handler.class = null
        sasl.login.class = null
        sasl.login.connect.timeout.ms = null
        sasl.login.read.timeout.ms = null
        sasl.login.refresh.buffer.seconds = 300
        sasl.login.refresh.min.period.seconds = 60
        sasl.login.refresh.window.factor = 0.8
        sasl.login.refresh.window.jitter = 0.05
        sasl.login.retry.backoff.max.ms = 10000
        sasl.login.retry.backoff.ms = 100
        sasl.mechanism = GSSAPI
        sasl.oauthbearer.clock.skew.seconds = 30
        sasl.oauthbearer.expected.audience = null
        sasl.oauthbearer.expected.issuer = null
        sasl.oauthbearer.jwks.endpoint.refresh.ms = 3600000
        sasl.oauthbearer.jwks.endpoint.retry.backoff.max.ms = 10000
        sasl.oauthbearer.jwks.endpoint.retry.backoff.ms = 100
        sasl.oauthbearer.jwks.endpoint.url = null
        sasl.oauthbearer.scope.claim.name = scope
        sasl.oauthbearer.sub.claim.name = sub
        sasl.oauthbearer.token.endpoint.url = null
        security.protocol = PLAINTEXT
        security.providers = null
        send.buffer.bytes = 131072
        socket.connection.setup.timeout.max.ms = 30000
        socket.connection.setup.timeout.ms = 10000
        ssl.cipher.suites = null
        ssl.enabled.protocols = [TLSv1.2, TLSv1.3]
        ssl.endpoint.identification.algorithm = https
        ssl.engine.factory.class = null
        ssl.key.password = null
        ssl.keymanager.algorithm = SunX509
        ssl.keystore.certificate.chain = null
        ssl.keystore.key = null
        ssl.keystore.location = null
        ssl.keystore.password = null
        ssl.keystore.type = JKS
        ssl.protocol = TLSv1.3
        ssl.provider = null
        ssl.secure.random.implementation = null
        ssl.trustmanager.algorithm = PKIX
        ssl.truststore.certificates = null
        ssl.truststore.location = null
        ssl.truststore.password = null
        ssl.truststore.type = JKS
        transaction.timeout.ms = 60000
        transactional.id = null
        value.serializer = class org.apache.kafka.common.serialization.StringSerializer

2026-07-08 06:25:51 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Instantiated an idempotent producer.
2026-07-08 06:25:51 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) Kafka version: 3.6.1
2026-07-08 06:25:51 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) Kafka commitId: 5e3c2b738d253ff5
2026-07-08 06:25:51 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) Kafka startTimeMs: 1783491951777
2026-07-08 06:25:51 INFO  [io.debezium.server.kafka.KafkaChangeConsumer] (main) consumer started...
2026-07-08 06:25:51 INFO  [io.debezium.server.DebeziumServer] (main) Consumer 'io.debezium.server.kafka.KafkaChangeConsumer' instantiated
2026-07-08 06:25:51 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = key
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = false

2026-07-08 06:25:51 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = value
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = false

2026-07-08 06:25:51 INFO  [io.debezium.embedded.EmbeddedEngine$EmbeddedConfig] (main) EmbeddedConfig values:
        access.control.allow.methods =
        access.control.allow.origin =
        admin.listeners = null
        auto.include.jmx.reporter = true
        bootstrap.servers = [localhost:9092]
        client.dns.lookup = use_all_dns_ips
        config.providers = []
        connector.client.config.override.policy = All
        header.converter = class org.apache.kafka.connect.storage.SimpleHeaderConverter
        key.converter = class org.apache.kafka.connect.json.JsonConverter
        listeners = [http://:8083]
        metric.reporters = []
        metrics.num.samples = 2
        metrics.recording.level = INFO
        metrics.sample.window.ms = 30000
        offset.flush.interval.ms = 60000
        offset.flush.timeout.ms = 5000
        offset.storage.file.filename = /debezium/data/offsets.dat
        offset.storage.partitions = null
        offset.storage.replication.factor = null
        offset.storage.topic =
        plugin.discovery = hybrid_warn
        plugin.path = null
        response.http.headers.config =
        rest.advertised.host.name = null
        rest.advertised.listener = null
        rest.advertised.port = null
        rest.extension.classes = []
        ssl.cipher.suites = null
        ssl.client.auth = none
        ssl.enabled.protocols = [TLSv1.2, TLSv1.3]
        ssl.endpoint.identification.algorithm = https
        ssl.engine.factory.class = null
        ssl.key.password = null
        ssl.keymanager.algorithm = SunX509
        ssl.keystore.certificate.chain = null
        ssl.keystore.key = null
        ssl.keystore.location = null
        ssl.keystore.password = null
        ssl.keystore.type = JKS
        ssl.protocol = TLSv1.3
        ssl.provider = null
        ssl.secure.random.implementation = null
        ssl.trustmanager.algorithm = PKIX
        ssl.truststore.certificates = null
        ssl.truststore.location = null
        ssl.truststore.password = null
        ssl.truststore.type = JKS
        task.shutdown.graceful.timeout.ms = 5000
        topic.creation.enable = true
        topic.tracking.allow.reset = true
        topic.tracking.enable = true
        value.converter = class org.apache.kafka.connect.json.JsonConverter

2026-07-08 06:25:51 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = key
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = true

2026-07-08 06:25:51 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = value
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = true

2026-07-08 06:25:51 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = header
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = true

2026-07-08 06:25:51 INFO  [io.debezium.server.DebeziumServer] (main) Engine executor started
2026-07-08 06:25:52 INFO  [io.debezium.config.CommonConnectorConfig] (pool-7-thread-1) Loading the custom source info struct maker plugin: io.debezium.connector.oracle.OracleSourceInfoStructMaker
2026-07-08 06:25:52 INFO  [io.quarkus] (main) debezium-server-dist 2.5.4.Final on JVM (powered by Quarkus 3.2.10.Final) started in 2.321s. Listening on: http://0.0.0.0:8080
2026-07-08 06:25:52 INFO  [io.quarkus] (main) Profile prod activated.
2026-07-08 06:25:52 INFO  [io.quarkus] (main) Installed features: [cdi, kubernetes-client, resteasy-jackson, smallrye-context-propagation, smallrye-health, vertx]
2026-07-08 06:25:52 INFO  [org.apache.kafka.clients.Metadata] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-07-08 06:25:52 INFO  [org.apache.kafka.clients.producer.internals.TransactionManager] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] ProducerId set to 1003 with epoch 0
2026-07-08 06:25:52 ERROR [io.debezium.connector.oracle.OracleConnector] (pool-7-thread-1) Failed testing connection for {connector.class=io.debezium.connector.oracle.OracleConnector, schema.history.internal.kafka.key.serializer=org.apache.kafka.common.serialization.StringSerializer, heartbeat.topics.prefix=heartbeat, errors.retry.delay.initial.ms=300, key.converter=org.apache.kafka.connect.json.JsonConverter, database.dbname=fincorepdb1, database.user=c##debezium, offset.storage=org.apache.kafka.connect.storage.FileOffsetBackingStore, header.converter.key=json, schema.history.internal.kafka.bootstrap.servers=kafka.backend.svc.cluster.local:9092, heartbeat.interval.ms=2000, schema.history.internal.kafka.producer.value.serializer=org.apache.kafka.common.serialization.StringSerializer , errors.max.retries=-1, database.password=********, name=kafka, tasks.max=1, log.mining.strategy=online_catalog, schema.history.internal.kafka.producer.key.serializer=org.apache.kafka.common.serialization.StringSerializer, database.sid=fincorepdb1, topic.prefix=fincore, decimal.handling.mode=string, offset.storage.file.filename=/debezium/data/offsets.dat, schema.history.internal.kafka.topic=schema-changes.oracle, log.mining.continuous.mine=false, log.mining.sleep.time.max=2000, log.mining.sleep.time.default=50, value.converter=org.apache.kafka.connect.json.JsonConverter, offset.storage.kafka.producer.value.serializer=org.apache.kafka.common.serialization.StringSerializer , schema.history.internal.kafka.producer.bootstrap.servers=kafka.backend.svc.cluster.local:9092, header.converter.value=json, offset.storage.kafka.key.serializer=org.apache.kafka.common.serialization.StringSerializer, log.mining.batch.size.max=100000, database.pdb.name=fincorepdb1, database.connection.adapter=logminer, key.converter.value=json, database.server.name=fincorepdb1, offset.flush.timeout.ms=5000, errors.retry.delay.max.ms=10000, offset.storage.kafka.value.serializer=org.apache.kafka.common.serialization.StringSerializer, value.converter.value=json, database.port=1523, offset.flush.interval.ms=60000, offset.storage.kafka.producer.bootstrap.servers=kafka.backend.svc.cluster.local:9092, database.hostname=10.177.179.145, log.mining.batch.size.default=50000, table.include.list=fincore.NOTIFICATIONS,fincore.USER_ROLES,fincore.PROCESS_STATUS,fincore.PERMISSIONS,fincore.ROLE_PERMISSIONS, value.converter.key=json, offset.storage.kafka.producer.key.serializer=org.apache.kafka.common.serialization.StringSerializer, key.converter.key=json, schema.history.internal.kafka.value.serializer=org.apache.kafka.common.serialization.StringSerializer} with user '[database.user,null,[],[],true]': java.lang.RuntimeException: Failed to resolve Oracle database version
        at io.debezium.connector.oracle.OracleConnection.resolveOracleDatabaseVersion(OracleConnection.java:190)
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
Caused by: java.sql.SQLException: Listener refused the connection with the following error:
ORA-12516, TNS:listener could not find available handler with matching protocol stack
  (CONNECTION_ID=ynk9wbM0Sj21CP3e81vMqQ==)
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
Caused by: oracle.net.ns.NetException: Listener refused the connection with the following error:
ORA-12516, TNS:listener could not find available handler with matching protocol stack
  (CONNECTION_ID=ynk9wbM0Sj21CP3e81vMqQ==)
        at oracle.net.ns.NSProtocolNIO.createRefusePacketException(NSProtocolNIO.java:830)
        at oracle.net.ns.NSProtocolNIO.handleConnectPacketResponse(NSProtocolNIO.java:407)
        at oracle.net.ns.NSProtocolNIO.negotiateConnection(NSProtocolNIO.java:218)
        at oracle.net.ns.NSProtocol.connect(NSProtocol.java:355)
        at oracle.jdbc.driver.T4CConnection.connect(T4CConnection.java:2652)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:669)
        ... 24 more

2026-07-08 06:25:52 ERROR [io.debezium.server.ConnectorLifecycle] (pool-7-thread-1) Connector completed: success = 'false', message = 'Connector configuration is not valid. Unable to connect: Failed to resolve Oracle database version', error = 'null'
2026-07-08 06:25:52 INFO  [io.debezium.server.DebeziumServer] (main) Received request to stop the engine
2026-07-08 06:25:52 INFO  [io.debezium.embedded.EmbeddedEngine] (main) Stopping the embedded engine
2026-07-08 06:25:52 INFO  [io.debezium.server.kafka.KafkaChangeConsumer] (main) consumer destroyed...
2026-07-08 06:25:52 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Closing the Kafka producer with timeoutMillis = 5000 ms.
2026-07-08 06:25:52 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics scheduler closed
2026-07-08 06:25:52 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-08 06:25:52 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics reporters closed
2026-07-08 06:25:52 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) App info kafka.producer for producer-1 unregistered
2026-07-08 06:25:52 INFO  [io.quarkus] (main) debezium-server-dist stopped in 0.056s
