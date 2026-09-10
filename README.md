2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka version: 3.6.1
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka commitId: 5e3c2b738d253ff5
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka startTimeMs: 1789033409919
2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.Metadata] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting generation and member id due to: consumer pro-actively leaving the group
2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-09-10 09:43:29 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Started database schema history recovery
2026-09-10 09:43:29 INFO  [io.debezium.storage.kafka.history.KafkaSchemaHistory] (debezium-oracleconnector-fincore-db-history-config-check) Database schema history topic 'schema-changes.oracle.fresh' has correct settings
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (kafka-admin-client-thread | fincore-schemahistory-topic-check) App info kafka.admin.client for fincore-schemahistory-topic-check unregistered
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics scheduler closed
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics reporters closed
2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.admin.AdminClientConfig] (debezium-oracleconnector-fincore-db-history-config-check) AdminClientConfig values:
        auto.include.jmx.reporter = true
        bootstrap.servers = [kafka.uat-cbops1.svc.cluster.local:9092]
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

2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.admin.AdminClientConfig] (debezium-oracleconnector-fincore-db-history-config-check) These configurations '[value.serializer, acks, batch.size, max.block.ms, buffer.memory, key.serializer, linger.ms]' were supplied but are not used yet.
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka version: 3.6.1
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka commitId: 5e3c2b738d253ff5
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (debezium-oracleconnector-fincore-db-history-config-check) Kafka startTimeMs: 1789033409937
2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.consumer.ConsumerConfig] (pool-7-thread-1) ConsumerConfig values:
        allow.auto.create.topics = true
        auto.commit.interval.ms = 5000
        auto.include.jmx.reporter = true
        auto.offset.reset = earliest
        bootstrap.servers = [kafka.uat-cbops1.svc.cluster.local:9092]
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

