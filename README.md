        ssl.truststore.password = null
        ssl.truststore.type = JKS
        value.deserializer = class org.apache.kafka.common.serialization.StringDeserializer

2026-11-26 06:26:36 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka version: 3.6.1
2026-11-26 06:26:36 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka commitId: 5e3c2b738d253ff5
2026-11-26 06:26:36 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka startTimeMs: 1795674396951
2026-11-26 06:26:36 INFO  [org.apache.kafka.clients.Metadata] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-11-26 06:26:36 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting generation and member id due to: consumer pro-actively leaving the group
2026-11-26 06:26:36 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-11-26 06:26:36 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-11-26 06:26:36 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-11-26 06:26:36 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-11-26 06:26:36 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-11-26 06:26:36 INFO  [org.apache.kafka.clients.consumer.ConsumerConfig] (pool-7-thread-1) ConsumerConfig values:
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

2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka version: 3.6.1
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka commitId: 5e3c2b738d253ff5
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka startTimeMs: 1795674397000
2026-11-26 06:26:37 INFO  [io.debezium.storage.kafka.history.KafkaSchemaHistory] (debezium-oracleconnector-fincore-db-history-config-check) Database schema history topic 'schema-changes.oracle' has correct settings
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (kafka-admin-client-thread | fincore-schemahistory-topic-check) App info kafka.admin.client for fincore-schemahistory-topic-check unregistered
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.Metadata] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics scheduler closed
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics reporters closed
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.admin.AdminClientConfig] (debezium-oracleconnector-fincore-db-history-config-check) AdminClientConfig values:
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

2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.admin.AdminClientConfig] (debezium-oracleconnector-fincore-db-history-config-check) These configurations '[value.serializer, acks, batch.size, max.block.ms, buffer.memory, key.serializer, linger.ms]' were supplied but are not used yet.
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka version: 3.6.1
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka commitId: 5e3c2b738d253ff5
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka startTimeMs: 1795674397006
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting generation and member id due to: consumer pro-actively leaving the group
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-11-26 06:26:37 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Started database schema history recovery
2026-11-26 06:26:37 INFO  [io.debezium.storage.kafka.history.KafkaSchemaHistory] (debezium-oracleconnector-fincore-db-history-config-check) Database schema history topic 'schema-changes.oracle' has correct settings
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (kafka-admin-client-thread | fincore-schemahistory-topic-check) App info kafka.admin.client for fincore-schemahistory-topic-check unregistered
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics scheduler closed
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics reporters closed
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.consumer.ConsumerConfig] (pool-7-thread-1) ConsumerConfig values:
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

