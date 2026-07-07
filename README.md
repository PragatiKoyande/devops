2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.Metadata] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting generation and member id due to: consumer pro-actively leaving the group
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.ConsumerConfig] (pool-7-thread-1) ConsumerConfig values:
        allow.auto.create.topics = true
        auto.commit.interval.ms = 5000
        auto.include.jmx.reporter = true
        auto.offset.reset = earliest
        bootstrap.servers = [kafka.backend.svc.cluster.local:9092]
        check.crcs = true
        client.dns.lookup = use_all_dns_ips
        client.id = fincore-schemahistory
        client.rack =
        connections.max.idle.ms = 540000
        default.api.timeout.ms = 60000
        enable.auto.commit = false
        exclude.internal.topics = true
        fetch.max.bytes = 52428800
        fetch.max.wait.ms = 500
        fetch.min.bytes = 1
        group.id = fincore-schemahistory
        group.instance.id = null
        heartbeat.interval.ms = 3000
        interceptor.classes = []
        internal.leave.group.on.close = true
        internal.throw.on.fetch.stable.offset.unsupported = false
        isolation.level = read_uncommitted
        key.deserializer = class org.apache.kafka.common.serialization.StringDeserializer
        max.partition.fetch.bytes = 1048576
        max.poll.interval.ms = 300000
        max.poll.records = 500
        metadata.max.age.ms = 300000
        metric.reporters = []
        metrics.num.samples = 2
        metrics.recording.level = INFO
        metrics.sample.window.ms = 30000
        partition.assignment.strategy = [class org.apache.kafka.clients.consumer.RangeAssignor, class org.apache.kafka.clients.consumer.CooperativeStickyAssignor]
        receive.buffer.bytes = 65536
        reconnect.backoff.max.ms = 1000
        reconnect.backoff.ms = 50
        request.timeout.ms = 30000
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
        session.timeout.ms = 10000
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
        value.deserializer = class org.apache.kafka.common.serialization.StringDeserializer

2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka version: 3.6.1
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka commitId: 5e3c2b738d253ff5
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka startTimeMs: 1783428474829
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.admin.AdminClientConfig] (debezium-oracleconnector-fincore-db-history-config-check) These configurations '[value.serializer, acks, batch.size, max.block.ms, buffer.memory, key.serializer, linger.ms]' were supplied but are not used yet.
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka version: 3.6.1
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka commitId: 5e3c2b738d253ff5
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka startTimeMs: 1783428474832
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.Metadata] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting generation and member id due to: consumer pro-actively leaving the group
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.ConsumerConfig] (pool-7-thread-1) ConsumerConfig values:
        allow.auto.create.topics = true
        auto.commit.interval.ms = 5000
        auto.include.jmx.reporter = true
        auto.offset.reset = earliest
        bootstrap.servers = [kafka.backend.svc.cluster.local:9092]
        check.crcs = true
        client.dns.lookup = use_all_dns_ips
        client.id = fincore-schemahistory
        client.rack =
        connections.max.idle.ms = 540000
        default.api.timeout.ms = 60000
        enable.auto.commit = false
        exclude.internal.topics = true
        fetch.max.bytes = 52428800
        fetch.max.wait.ms = 500
        fetch.min.bytes = 1
        group.id = fincore-schemahistory
        group.instance.id = null
        heartbeat.interval.ms = 3000
        interceptor.classes = []
        internal.leave.group.on.close = true
        internal.throw.on.fetch.stable.offset.unsupported = false
        isolation.level = read_uncommitted
        key.deserializer = class org.apache.kafka.common.serialization.StringDeserializer
        max.partition.fetch.bytes = 1048576
        max.poll.interval.ms = 300000
        max.poll.records = 500
        metadata.max.age.ms = 300000
        metric.reporters = []
        metrics.num.samples = 2
        metrics.recording.level = INFO
        metrics.sample.window.ms = 30000
        partition.assignment.strategy = [class org.apache.kafka.clients.consumer.RangeAssignor, class org.apache.kafka.clients.consumer.CooperativeStickyAssignor]
        receive.buffer.bytes = 65536
        reconnect.backoff.max.ms = 1000
        reconnect.backoff.ms = 50
        request.timeout.ms = 30000
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
        session.timeout.ms = 10000
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
        value.deserializer = class org.apache.kafka.common.serialization.StringDeserializer