2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka version: 3.6.1
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka commitId: 5e3c2b738d253ff5
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) Kafka startTimeMs: 1789033409941
2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.consumer.KafkaConsumer] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Subscribed to topic(s): schema-changes.oracle.fresh
2026-09-10 09:43:29 INFO  [io.debezium.storage.kafka.history.KafkaSchemaHistory] (debezium-oracleconnector-fincore-db-history-config-check) Database schema history topic 'schema-changes.oracle.fresh' has correct settings
2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.Metadata] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Cluster ID: jgQjUybBSACbAFjwpKFQiA
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.utils.AppInfoParser] (kafka-admin-client-thread | fincore-schemahistory-topic-check) App info kafka.admin.client for fincore-schemahistory-topic-check unregistered
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics scheduler closed
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-09-10 09:43:29 INFO  [org.apache.kafka.common.metrics.Metrics] (kafka-admin-client-thread | fincore-schemahistory-topic-check) Metrics reporters closed
2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Discovered group coordinator kafka.uat-cbops1.svc.cluster.local:9092 (id: 2147483646 rack: null)
2026-09-10 09:43:29 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] (Re-)joining group
2026-09-10 09:43:30 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: need to re-join with the given member-id: fincore-schemahistory-44b2ad72-2667-45d8-b200-bb2dac040950
2026-09-10 09:43:30 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: rebalance failed due to 'The group member needs to have a valid member id before actually entering a consumer group.' (MemberIdRequiredException)
2026-09-10 09:43:30 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] (Re-)joining group
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Successfully joined group with generation Generation{generationId=3, memberId='fincore-schemahistory-44b2ad72-2667-45d8-b200-bb2dac040950', protocol='range'}
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Finished assignment for group at generation 3: {fincore-schemahistory-44b2ad72-2667-45d8-b200-bb2dac040950=Assignment(partitions=[schema-changes.oracle.fresh-0])}
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Successfully synced group in generation Generation{generationId=3, memberId='fincore-schemahistory-44b2ad72-2667-45d8-b200-bb2dac040950', protocol='range'}
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Notifying assignor about the new Assignment(partitions=[schema-changes.oracle.fresh-0])
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Adding newly assigned partitions: schema-changes.oracle.fresh-0
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Found no committed offset for partition schema-changes.oracle.fresh-0
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.SubscriptionState] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting offset for partition schema-changes.oracle.fresh-0 to position FetchPosition{offset=0, offsetEpoch=Optional.empty, currentLeader=LeaderAndEpoch{leader=Optional[kafka.uat-cbops1.svc.cluster.local:9092 (id: 1 rack: null)], epoch=8}}.
2026-09-10 09:43:33 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Database schema history recovery in progress, recovered 1 records
2026-09-10 09:43:33 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Already applied 1 database changes
2026-09-10 09:43:33 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Already applied 126 database changes
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Revoke previously assigned partitions schema-changes.oracle.fresh-0
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Member fincore-schemahistory-44b2ad72-2667-45d8-b200-bb2dac040950 sending LeaveGroup request to coordinator kafka.uat-cbops1.svc.cluster.local:9092 (id: 2147483646 rack: null) due to the consumer is being closed
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Resetting generation and member id due to: consumer pro-actively leaving the group
2026-09-10 09:43:33 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-09-10 09:43:33 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-09-10 09:43:33 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-09-10 09:43:33 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-09-10 09:43:33 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-09-10 09:43:33 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Finished database schema history recovery of 126 change(s) in 3756 ms
2026-09-10 09:43:33 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."PROCESS_STATUS_SEQ"."NEXTVAL" ' to type '2'.  Expression evaluation is not supported.
2026-09-10 09:43:33 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."PROCESS_STATUS_SEQ"."NEXTVAL" ' to type '2'.  Expression evaluation is not supported.
2026-09-10 09:43:33 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Mapper for type '-3' not found.
2026-09-10 09:43:33 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Mapper for type '-3' not found.
2026-09-10 09:43:33 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."MENU_ITEMS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-09-10 09:43:33 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."MENU_ITEMS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-09-10 09:43:33 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = SignalProcessor
2026-09-10 09:43:33 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = change-event-source-coordinator
2026-09-10 09:43:33 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = blocking-snapshot
2026-09-10 09:43:33 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Creating thread debezium-oracleconnector-fincore-change-event-source-coordinator
2026-09-10 09:43:33 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Metrics registered
2026-09-10 09:43:33 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Context created
2026-09-10 09:43:33 INFO  [io.debezium.connector.oracle.OracleSnapshotChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) The previous offset has been found.
2026-09-10 09:43:33 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Snapshot ended with SnapshotResult [status=SKIPPED, offset=OracleOffsetContext [scn=190472583, commit_scn=["160183892:0:05001700614f0000","190472588:1:0a000900e5090300"]]]
2026-09-10 09:43:33 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Connected metrics set to 'true'
2026-09-10 09:43:33 INFO  [io.debezium.pipeline.signal.SignalProcessor] (debezium-oracleconnector-fincore-change-event-source-coordinator) SignalProcessor started. Scheduling it every 5000ms
2026-09-10 09:43:33 INFO  [io.debezium.util.Threads] (debezium-oracleconnector-fincore-change-event-source-coordinator) Creating thread debezium-oracleconnector-fincore-SignalProcessor
2026-09-10 09:43:33 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Starting streaming
2026-09-10 09:43:33 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Redo Log Group Sizes:
2026-09-10 09:43:33 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator)         Group #1: 209715200 bytes
2026-09-10 09:43:33 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator)         Group #2: 209715200 bytes
2026-09-10 09:43:33 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator)         Group #3: 209715200 bytes
2026-09-10 09:43:34 ERROR [io.debezium.connector.oracle.logminer.LogMinerDatabaseStateWriter] (debezium-oracleconnector-fincore-change-event-source-coordinator) Failed to start a LogMiner mining session with parameters:
2026-09-10 09:43:34 ERROR [io.debezium.connector.oracle.logminer.LogMinerDatabaseStateWriter] (debezium-oracleconnector-fincore-change-event-source-coordinator)        SCN: [0-0], Required Start SCN: 0, Options: 2064, Status: 0 - N/A
2026-09-10 09:43:34 ERROR [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Got exception when starting mining session.: java.sql.SQLException: ORA-16331: container "FINCOREGGPDB2" is not open
ORA-06512: at "SYS.DBMS_LOGMNR", line 72
ORA-06512: at line 1

        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:630)
        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:564)
        at oracle.jdbc.driver.T4C8Oall.processError(T4C8Oall.java:1231)
        at oracle.jdbc.driver.T4CTTIfun.receive(T4CTTIfun.java:772)
        at oracle.jdbc.driver.T4CTTIfun.doRPC(T4CTTIfun.java:299)
        at oracle.jdbc.driver.T4C8Oall.doOALL(T4C8Oall.java:512)
        at oracle.jdbc.driver.T4CStatement.doOall8(T4CStatement.java:123)
        at oracle.jdbc.driver.T4CStatement.executeForRows(T4CStatement.java:1200)
        at oracle.jdbc.driver.OracleStatement.executeSQLStatement(OracleStatement.java:1820)
        at oracle.jdbc.driver.OracleStatement.doExecuteWithTimeout(OracleStatement.java:1472)
        at oracle.jdbc.driver.OracleStatement.executeInternal(OracleStatement.java:2505)
        at oracle.jdbc.driver.OracleStatement.execute(OracleStatement.java:2460)
        at oracle.jdbc.driver.OracleStatementWrapper.execute(OracleStatementWrapper.java:328)
        at io.debezium.jdbc.JdbcConnection.executeWithoutCommitting(JdbcConnection.java:1451)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.startMiningSession(LogMinerStreamingChangeEventSource.java:637)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:243)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)