2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka version: 3.6.1
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka commitId: 5e3c2b738d253ff5
2026-11-26 06:26:37 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka startTimeMs: 1795674397021
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.consumer.KafkaConsumer] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Subscribed to topic(s): schema-changes.oracle
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.Metadata] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Discovered group coordinator kafka-0.kafka.backend.svc.cluster.local:9092 (id: 2147483646 rack: null)
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] (Re-)joining group
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: need to re-join with the given member-id: fincore-schemahistory-82d8cfa8-c633-48c8-8485-990b76176e39
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: rebalance failed due to 'The group member needs to have a valid member id before actually entering a consumer group.' (MemberIdRequiredException)
2026-11-26 06:26:37 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] (Re-)joining group
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Successfully joined group with generation Generation{generationId=7, memberId='fincore-schemahistory-82d8cfa8-c633-48c8-8485-990b76176e39', protocol='range'}
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Finished assignment for group at generation 7: {fincore-schemahistory-82d8cfa8-c633-48c8-8485-990b76176e39=Assignment(partitions=[schema-changes.oracle-0])}
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Successfully synced group in generation Generation{generationId=7, memberId='fincore-schemahistory-82d8cfa8-c633-48c8-8485-990b76176e39', protocol='range'}
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Notifying assignor about the new Assignment(partitions=[schema-changes.oracle-0])
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Adding newly assigned partitions: schema-changes.oracle-0
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Found no committed offset for partition schema-changes.oracle-0
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.SubscriptionState] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting offset for partition schema-changes.oracle-0 to position FetchPosition{offset=0, offsetEpoch=Optional.empty, currentLeader=LeaderAndEpoch{leader=Optional[kafka-0.kafka.backend.svc.cluster.local:9092 (id: 1 rack: null)], epoch=10}}.
2026-11-26 06:26:40 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Database schema history recovery in progress, recovered 1 records
2026-11-26 06:26:40 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Already applied 1 database changes
2026-11-26 06:26:40 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Already applied 176 database changes
2026-11-26 06:26:40 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Database schema history recovery in progress, recovered 177 records
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Revoke previously assigned partitions schema-changes.oracle-0
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Member fincore-schemahistory-82d8cfa8-c633-48c8-8485-990b76176e39 sending LeaveGroup request to coordinator kafka-0.kafka.backend.svc.cluster.local:9092 (id: 2147483646 rack: null) due to the consumer is being closed
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting generation and member id due to: consumer pro-actively leaving the group
2026-11-26 06:26:40 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-11-26 06:26:40 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-11-26 06:26:40 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-11-26 06:26:40 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-11-26 06:26:40 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-11-26 06:26:40 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Finished database schema history recovery of 177 change(s) in 3917 ms
2026-11-26 06:26:40 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."PROCESS_STATUS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-11-26 06:26:40 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."PROCESS_STATUS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-11-26 06:26:40 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Mapper for type '-3' not found.
2026-11-26 06:26:40 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Mapper for type '-3' not found.
2026-11-26 06:26:40 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."MENU_ITEMS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-11-26 06:26:40 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."MENU_ITEMS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-11-26 06:26:40 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = SignalProcessor
2026-11-26 06:26:40 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = change-event-source-coordinator
2026-11-26 06:26:40 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = blocking-snapshot
2026-11-26 06:26:40 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Creating thread debezium-oracleconnector-fincore-change-event-source-coordinator
2026-11-26 06:26:40 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Metrics registered
2026-11-26 06:26:41 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Context created
2026-11-26 06:26:41 INFO  [io.debezium.connector.oracle.OracleSnapshotChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) The previous offset has been found.
2026-11-26 06:26:41 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Snapshot ended with SnapshotResult [status=SKIPPED, offset=OracleOffsetContext [scn=121918308, commit_scn=["121926063:1:0a000600c5900100"]]]
2026-11-26 06:26:41 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Connected metrics set to 'true'
2026-11-26 06:26:41 INFO  [io.debezium.pipeline.signal.SignalProcessor] (debezium-oracleconnector-fincore-change-event-source-coordinator) SignalProcessor started. Scheduling it every 5000ms
2026-11-26 06:26:41 INFO  [io.debezium.util.Threads] (debezium-oracleconnector-fincore-change-event-source-coordinator) Creating thread debezium-oracleconnector-fincore-SignalProcessor
2026-11-26 06:26:41 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Starting streaming
2026-11-26 06:26:41 ERROR [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Mining session stopped due to error.: io.debezium.DebeziumException: Online REDO LOG files or archive log files do not contain the offset scn 121918308.  Please perform a new snapshot.
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:166)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)

2026-11-26 06:26:41 ERROR [io.debezium.pipeline.ErrorHandler] (debezium-oracleconnector-fincore-change-event-source-coordinator) Producer failure: io.debezium.DebeziumException: Online REDO LOG files or archive log files do not contain the offset scn 121918308.  Please perform a new snapshot.
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:166)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)

