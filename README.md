2026-03-31 07:55:34 [main] INFO  c.t.f.R.ReportbuilderApplication - Starting ReportbuilderApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-31 07:55:35 [main] INFO  c.t.f.R.ReportbuilderApplication - The following 1 profile is active: "dev"
2026-03-31 07:55:41 [main] INFO  o.s.d.r.c.RepositoryConfigurationDelegate - Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-31 07:55:41 [main] INFO  o.s.d.r.c.RepositoryConfigurationDelegate - Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-31 07:55:41 [main] INFO  o.s.d.r.c.RepositoryConfigurationDelegate - Finished Spring Data repository scanning in 96 ms. Found 0 Redis repository interfaces.
2026-03-31 07:55:45 [main] INFO  o.s.b.w.e.tomcat.TomcatWebServer - Tomcat initialized with port 8091 (http)
2026-03-31 07:55:45 [main] INFO  o.a.catalina.core.StandardService - Starting service [Tomcat]
2026-03-31 07:55:45 [main] INFO  o.a.catalina.core.StandardEngine - Starting Servlet engine: [Apache Tomcat/10.1.48]
2026-03-31 07:55:45 [main] INFO  o.a.c.c.C.[Tomcat].[localhost].[/] - Initializing Spring embedded WebApplicationContext
2026-03-31 07:55:45 [main] INFO  o.s.b.w.s.c.ServletWebServerApplicationContext - Root WebApplicationContext: initialization completed in 10214 ms
2026-03-31 07:55:48 [main] INFO  com.zaxxer.hikari.HikariDataSource - HikariPool-1 - Starting...
2026-03-31 07:55:49 [main] INFO  com.zaxxer.hikari.pool.HikariPool - HikariPool-1 - Added connection oracle.jdbc.driver.T4CConnection@4ea48b2e
2026-03-31 07:55:49 [main] INFO  com.zaxxer.hikari.HikariDataSource - HikariPool-1 - Start completed.
2026-03-31 07:55:52 [main] INFO  c.t.f.R.b.m.BatchDataMaterializer - BatchDataMaterializer initialized with 15 parallel threads
2026-03-31 07:55:52 [main] INFO  c.t.f.R.s.a.AggregatorServiceImpl - AggregatorService: safeLimit=50, timeout=1800000ms
2026-03-31 07:55:53 [main] INFO  c.t.f.R.service.export.PdfService - Logo loaded successfully from: classpath:images/sbi-logo.png
2026-03-31 07:55:53 [main] INFO  c.t.f.R.config.HadoopConfig - Initializing HDFS connection to: hdfs://10.177.179.99:8022 as user: root
2026-03-31 07:55:54 [main] WARN  o.a.hadoop.util.NativeCodeLoader - Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
2026-03-31 07:55:56 [main] INFO  c.t.f.R.config.AsyncConfig - Initialized batch report generation executor: core=10, max=60, queue=1000
2026-03-31 07:55:56 [main] INFO  c.t.f.R.b.o.BatchJobOrchestrator - BatchJobOrchestrator initialized. materializationTimeout=240m, generationTimeout=240m
2026-03-31 07:55:58 [main] INFO  c.t.f.R.config.AsyncConfig - Initialized async report executor: core=4, max=50, queue=100
2026-03-31 07:55:58 [main] INFO  c.t.f.R.config.CacheConfig - Redis cache manager initialized with secure type validation. Caches: [reportTemplates, reportVariants]
2026-03-31 07:56:02 [main] INFO  o.s.b.a.e.web.EndpointLinksResolver - Exposing 4 endpoints beneath base path '/actuator'
2026-03-31 07:56:02 [main] INFO  o.s.b.w.e.tomcat.TomcatWebServer - Tomcat started on port 8091 (http) with context path '/'
2026-03-31 07:56:02 [main] INFO  o.a.k.c.consumer.ConsumerConfig - ConsumerConfig values:
        allow.auto.create.topics = true
        auto.commit.interval.ms = 5000
        auto.include.jmx.reporter = true
        auto.offset.reset = earliest
        bootstrap.servers = [kafka-0.kafka.be-test.svc.cluster.local:9092]
        check.crcs = true
        client.dns.lookup = use_all_dns_ips
        client.id = consumer-report-builder-group-1
        client.rack =
        connections.max.idle.ms = 540000
        default.api.timeout.ms = 60000
        enable.auto.commit = false
        enable.metrics.push = true
        exclude.internal.topics = true
        fetch.max.bytes = 52428800
        fetch.max.wait.ms = 500
        fetch.min.bytes = 1
        group.id = report-builder-group
        group.instance.id = null
        group.protocol = classic
        group.remote.assignor = null
        heartbeat.interval.ms = 3000
        interceptor.classes = []
        internal.leave.group.on.close = true
        internal.throw.on.fetch.stable.offset.unsupported = false
        isolation.level = read_uncommitted
        key.deserializer = class org.apache.kafka.common.serialization.StringDeserializer
        max.partition.fetch.bytes = 1048576
        max.poll.interval.ms = 300000
        max.poll.records = 5
        metadata.max.age.ms = 300000
        metadata.recovery.strategy = none
        metric.reporters = []
        metrics.num.samples = 2
        metrics.recording.level = INFO
        metrics.sample.window.ms = 30000
        partition.assignment.strategy = [class org.apache.kafka.clients.consumer.RangeAssignor, class org.apache.kafka.clients.consumer.CooperativeStickyAssignor]
        receive.buffer.bytes = 65536
        reconnect.backoff.max.ms = 1000
        reconnect.backoff.ms = 50
        request.timeout.ms = 30000
        retry.backoff.max.ms = 1000
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
        sasl.oauthbearer.header.urlencode = false
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
        session.timeout.ms = 45000
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
        value.deserializer = class org.springframework.kafka.support.serializer.ErrorHandlingDeserializer