Caused by: Error : 16331, Position : 0, Sql = BEGIN sys.dbms_logmnr.start_logmnr(startScn => '190472584', endScn => '190522583', OPTIONS => DBMS_LOGMNR.DICT_FROM_ONLINE_CATALOG  + DBMS_LOGMNR.NO_ROWID_IN_STMT);END;, OriginalSql = BEGIN sys.dbms_logmnr.start_logmnr(startScn => '190472584', endScn => '190522583', OPTIONS => DBMS_LOGMNR.DICT_FROM_ONLINE_CATALOG  + DBMS_LOGMNR.NO_ROWID_IN_STMT);END;, Error Msg = ORA-16331: container "FINCOREGGPDB2" is not open
ORA-06512: at "SYS.DBMS_LOGMNR", line 72
ORA-06512: at line 1

        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:637)
        ... 24 more

2026-09-10 09:43:34 ERROR [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Mining session stopped due to error.: java.sql.SQLException: ORA-16331: container "FINCOREGGPDB2" is not open
ORA-06512: at "SYS.DBMS_LOGMNR", line 72
ORA-06512: at line 1

        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:630)
        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:564)
        at oracle.jdbc.driver.T4C8Oall.processError(T4C8Oall.java:1231)
        at oracle.jdbc.driver.T4CTTIfun.receive(T4CTTIfun.java:772)
        at oracle.jdbc.driver.T4CTTIfun.doRPC(T4CTTIfun.java:299)
        at oracle.jdbc.driver.T4C8Oall.doOALL(T4C8Oall.java:512)
        at oracle.jdbc.driver.T4CStatement.doOall8(T4CStatement.java:123)
        at oracle.jdbc.driver.T4CStatement.executeForRows(T4CStatement.java:1200)
        at oracle.jdbc.driver.OracleStatement.executeSQLStatement(OracleStatement.java:1820)
        at oracle.jdbc.driver.OracleStatement.doExecuteWithTimeout(OracleStatement.java:1472)
        at oracle.jdbc.driver.OracleStatement.executeInternal(OracleStatement.java:2505)
        at oracle.jdbc.driver.OracleStatement.execute(OracleStatement.java:2460)
        at oracle.jdbc.driver.OracleStatementWrapper.execute(OracleStatementWrapper.java:328)
        at io.debezium.jdbc.JdbcConnection.executeWithoutCommitting(JdbcConnection.java:1451)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.startMiningSession(LogMinerStreamingChangeEventSource.java:637)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:243)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)
Caused by: Error : 16331, Position : 0, Sql = BEGIN sys.dbms_logmnr.start_logmnr(startScn => '190472584', endScn => '190522583', OPTIONS => DBMS_LOGMNR.DICT_FROM_ONLINE_CATALOG  + DBMS_LOGMNR.NO_ROWID_IN_STMT);END;, OriginalSql = BEGIN sys.dbms_logmnr.start_logmnr(startScn => '190472584', endScn => '190522583', OPTIONS => DBMS_LOGMNR.DICT_FROM_ONLINE_CATALOG  + DBMS_LOGMNR.NO_ROWID_IN_STMT);END;, Error Msg = ORA-16331: container "FINCOREGGPDB2" is not open
ORA-06512: at "SYS.DBMS_LOGMNR", line 72
ORA-06512: at line 1

        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:637)
        ... 24 more

