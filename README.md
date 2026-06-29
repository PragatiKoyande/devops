2026-06-23 07:28:55 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Instantiated an idempotent producer.
2026-06-23 07:28:55 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) Kafka version: 3.6.1
2026-06-23 07:28:55 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) Kafka commitId: 5e3c2b738d253ff5
2026-06-23 07:28:55 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) Kafka startTimeMs: 1782199735039
2026-06-23 07:28:55 INFO  [io.debezium.server.kafka.KafkaChangeConsumer] (main) consumer started...
2026-06-23 07:28:55 INFO  [io.debezium.server.DebeziumServer] (main) Consumer 'io.debezium.server.kafka.KafkaChangeConsumer' instantiated
2026-06-23 07:28:55 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = key
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = false

2026-06-23 07:28:55 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = value
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = false

2026-06-23 07:28:55 INFO  [io.debezium.embedded.EmbeddedEngine$EmbeddedConfig] (main) EmbeddedConfig values:
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

2026-06-23 07:28:55 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = key
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = true

2026-06-23 07:28:55 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = value
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = true

2026-06-23 07:28:55 INFO  [org.apache.kafka.connect.json.JsonConverterConfig] (main) JsonConverterConfig values:
        converter.type = header
        decimal.format = BASE64
        replace.null.with.default = true
        schemas.cache.size = 1000
        schemas.enable = true

2026-06-23 07:28:55 INFO  [io.debezium.server.DebeziumServer] (main) Engine executor started
2026-06-23 07:28:55 INFO  [io.debezium.config.CommonConnectorConfig] (pool-7-thread-1) Loading the custom source info struct maker plugin: io.debezium.connector.oracle.OracleSourceInfoStructMaker
2026-06-23 07:28:55 INFO  [io.quarkus] (main) debezium-server-dist 2.5.4.Final on JVM (powered by Quarkus 3.2.10.Final) started in 1.788s. Listening on: http://0.0.0.0:8080
2026-06-23 07:28:55 INFO  [io.quarkus] (main) Profile prod activated.
2026-06-23 07:28:55 INFO  [io.quarkus] (main) Installed features: [cdi, kubernetes-client, resteasy-jackson, smallrye-context-propagation, smallrye-health, vertx]
2026-06-23 07:28:55 INFO  [org.apache.kafka.clients.Metadata] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-06-23 07:28:55 INFO  [org.apache.kafka.clients.producer.internals.TransactionManager] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] ProducerId set to 30643 with epoch 0
2026-06-23 07:37:55 INFO  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Node -1 disconnected.