2026-03-31 07:56:03 [main] INFO  o.a.k.c.t.i.KafkaMetricsCollector - initializing Kafka metrics collector
2026-03-31 07:56:03 [main] WARN  o.apache.kafka.clients.ClientUtils - Couldn't resolve server kafka-0.kafka.be-test.svc.cluster.local:9092 from bootstrap.servers as DNS resolution failed for kafka-0.kafka.be-test.svc.cluster.local
2026-03-31 07:56:03 [main] INFO  o.a.kafka.common.metrics.Metrics - Metrics scheduler closed
2026-03-31 07:56:03 [main] INFO  o.a.kafka.common.metrics.Metrics - Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-03-31 07:56:03 [main] INFO  o.a.kafka.common.metrics.Metrics - Closing reporter org.apache.kafka.common.telemetry.internals.ClientTelemetryReporter
2026-03-31 07:56:03 [main] INFO  o.a.kafka.common.metrics.Metrics - Metrics reporters closed
2026-03-31 07:56:03 [main] INFO  o.a.kafka.common.utils.AppInfoParser - App info kafka.consumer for consumer-report-builder-group-1 unregistered
2026-03-31 07:56:03 [main] INFO  o.s.b.w.e.tomcat.GracefulShutdown - Commencing graceful shutdown. Waiting for active requests to complete
2026-03-31 07:56:03 [tomcat-shutdown] INFO  o.s.b.w.e.tomcat.GracefulShutdown - Graceful shutdown complete
2026-03-31 07:56:03 [main] WARN  o.s.b.w.s.c.AnnotationConfigServletWebServerApplicationContext - Exception encountered during context initialization - cancelling refresh attempt: org.springframework.context.ApplicationContextException: Failed to start bean 'org.springframework.kafka.config.internalKafkaListenerEndpointRegistry'
2026-03-31 07:56:03 [main] INFO  c.t.f.R.s.a.AggregatorServiceImpl - Shutting down AggregatorService executor...
2026-03-31 07:56:03 [main] INFO  c.t.f.R.b.m.BatchDataMaterializer - Shutting down materializationExecutor...
2026-03-31 07:56:03 [main] INFO  com.zaxxer.hikari.HikariDataSource - HikariPool-1 - Shutdown initiated...
2026-03-31 07:56:03 [main] INFO  com.zaxxer.hikari.HikariDataSource - HikariPool-1 - Shutdown completed.
2026-03-31 07:56:03 [main] INFO  o.s.b.a.l.ConditionEvaluationReportLogger -

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-31 07:56:03 [main] ERROR o.s.boot.SpringApplication - Application run failed
org.springframework.context.ApplicationContextException: Failed to start bean 'org.springframework.kafka.config.internalKafkaListenerEndpointRegistry'
        at org.springframework.context.support.DefaultLifecycleProcessor.doStart(DefaultLifecycleProcessor.java:408)
        at org.springframework.context.support.DefaultLifecycleProcessor.doStart(DefaultLifecycleProcessor.java:394)
        at org.springframework.context.support.DefaultLifecycleProcessor$LifecycleGroup.start(DefaultLifecycleProcessor.java:586)
        at java.base/java.lang.Iterable.forEach(Iterable.java:75)
        at org.springframework.context.support.DefaultLifecycleProcessor.startBeans(DefaultLifecycleProcessor.java:364)
        at org.springframework.context.support.DefaultLifecycleProcessor.onRefresh(DefaultLifecycleProcessor.java:310)
        at org.springframework.context.support.AbstractApplicationContext.finishRefresh(AbstractApplicationContext.java:1009)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:630)
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:752)
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:439)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:318)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1361)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1350)
        at com.tcs.fincore.ReportBuilder.ReportbuilderApplication.main(ReportbuilderApplication.java:9)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:106)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