2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka version: 3.6.1
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka commitId: 5e3c2b738d253ff5
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka startTimeMs: 1783428474841
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.Metadata] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting generation and member id due to: consumer pro-actively leaving the group
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-07-07 12:47:54 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Started database schema history recovery
2026-07-07 12:47:54 INFO  [io.debezium.storage.kafka.history.KafkaSchemaHistory] (debezium-oracleconnector-fincore-db-history-config-check) Database schema history topic 'schema-changes.oracle' has correct settings
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (kafka-admin-client-thread | fincore-schemahistory-topic-check) App info kafka.admin.client for fincore-schemahistory-topic-check unregistered
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics scheduler closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics reporters closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.admin.AdminClientConfig] (debezium-oracleconnector-fincore-db-history-config-check) AdminClientConfig values:
        auto.include.jmx.reporter = true
        bootstrap.servers = [kafka.backend.svc.cluster.local:9092]
        client.dns.lookup = use_all_dns_ips
        client.id = fincore-schemahistory-topic-check
        connections.max.idle.ms = 300000
        default.api.timeout.ms = 60000
        metadata.max.age.ms = 300000
        metric.reporters = []
        metrics.num.samples = 2
        metrics.recording.level = INFO
        metrics.sample.window.ms = 30000
        receive.buffer.bytes = 65536
        reconnect.backoff.max.ms = 1000
        reconnect.backoff.ms = 50
        request.timeout.ms = 30000
        retries = 1
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

2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.admin.AdminClientConfig] (debezium-oracleconnector-fincore-db-history-config-check) These configurations '[value.serializer, acks, batch.size, max.block.ms, buffer.memory, key.serializer, linger.ms]' were supplied but are not used yet.
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka version: 3.6.1
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka commitId: 5e3c2b738d253ff5
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka startTimeMs: 1783428474854
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.ConsumerConfig] (pool-7-thread-1) ConsumerConfig values:
        allow.auto.create.topics = true
        auto.commit.interval.ms = 5000
        auto.include.jmx.reporter = true
        auto.offset.reset = earliest
        bootstrap.servers = [kafka.backend.svc.cluster.local:9092]
        check.crcs = true
        client.dns.lookup = use_all_dns_ips
        client.id = fincore-schemahistory
        client.rack =
        connections.max.idle.ms = 540000
        default.api.timeout.ms = 60000
        enable.auto.commit = false
        exclude.internal.topics = true
        fetch.max.bytes = 52428800
        fetch.max.wait.ms = 500
        fetch.min.bytes = 1
        group.id = fincore-schemahistory
        group.instance.id = null
        heartbeat.interval.ms = 3000
        interceptor.classes = []
        internal.leave.group.on.close = true
        internal.throw.on.fetch.stable.offset.unsupported = false
        isolation.level = read_uncommitted
        key.deserializer = class org.apache.kafka.common.serialization.StringDeserializer
        max.partition.fetch.bytes = 1048576
        max.poll.interval.ms = 300000
        max.poll.records = 500
        metadata.max.age.ms = 300000
        metric.reporters = []
        metrics.num.samples = 2
        metrics.recording.level = INFO
        metrics.sample.window.ms = 30000
        partition.assignment.strategy = [class org.apache.kafka.clients.consumer.RangeAssignor, class org.apache.kafka.clients.consumer.CooperativeStickyAssignor]
        receive.buffer.bytes = 65536
        reconnect.backoff.max.ms = 1000
        reconnect.backoff.ms = 50
        request.timeout.ms = 30000
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
        session.timeout.ms = 10000
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
        value.deserializer = class org.apache.kafka.common.serialization.StringDeserializer