2026-09-10 09:43:34 ERROR [io.debezium.pipeline.ErrorHandler] (debezium-oracleconnector-fincore-change-event-source-coordinator) Producer failure: java.sql.SQLException: ORA-16331: container "FINCOREGGPDB2" is not open
ORA-06512: at "SYS.DBMS_LOGMNR", line 72
ORA-06512: at line 1

        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:630)
        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:564)
        at oracle.jdbc.driver.T4C8Oall.processError(T4C8Oall.java:1231)
        at oracle.jdbc.driver.T4CTTIfun.receive(T4CTTIfun.java:772)
        at oracle.jdbc.driver.T4CTTIfun.doRPC(T4CTTIfun.java:299)
        at oracle.jdbc.driver.T4C8Oall.doOALL(T4C8Oall.java:512)
        at oracle.jdbc.driver.T4CStatement.doOall8(T4CStatement.java:123)
        at oracle.jdbc.driver.T4CStatement.executeForRows(T4CStatement.java:1200)
        at oracle.jdbc.driver.OracleStatement.executeSQLStatement(OracleStatement.java:1820)
        at oracle.jdbc.driver.OracleStatement.doExecuteWithTimeout(OracleStatement.java:1472)
        at oracle.jdbc.driver.OracleStatement.executeInternal(OracleStatement.java:2505)
        at oracle.jdbc.driver.OracleStatement.execute(OracleStatement.java:2460)
        at oracle.jdbc.driver.OracleStatementWrapper.execute(OracleStatementWrapper.java:328)
        at io.debezium.jdbc.JdbcConnection.executeWithoutCommitting(JdbcConnection.java:1451)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.startMiningSession(LogMinerStreamingChangeEventSource.java:637)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:243)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)
Caused by: Error : 16331, Position : 0, Sql = BEGIN sys.dbms_logmnr.start_logmnr(startScn => '190472584', endScn => '190522583', OPTIONS => DBMS_LOGMNR.DICT_FROM_ONLINE_CATALOG  + DBMS_LOGMNR.NO_ROWID_IN_STMT);END;, OriginalSql = BEGIN sys.dbms_logmnr.start_logmnr(startScn => '190472584', endScn => '190522583', OPTIONS => DBMS_LOGMNR.DICT_FROM_ONLINE_CATALOG  + DBMS_LOGMNR.NO_ROWID_IN_STMT);END;, Error Msg = ORA-16331: container "FINCOREGGPDB2" is not open
ORA-06512: at "SYS.DBMS_LOGMNR", line 72
ORA-06512: at line 1

        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:637)
        ... 24 more