Caused by: org.apache.kafka.common.KafkaException: Failed to construct kafka consumer
        at org.apache.kafka.clients.consumer.internals.ClassicKafkaConsumer.<init>(ClassicKafkaConsumer.java:270)
        at org.apache.kafka.clients.consumer.internals.ConsumerDelegateCreator.create(ConsumerDelegateCreator.java:65)
        at org.apache.kafka.clients.consumer.KafkaConsumer.<init>(KafkaConsumer.java:600)
        at org.apache.kafka.clients.consumer.KafkaConsumer.<init>(KafkaConsumer.java:595)
        at org.springframework.kafka.core.DefaultKafkaConsumerFactory$ExtendedKafkaConsumer.<init>(DefaultKafkaConsumerFactory.java:498)
        at org.springframework.kafka.core.DefaultKafkaConsumerFactory.createRawConsumer(DefaultKafkaConsumerFactory.java:453)
        at org.springframework.kafka.core.DefaultKafkaConsumerFactory.createKafkaConsumer(DefaultKafkaConsumerFactory.java:430)
        at org.springframework.kafka.core.DefaultKafkaConsumerFactory.createConsumerWithAdjustedProperties(DefaultKafkaConsumerFactory.java:407)
        at org.springframework.kafka.core.DefaultKafkaConsumerFactory.createKafkaConsumer(DefaultKafkaConsumerFactory.java:374)
        at org.springframework.kafka.core.DefaultKafkaConsumerFactory.createConsumer(DefaultKafkaConsumerFactory.java:335)
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.<init>(KafkaMessageListenerContainer.java:877)
        at org.springframework.kafka.listener.KafkaMessageListenerContainer.doStart(KafkaMessageListenerContainer.java:388)
        at org.springframework.kafka.listener.AbstractMessageListenerContainer.start(AbstractMessageListenerContainer.java:520)
        at org.springframework.kafka.listener.ConcurrentMessageListenerContainer.doStart(ConcurrentMessageListenerContainer.java:264)
        at org.springframework.kafka.listener.AbstractMessageListenerContainer.start(AbstractMessageListenerContainer.java:520)
        at org.springframework.kafka.config.KafkaListenerEndpointRegistry.startIfNecessary(KafkaListenerEndpointRegistry.java:436)
        at org.springframework.kafka.config.KafkaListenerEndpointRegistry.start(KafkaListenerEndpointRegistry.java:382)
        at org.springframework.context.support.DefaultLifecycleProcessor.doStart(DefaultLifecycleProcessor.java:405)
        ... 19 common frames omitted
Caused by: org.apache.kafka.common.config.ConfigException: No resolvable bootstrap urls given in bootstrap.servers
        at org.apache.kafka.clients.ClientUtils.parseAndValidateAddresses(ClientUtils.java:104)
        at org.apache.kafka.clients.ClientUtils.parseAndValidateAddresses(ClientUtils.java:63)
        at org.apache.kafka.clients.ClientUtils.parseAndValidateAddresses(ClientUtils.java:59)
        at org.apache.kafka.clients.consumer.internals.ClassicKafkaConsumer.<init>(ClassicKafkaConsumer.java:189)
        ... 36 common frames omitted



        this is the issue 