2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka version: 3.6.1
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka commitId: 5e3c2b738d253ff5
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka startTimeMs: 1783428474858
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.KafkaConsumer] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Subscribed to topic(s): schema-changes.oracle
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.Metadata] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-07-07 12:47:54 INFO  [io.debezium.storage.kafka.history.KafkaSchemaHistory] (debezium-oracleconnector-fincore-db-history-config-check) Database schema history topic 'schema-changes.oracle' has correct settings
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.utils.AppInfoParser] (kafka-admin-client-thread | fincore-schemahistory-topic-check) App info kafka.admin.client for fincore-schemahistory-topic-check unregistered
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics scheduler closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-07 12:47:54 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics reporters closed
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Discovered group coordinator kafka-0.kafka.backend.svc.cluster.local:9092 (id: 2147483646 rack: null)
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] (Re-)joining group
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: need to re-join with the given member-id: fincore-schemahistory-28e6884c-e905-4d45-8934-4483119e7049
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: rebalance failed due to 'The group member needs to have a valid member id before actually entering a consumer group.' (MemberIdRequiredException)
2026-07-07 12:47:54 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] (Re-)joining group
2026-07-07 12:47:57 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Successfully joined group with generation Generation{generationId=1, memberId='fincore-schemahistory-28e6884c-e905-4d45-8934-4483119e7049', protocol='range'}
2026-07-07 12:47:57 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Finished assignment for group at generation 1: {fincore-schemahistory-28e6884c-e905-4d45-8934-4483119e7049=Assignment(partitions=[schema-changes.oracle-0])}
2026-07-07 12:47:57 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Successfully synced group in generation Generation{generationId=1, memberId='fincore-schemahistory-28e6884c-e905-4d45-8934-4483119e7049', protocol='range'}
2026-07-07 12:47:57 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Notifying assignor about the new Assignment(partitions=[schema-changes.oracle-0])
2026-07-07 12:47:57 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Adding newly assigned partitions: schema-changes.oracle-0
2026-07-07 12:47:57 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Found no committed offset for partition schema-changes.oracle-0
2026-07-07 12:47:57 INFO  [org.apache.kafka.clients.consumer.internals.SubscriptionState] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting offset for partition schema-changes.oracle-0 to position FetchPosition{offset=0, offsetEpoch=Optional.empty, currentLeader=LeaderAndEpoch{leader=Optional[kafka-0.kafka.backend.svc.cluster.local:9092 (id: 1 rack: null)], epoch=6}}.
2026-07-07 12:47:58 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Database schema history recovery in progress, recovered 1 records
2026-07-07 12:47:58 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Already applied 1 database changes
2026-07-07 12:47:59 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Already applied 131 database changes
2026-07-07 12:47:59 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Revoke previously assigned partitions schema-changes.oracle-0
2026-07-07 12:47:59 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Member fincore-schemahistory-28e6884c-e905-4d45-8934-4483119e7049 sending LeaveGroup request to coordinator kafka-0.kafka.backend.svc.cluster.local:9092 (id: 2147483646 rack: null) due to the consumer is being closed
2026-07-07 12:47:59 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting generation and member id due to: consumer pro-actively leaving the group
2026-07-07 12:47:59 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-07-07 12:47:59 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-07-07 12:47:59 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-07 12:47:59 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-07-07 12:47:59 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-07-07 12:47:59 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Finished database schema history recovery of 131 change(s) in 4219 ms
2026-07-07 12:47:59 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."PROCESS_STATUS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-07-07 12:47:59 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."PROCESS_STATUS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-07-07 12:47:59 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Mapper for type '-3' not found.
2026-07-07 12:47:59 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Mapper for type '-3' not found.
2026-07-07 12:47:59 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."MENU_ITEMS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-07-07 12:47:59 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."MENU_ITEMS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-07-07 12:47:59 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = SignalProcessor
2026-07-07 12:47:59 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = change-event-source-coordinator
2026-07-07 12:47:59 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = blocking-snapshot
2026-07-07 12:47:59 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Creating thread debezium-oracleconnector-fincore-change-event-source-coordinator
2026-07-07 12:47:59 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Metrics registered
2026-07-07 12:47:59 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Context created
2026-07-07 12:47:59 INFO  [io.debezium.connector.oracle.OracleSnapshotChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) The previous offset has been found.
2026-07-07 12:47:59 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Snapshot ended with SnapshotResult [status=SKIPPED, offset=OracleOffsetContext [scn=198878588, commit_scn=["198880467:1:11000800842f0000"]]]
2026-07-07 12:47:59 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Connected metrics set to 'true'
2026-07-07 12:47:59 INFO  [io.debezium.pipeline.signal.SignalProcessor] (debezium-oracleconnector-fincore-change-event-source-coordinator) SignalProcessor started. Scheduling it every 5000ms
2026-07-07 12:47:59 INFO  [io.debezium.util.Threads] (debezium-oracleconnector-fincore-change-event-source-coordinator) Creating thread debezium-oracleconnector-fincore-SignalProcessor
2026-07-07 12:47:59 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Starting streaming
2026-07-07 12:47:59 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Redo Log Group Sizes:
2026-07-07 12:47:59 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator)         Group #1: 209715200 bytes
2026-07-07 12:47:59 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator)         Group #2: 209715200 bytes
2026-07-07 12:47:59 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator)         Group #3: 209715200 bytes
2026-07-07 12:48:04 ERROR [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Mining session stopped due to error.: io.debezium.text.ParsingException: DDL statement couldn't be parsed. Please open a Jira issue with the statement 'ALTER TABLE GL_BALANCE DROP PARTITIONS  FOR (TO_DATE(' 2026-03-30 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-03-31 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-01 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-02 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-03 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-04 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-05 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-06 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-07 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-08 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-09 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-10 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-11 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-12 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-13 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-14 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-15 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-16 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-17 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-18 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-19 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-20 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-21 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-22 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-23 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-24 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-25 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-26 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-27 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-28 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-29 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) update indexes;'
mismatched input ',' expecting {<EOF>, '/', ';'}
        at io.debezium.antlr.ParsingErrorListener.syntaxError(ParsingErrorListener.java:43)
        at org.antlr.v4.runtime.ProxyErrorListener.syntaxError(ProxyErrorListener.java:41)
        at org.antlr.v4.runtime.Parser.notifyErrorListeners(Parser.java:543)
        at org.antlr.v4.runtime.DefaultErrorStrategy.reportInputMismatch(DefaultErrorStrategy.java:327)
        at org.antlr.v4.runtime.DefaultErrorStrategy.reportError(DefaultErrorStrategy.java:139)
        at io.debezium.ddl.parser.oracle.generated.PlSqlParser.sql_script(PlSqlParser.java:2197)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parseTree(OracleDdlParser.java:73)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parseTree(OracleDdlParser.java:32)
        at io.debezium.antlr.AntlrDdlParser.parse(AntlrDdlParser.java:78)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parse(OracleDdlParser.java:68)
        at io.debezium.connector.oracle.OracleSchemaChangeEventEmitter.emitSchemaChangeEvent(OracleSchemaChangeEventEmitter.java:84)
        at io.debezium.pipeline.EventDispatcher.dispatchSchemaChangeEvent(EventDispatcher.java:379)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.handleSchemaChange(AbstractLogMinerEventProcessor.java:773)
        at io.debezium.connector.oracle.logminer.processor.memory.MemoryLogMinerEventProcessor.handleSchemaChange(MemoryLogMinerEventProcessor.java:176)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.processRow(AbstractLogMinerEventProcessor.java:368)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.processResults(AbstractLogMinerEventProcessor.java:314)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.process(AbstractLogMinerEventProcessor.java:235)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:248)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)
Caused by: org.antlr.v4.runtime.InputMismatchException
        at org.antlr.v4.runtime.DefaultErrorStrategy.sync(DefaultErrorStrategy.java:270)
        at io.debezium.ddl.parser.oracle.generated.PlSqlParser.sql_script(PlSqlParser.java:2129)
        ... 21 more

2026-07-07 12:48:04 ERROR [io.debezium.pipeline.ErrorHandler] (debezium-oracleconnector-fincore-change-event-source-coordinator) Producer failure: io.debezium.text.ParsingException: DDL statement couldn't be parsed. Please open a Jira issue with the statement 'ALTER TABLE GL_BALANCE DROP PARTITIONS  FOR (TO_DATE(' 2026-03-30 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-03-31 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-01 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-02 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-03 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-04 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-05 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-06 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-07 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-08 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-09 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-10 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-11 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-12 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-13 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-14 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-15 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-16 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-17 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-18 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-19 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-20 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-21 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-22 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-23 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-24 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-25 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-26 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-27 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-28 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-29 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) update indexes;'
mismatched input ',' expecting {<EOF>, '/', ';'}
        at io.debezium.antlr.ParsingErrorListener.syntaxError(ParsingErrorListener.java:43)
        at org.antlr.v4.runtime.ProxyErrorListener.syntaxError(ProxyErrorListener.java:41)
        at org.antlr.v4.runtime.Parser.notifyErrorListeners(Parser.java:543)
        at org.antlr.v4.runtime.DefaultErrorStrategy.reportInputMismatch(DefaultErrorStrategy.java:327)
        at org.antlr.v4.runtime.DefaultErrorStrategy.reportError(DefaultErrorStrategy.java:139)
        at io.debezium.ddl.parser.oracle.generated.PlSqlParser.sql_script(PlSqlParser.java:2197)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parseTree(OracleDdlParser.java:73)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parseTree(OracleDdlParser.java:32)
        at io.debezium.antlr.AntlrDdlParser.parse(AntlrDdlParser.java:78)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parse(OracleDdlParser.java:68)
        at io.debezium.connector.oracle.OracleSchemaChangeEventEmitter.emitSchemaChangeEvent(OracleSchemaChangeEventEmitter.java:84)
        at io.debezium.pipeline.EventDispatcher.dispatchSchemaChangeEvent(EventDispatcher.java:379)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.handleSchemaChange(AbstractLogMinerEventProcessor.java:773)
        at io.debezium.connector.oracle.logminer.processor.memory.MemoryLogMinerEventProcessor.handleSchemaChange(MemoryLogMinerEventProcessor.java:176)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.processRow(AbstractLogMinerEventProcessor.java:368)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.processResults(AbstractLogMinerEventProcessor.java:314)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.process(AbstractLogMinerEventProcessor.java:235)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:248)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)
Caused by: org.antlr.v4.runtime.InputMismatchException
        at org.antlr.v4.runtime.DefaultErrorStrategy.sync(DefaultErrorStrategy.java:270)
        at io.debezium.ddl.parser.oracle.generated.PlSqlParser.sql_script(PlSqlParser.java:2129)
        ... 21 more

2026-07-07 12:48:04 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) startScn=198878588, endScn=198928588
2026-07-07 12:48:04 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Streaming metrics dump: LogMinerStreamingChangeEventSourceMetrics{connectorConfig=io.debezium.connector.oracle.OracleConnectorConfig@68cb16d2, startTime=2026-07-07T12:47:59.115131Z, clock=SystemClock[Z], currentScn=220619319, offsetScn=null, commitScn=null, oldestScn=-1, oldestScnTime=null, currentLogFileNames=[Ljava.lang.String;@64c7cb48, redoLogStatuses=[Ljava.lang.String;@4ee70a41, databaseZoneOffset=+05:30, batchSize=51000, logSwitchCount=0, logMinerQueryCount=1, sleepTime=800, minimumLogsMined=1, maximumLogsMined=1, maxBatchProcessingThroughput=0, timeDifference=3, processedRowsCount=0, activeTransactionCount=1, rolledBackTransactionCount=0, oversizedTransactionCount=0, changesCount=0, scnFreezeCount=0, batchProcessingDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@633f591a, fetchQueryDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@5372ae29, commitDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@935b284, lagFromSourceDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@7f7614e1, miningSessionStartupDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@6618659c, parseTimeDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@20dd9c90, resultSetNextDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@458ab9d, userGlobalAreaMemory=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$MaxLongValueMetric@4b4666eb, processGlobalAreaMemory=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$MaxLongValueMetric@6e57ce9a, abandonedTransactionIds=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$LRUSet@22a2f6dc, rolledBackTransactionIds=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$LRUSet@6367b556} io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics@87a0772
2026-07-07 12:48:04 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Offsets: OracleOffsetContext [scn=198880483, commit_scn=["198880483:1:0d001200de390000"]]
2026-07-07 12:48:04 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Finished streaming
2026-07-07 12:48:04 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Connected metrics set to 'false'
2026-07-07 12:48:04 INFO  [io.debezium.embedded.EmbeddedEngine] (pool-7-thread-1) Stopping the task and engine
2026-07-07 12:48:04 INFO  [io.debezium.connector.common.BaseSourceTask] (pool-7-thread-1) Stopping down connector
2026-07-07 12:48:04 INFO  [io.debezium.pipeline.signal.SignalProcessor] (pool-7-thread-1) SignalProcessor stopped
2026-07-07 12:48:04 INFO  [io.debezium.service.DefaultServiceRegistry] (pool-7-thread-1) Debezium ServiceRegistry stopped.
2026-07-07 12:48:04 INFO  [io.debezium.jdbc.JdbcConnection] (pool-9-thread-1) Connection gracefully closed
2026-07-07 12:48:04 INFO  [io.debezium.jdbc.JdbcConnection] (pool-10-thread-1) Connection gracefully closed
2026-07-07 12:48:04 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (pool-7-thread-1) [Producer clientId=fincore-schemahistory] Closing the Kafka producer with timeoutMillis = 30000 ms.
2026-07-07 12:48:04 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-07-07 12:48:04 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-07 12:48:04 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-07-07 12:48:04 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.producer for fincore-schemahistory unregistered
2026-07-07 12:48:04 INFO  [org.apache.kafka.connect.storage.FileOffsetBackingStore] (pool-7-thread-1) Stopped FileOffsetBackingStore
2026-07-07 12:48:04 ERROR [io.debezium.server.ConnectorLifecycle] (pool-7-thread-1) Connector completed: success = 'false', message = 'Error while trying to run connector class 'io.debezium.connector.oracle.OracleConnector'', error = 'org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.': org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.
        at io.debezium.pipeline.ErrorHandler.setProducerThrowable(ErrorHandler.java:67)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:269)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)