2026-11-26 06:26:41 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) startScn=121918308, endScn=null
2026-11-26 06:26:41 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Streaming metrics dump: LogMinerStreamingChangeEventSourceMetrics{connectorConfig=io.debezium.connector.oracle.OracleConnectorConfig@3e03dcb0, startTime=2026-11-26T06:26:40.978959Z, clock=SystemClock[Z], currentScn=null, offsetScn=null, commitScn=null, oldestScn=null, oldestScnTime=null, currentLogFileNames=[Ljava.lang.String;@1a2f77e1, redoLogStatuses=[Ljava.lang.String;@36011197, databaseZoneOffset=Z, batchSize=50000, logSwitchCount=0, logMinerQueryCount=0, sleepTime=1000, minimumLogsMined=0, maximumLogsMined=0, maxBatchProcessingThroughput=0, timeDifference=0, processedRowsCount=0, activeTransactionCount=0, rolledBackTransactionCount=0, oversizedTransactionCount=0, changesCount=0, scnFreezeCount=0, batchProcessingDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@4c8c2d99, fetchQueryDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@6cca9ee4, commitDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@d3b6ce3, lagFromSourceDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@3388597a, miningSessionStartupDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@1e454a77, parseTimeDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@26c0dae5, resultSetNextDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@70caf6aa, userGlobalAreaMemory=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$MaxLongValueMetric@1783240, processGlobalAreaMemory=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$MaxLongValueMetric@35dac6ea, abandonedTransactionIds=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$LRUSet@15ed2546, rolledBackTransactionIds=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$LRUSet@32b5fef7} io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics@4ef5f87b
2026-11-26 06:26:41 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Offsets: OracleOffsetContext [scn=121918308, commit_scn=["121926063:1:0a000600c5900100"]]
2026-11-26 06:26:41 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Finished streaming
2026-11-26 06:26:41 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Connected metrics set to 'false'
2026-11-26 06:26:41 INFO  [io.debezium.embedded.EmbeddedEngine] (pool-7-thread-1) Stopping the task and engine
2026-11-26 06:26:41 INFO  [io.debezium.connector.common.BaseSourceTask] (pool-7-thread-1) Stopping down connector
2026-11-26 06:26:41 INFO  [io.debezium.pipeline.signal.SignalProcessor] (pool-7-thread-1) SignalProcessor stopped
2026-11-26 06:26:41 INFO  [io.debezium.service.DefaultServiceRegistry] (pool-7-thread-1) Debezium ServiceRegistry stopped.
2026-11-26 06:26:41 INFO  [io.debezium.jdbc.JdbcConnection] (pool-9-thread-1) Connection gracefully closed
2026-11-26 06:26:41 INFO  [io.debezium.jdbc.JdbcConnection] (pool-10-thread-1) Connection gracefully closed
2026-11-26 06:26:41 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (pool-7-thread-1) [Producer clientId=fincore-schemahistory] Closing the Kafka producer with timeoutMillis = 30000 ms.
2026-11-26 06:26:41 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-11-26 06:26:41 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-11-26 06:26:41 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-11-26 06:26:41 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.producer for fincore-schemahistory unregistered
2026-11-26 06:26:41 INFO  [org.apache.kafka.connect.storage.FileOffsetBackingStore] (pool-7-thread-1) Stopped FileOffsetBackingStore
2026-11-26 06:26:41 ERROR [io.debezium.server.ConnectorLifecycle] (pool-7-thread-1) Connector completed: success = 'false', message = 'Error while trying to run connector class 'io.debezium.connector.oracle.OracleConnector'', error = 'org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.': org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.
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
Caused by: io.debezium.DebeziumException: Online REDO LOG files or archive log files do not contain the offset scn 121918308.  Please perform a new snapshot.
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:166)
        ... 9 more

2026-11-26 06:26:41 INFO  [io.debezium.server.DebeziumServer] (main) Received request to stop the engine
2026-11-26 06:26:41 INFO  [io.debezium.embedded.EmbeddedEngine] (main) Stopping the embedded engine
2026-11-26 06:26:41 INFO  [io.debezium.server.kafka.KafkaChangeConsumer] (main) consumer destroyed...
2026-11-26 06:26:41 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Closing the Kafka producer with timeoutMillis = 5000 ms.
2026-11-26 06:26:41 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics scheduler closed
2026-11-26 06:26:41 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-11-26 06:26:41 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics reporters closed
2026-11-26 06:26:41 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) App info kafka.producer for producer-1 unregistered
2026-11-26 06:26:41 INFO  [io.quarkus] (main) debezium-server-dist stopped in 0.027s
