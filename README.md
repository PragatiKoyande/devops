[root@fcppjump PRE-PROD-Microservices]# k logs debezium-server-86c8fbbbcb-g2bch -f  -n backend --kubeconfig h06vkspreprodcbopscls-kubeconfig.yaml
       __       __                 _
  ____/ /___   / /_   ___  ____   (_)__  __ ____ ___
 / __  // _ \ / __ \ / _ \/_  /  / // / / // __ `__ \
/ /_/ //  __// /_/ //  __/ / /_ / // /_/ // / / / / /
\__,_/ \___//_.___/ \___/ /___//_/ \__,_//_/ /_/ /_/



                      Powered by Quarkus 3.2.10.Final
2026-07-08 06:08:14 INFO  [io.debezium.server.BaseChangeConsumer] (main) Using 'io.debezium.server.BaseChangeConsumer$$Lambda$232/0x000000084030bc40@69391e08' stream name mapper
2026-07-08 06:08:14 INFO  [org.apache.kafka.clients.producer.ProducerConfig] (main) ProducerConfig values:
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

2026-07-08 06:08:14 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Instantiated an idempotent producer.
2026-07-08 06:08:34 WARN  [org.apache.kafka.clients.ClientUtils] (main) Couldn't resolve server kafka.backend.svc.cluster.local:9092 from bootstrap.servers as DNS resolution failed for kafka.backend.svc.cluster.local
2026-07-08 06:08:34 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Closing the Kafka producer with timeoutMillis = 0 ms.
2026-07-08 06:08:34 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics scheduler closed
2026-07-08 06:08:34 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-07-08 06:08:34 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics reporters closed
2026-07-08 06:08:34 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) App info kafka.producer for producer-1 unregistered
2026-07-08 06:08:34 ERROR [io.quarkus.runtime.Application] (main) Failed to start application (with profile [prod]): java.lang.RuntimeException: Failed to start quarkus
        at io.quarkus.runner.ApplicationImpl.doStart(Unknown Source)
        at io.quarkus.runtime.Application.start(Application.java:101)
        at io.quarkus.runtime.ApplicationLifecycleManager.run(ApplicationLifecycleManager.java:111)
        at io.quarkus.runtime.Quarkus.run(Quarkus.java:71)
        at io.quarkus.runtime.Quarkus.run(Quarkus.java:44)
        at io.quarkus.runtime.Quarkus.run(Quarkus.java:124)
        at io.debezium.server.Main.main(Main.java:15)
Caused by: org.apache.kafka.common.KafkaException: Failed to construct kafka producer
        at org.apache.kafka.clients.producer.KafkaProducer.<init>(KafkaProducer.java:459)
        at org.apache.kafka.clients.producer.KafkaProducer.<init>(KafkaProducer.java:287)
        at org.apache.kafka.clients.producer.KafkaProducer.<init>(KafkaProducer.java:270)
        at io.debezium.server.kafka.KafkaChangeConsumer.start(KafkaChangeConsumer.java:63)
        at io.debezium.server.kafka.KafkaChangeConsumer_Bean.doCreate(Unknown Source)
        at io.debezium.server.kafka.KafkaChangeConsumer_Bean.create(Unknown Source)
        at io.debezium.server.kafka.KafkaChangeConsumer_Bean.create(Unknown Source)
        at io.debezium.server.DebeziumServer.start(DebeziumServer.java:129)
        at io.debezium.server.DebeziumServer_Bean.doCreate(Unknown Source)
        at io.debezium.server.DebeziumServer_Bean.create(Unknown Source)
        at io.debezium.server.DebeziumServer_Bean.create(Unknown Source)
        at io.quarkus.arc.impl.AbstractSharedContext.createInstanceHandle(AbstractSharedContext.java:113)
        at io.quarkus.arc.impl.AbstractSharedContext$1.get(AbstractSharedContext.java:37)
        at io.quarkus.arc.impl.AbstractSharedContext$1.get(AbstractSharedContext.java:34)
        at io.quarkus.arc.impl.LazyValue.get(LazyValue.java:26)
        at io.quarkus.arc.impl.ComputingCache.computeIfAbsent(ComputingCache.java:69)
        at io.quarkus.arc.impl.AbstractSharedContext.get(AbstractSharedContext.java:34)
        at io.quarkus.arc.impl.ClientProxies.getApplicationScopedDelegate(ClientProxies.java:21)
        at io.debezium.server.DebeziumServer_ClientProxy.arc$delegate(Unknown Source)
        at io.debezium.server.DebeziumServer_ClientProxy.arc_contextualInstance(Unknown Source)
        at io.debezium.server.DebeziumServer_Observer_Synthetic_f28a48f6bdce4326db44aec92fdb5c84d535b5d9.notify(Unknown Source)
        at io.quarkus.arc.impl.EventImpl$Notifier.notifyObservers(EventImpl.java:346)
        at io.quarkus.arc.impl.EventImpl$Notifier.notify(EventImpl.java:328)
        at io.quarkus.arc.impl.EventImpl.fire(EventImpl.java:82)
        at io.quarkus.arc.runtime.ArcRecorder.fireLifecycleEvent(ArcRecorder.java:155)
        at io.quarkus.arc.runtime.ArcRecorder.handleLifecycleEvents(ArcRecorder.java:106)
        at io.quarkus.deployment.steps.LifecycleEventsBuildStep$startupEvent1144526294.deploy_0(Unknown Source)
        at io.quarkus.deployment.steps.LifecycleEventsBuildStep$startupEvent1144526294.deploy(Unknown Source)
        ... 7 more
Caused by: org.apache.kafka.common.config.ConfigException: No resolvable bootstrap urls given in bootstrap.servers
        at org.apache.kafka.clients.ClientUtils.parseAndValidateAddresses(ClientUtils.java:101)
        at org.apache.kafka.clients.ClientUtils.parseAndValidateAddresses(ClientUtils.java:60)
        at org.apache.kafka.clients.ClientUtils.parseAndValidateAddresses(ClientUtils.java:56)
        at org.apache.kafka.clients.producer.KafkaProducer.<init>(KafkaProducer.java:435)
        ... 34 more