Caused by: io.debezium.text.ParsingException: DDL statement couldn't be parsed. Please open a Jira issue with the statement 'ALTER TABLE GL_BALANCE DROP PARTITIONS  FOR (TO_DATE(' 2026-03-30 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-03-31 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-01 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-02 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-03 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-04 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-05 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-06 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-07 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-08 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-09 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-10 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-11 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-12 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-13 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-14 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-15 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-16 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-17 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-18 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-19 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-20 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-21 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-22 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-23 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-24 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-25 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-26 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-27 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-28 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) , FOR (TO_DATE(' 2026-04-29 00:00:00', 'SYYYY-MM-DD HH24:MI:SS', 'NLS_CALENDAR=GREGORIAN')) update indexes;'
mismatched input ',' expecting {<EOF>, '/', ';'}
        at io.debezium.antlr.ParsingErrorListener.syntaxError(ParsingErrorListener.java:43)
        at org.antlr.v4.runtime.ProxyErrorListener.syntaxError(ProxyErrorListener.java:41)
        at org.antlr.v4.runtime.Parser.notifyErrorListeners(Parser.java:543)
        at org.antlr.v4.runtime.DefaultErrorStrategy.reportInputMismatch(DefaultErrorStrategy.java:327)
        at org.antlr.v4.runtime.DefaultErrorStrategy.reportError(DefaultErrorStrategy.java:139)
        at io.debezium.ddl.parser.oracle.generated.PlSqlParser.sql_script(PlSqlParser.java:2197)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parseTree(OracleDdlParser.java:73)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parseTree(OracleDdlParser.java:32)
        at io.debezium.antlr.AntlrDdlParser.parse(AntlrDdlParser.java:78)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parse(OracleDdlParser.java:68)
        at io.debezium.connector.oracle.OracleSchemaChangeEventEmitter.emitSchemaChangeEvent(OracleSchemaChangeEventEmitter.java:84)
        at io.debezium.pipeline.EventDispatcher.dispatchSchemaChangeEvent(EventDispatcher.java:379)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.handleSchemaChange(AbstractLogMinerEventProcessor.java:773)
        at io.debezium.connector.oracle.logminer.processor.memory.MemoryLogMinerEventProcessor.handleSchemaChange(MemoryLogMinerEventProcessor.java:176)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.processRow(AbstractLogMinerEventProcessor.java:368)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.processResults(AbstractLogMinerEventProcessor.java:314)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.process(AbstractLogMinerEventProcessor.java:235)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:248)
        ... 9 more
Caused by: org.antlr.v4.runtime.InputMismatchException
        at org.antlr.v4.runtime.DefaultErrorStrategy.sync(DefaultErrorStrategy.java:270)
        at io.debezium.ddl.parser.oracle.generated.PlSqlParser.sql_script(PlSqlParser.java:2129)
        ... 21 more

2026-07-07 12:48:04 INFO  [io.debezium.server.DebeziumServer] (main) Received request to stop the engine
2026-07-07 12:48:04 INFO  [io.debezium.embedded.EmbeddedEngine] (main) Stopping the embedded engine
2026-07-07 12:48:04 INFO  [io.debezium.server.kafka.KafkaChangeConsumer] (main) consumer destroyed...
2026-07-07 12:48:04 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Closing the Kafka producer with timeoutMillis = 5000 ms.
2026-07-07 12:48:04 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics scheduler closed
2026-07-07 12:48:04 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-07 12:48:04 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics reporters closed
2026-07-07 12:48:04 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) App info kafka.producer for producer-1 unregistered
2026-07-07 12:48:04 INFO  [io.quarkus] (main) debezium-server-dist stopped in 0.032s