2026-09-10 09:43:34 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) startScn=190472583, endScn=190522583
2026-09-10 09:43:34 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Streaming metrics dump: LogMinerStreamingChangeEventSourceMetrics{connectorConfig=io.debezium.connector.oracle.OracleConnectorConfig@47f1c712, startTime=2026-09-10T09:43:33.721997Z, clock=SystemClock[Z], currentScn=190892425, offsetScn=null, commitScn=null, oldestScn=null, oldestScnTime=null, currentLogFileNames=[Ljava.lang.String;@583521f6, redoLogStatuses=[Ljava.lang.String;@1473abb6, databaseZoneOffset=+05:30, batchSize=51000, logSwitchCount=0, logMinerQueryCount=0, sleepTime=800, minimumLogsMined=1, maximumLogsMined=1, maxBatchProcessingThroughput=0, timeDifference=-27506, processedRowsCount=0, activeTransactionCount=0, rolledBackTransactionCount=0, oversizedTransactionCount=0, changesCount=0, scnFreezeCount=0, batchProcessingDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@53066866, fetchQueryDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@1a86ec43, commitDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@6b4d5474, lagFromSourceDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@626a6cb0, miningSessionStartupDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@2cf7dc3, parseTimeDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@2f867d2d, resultSetNextDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@2e69625d, userGlobalAreaMemory=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$MaxLongValueMetric@1f5784cc, processGlobalAreaMemory=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$MaxLongValueMetric@668fc380, abandonedTransactionIds=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$LRUSet@7afca569, rolledBackTransactionIds=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$LRUSet@1fe24be1} io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics@b5f2dff
2026-09-10 09:43:34 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Offsets: OracleOffsetContext [scn=190472583, commit_scn=["160183892:0:05001700614f0000","190472588:1:0a000900e5090300"]]
2026-09-10 09:43:34 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Finished streaming
2026-09-10 09:43:34 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Connected metrics set to 'false'
2026-09-10 09:43:34 INFO  [io.debezium.embedded.EmbeddedEngine] (pool-7-thread-1) Stopping the task and engine
2026-09-10 09:43:34 INFO  [io.debezium.connector.common.BaseSourceTask] (pool-7-thread-1) Stopping down connector
2026-09-10 09:43:34 INFO  [io.debezium.pipeline.signal.SignalProcessor] (pool-7-thread-1) SignalProcessor stopped
2026-09-10 09:43:34 INFO  [io.debezium.service.DefaultServiceRegistry] (pool-7-thread-1) Debezium ServiceRegistry stopped.
2026-09-10 09:43:34 INFO  [io.debezium.jdbc.JdbcConnection] (pool-9-thread-1) Connection gracefully closed
2026-09-10 09:43:34 INFO  [io.debezium.jdbc.JdbcConnection] (pool-10-thread-1) Connection gracefully closed
2026-09-10 09:43:34 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (pool-7-thread-1) [Producer clientId=fincore-schemahistory] Closing the Kafka producer with timeoutMillis = 30000 ms.
2026-09-10 09:43:34 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-09-10 09:43:34 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-09-10 09:43:34 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-09-10 09:43:34 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.producer for fincore-schemahistory unregistered
2026-09-10 09:43:34 INFO  [org.apache.kafka.connect.storage.FileOffsetBackingStore] (pool-7-thread-1) Stopped FileOffsetBackingStore
2026-09-10 09:43:34 ERROR [io.debezium.server.ConnectorLifecycle] (pool-7-thread-1) Connector completed: success = 'false', message = 'Error while trying to run connector class 'io.debezium.connector.oracle.OracleConnector'', error = 'org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.': org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.
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
Caused by: java.sql.SQLException: ORA-16331: container "FINCOREGGPDB2" is not open
ORA-06512: at "SYS.DBMS_LOGMNR", line 72
ORA-06512: at line 1

        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:630)
        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:564)
        at oracle.jdbc.driver.T4C8Oall.processError(T4C8Oall.java:1231)
        at oracle.jdbc.driver.T4CTTIfun.receive(T4CTTIfun.java:772)
        at oracle.jdbc.driver.T4CTTIfun.doRPC(T4CTTIfun.java:299)
        at oracle.jdbc.driver.T4C8Oall.doOALL(T4C8Oall.java:512)
        at oracle.jdbc.driver.T4CStatement.doOall8(T4CStatement.java:123)
        at oracle.jdbc.driver.T4CStatement.executeForRows(T4CStatement.java:1200)
        at oracle.jdbc.driver.OracleStatement.executeSQLStatement(OracleStatement.java:1820)
        at oracle.jdbc.driver.OracleStatement.doExecuteWithTimeout(OracleStatement.java:1472)
        at oracle.jdbc.driver.OracleStatement.executeInternal(OracleStatement.java:2505)
        at oracle.jdbc.driver.OracleStatement.execute(OracleStatement.java:2460)
        at oracle.jdbc.driver.OracleStatementWrapper.execute(OracleStatementWrapper.java:328)
        at io.debezium.jdbc.JdbcConnection.executeWithoutCommitting(JdbcConnection.java:1451)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.startMiningSession(LogMinerStreamingChangeEventSource.java:637)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:243)
        ... 9 more
Caused by: Error : 16331, Position : 0, Sql = BEGIN sys.dbms_logmnr.start_logmnr(startScn => '190472584', endScn => '190522583', OPTIONS => DBMS_LOGMNR.DICT_FROM_ONLINE_CATALOG  + DBMS_LOGMNR.NO_ROWID_IN_STMT);END;, OriginalSql = BEGIN sys.dbms_logmnr.start_logmnr(startScn => '190472584', endScn => '190522583', OPTIONS => DBMS_LOGMNR.DICT_FROM_ONLINE_CATALOG  + DBMS_LOGMNR.NO_ROWID_IN_STMT);END;, Error Msg = ORA-16331: container "FINCOREGGPDB2" is not open
ORA-06512: at "SYS.DBMS_LOGMNR", line 72
ORA-06512: at line 1

        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:637)
        ... 24 more

2026-09-10 09:43:34 INFO  [io.debezium.server.DebeziumServer] (main) Received request to stop the engine
2026-09-10 09:43:34 INFO  [io.debezium.embedded.EmbeddedEngine] (main) Stopping the embedded engine
2026-09-10 09:43:34 INFO  [io.debezium.server.kafka.KafkaChangeConsumer] (main) consumer destroyed...
2026-09-10 09:43:34 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Closing the Kafka producer with timeoutMillis = 5000 ms.
2026-09-10 09:43:34 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics scheduler closed
2026-09-10 09:43:34 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-09-10 09:43:34 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics reporters closed
2026-09-10 09:43:34 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) App info kafka.producer for producer-1 unregistered
2026-09-10 09:43:34 INFO  [io.quarkus] (main) debezium-server-dist stopped in 0.026s
