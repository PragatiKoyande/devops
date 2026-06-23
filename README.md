  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v3.5.4)

2026-06-23 :: 12:56:56.989 || INFO :: StartupInfoLogger.java: | 53 | :: Starting LoginService v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)
2026-06-23 :: 12:56:56.995 || INFO :: SpringApplication.java: | 658 | :: The following 1 profile is active: "uat"
2026-06-23 :: 12:56:58.570 || INFO :: RepositoryConfigurationDelegate.java: | 294 | :: Multiple Spring Data modules found, entering strict repository configuration mode
2026-06-23 :: 12:56:58.573 || INFO :: RepositoryConfigurationDelegate.java: | 145 | :: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-06-23 :: 12:56:58.757 || INFO :: RepositoryConfigurationDelegate.java: | 213 | :: Finished Spring Data repository scanning in 166 ms. Found 8 JPA repository interfaces.
2026-06-23 :: 12:56:58.776 || INFO :: RepositoryConfigurationDelegate.java: | 294 | :: Multiple Spring Data modules found, entering strict repository configuration mode
2026-06-23 :: 12:56:58.779 || INFO :: RepositoryConfigurationDelegate.java: | 145 | :: Bootstrapping Spring Data LDAP repositories in DEFAULT mode.
2026-06-23 :: 12:56:58.789 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.BranchRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-06-23 :: 12:56:58.790 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LaunchConfigRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-06-23 :: 12:56:58.790 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginAttemptRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-06-23 :: 12:56:58.791 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginParamRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-06-23 :: 12:56:58.791 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.MenuItemRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-06-23 :: 12:56:58.791 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RefreshTokenRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-06-23 :: 12:56:58.792 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RolePermissionsRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-06-23 :: 12:56:58.792 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.UserRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-06-23 :: 12:56:58.792 || INFO :: RepositoryConfigurationDelegate.java: | 213 | :: Finished Spring Data repository scanning in 8 ms. Found 0 LDAP repository interfaces.
2026-06-23 :: 12:56:58.813 || INFO :: RepositoryConfigurationDelegate.java: | 294 | :: Multiple Spring Data modules found, entering strict repository configuration mode
2026-06-23 :: 12:56:58.815 || INFO :: RepositoryConfigurationDelegate.java: | 145 | :: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-06-23 :: 12:56:58.833 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.BranchRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-23 :: 12:56:58.834 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LaunchConfigRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-23 :: 12:56:58.834 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginAttemptRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-23 :: 12:56:58.834 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginParamRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-23 :: 12:56:58.834 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.MenuItemRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-23 :: 12:56:58.834 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RefreshTokenRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-23 :: 12:56:58.834 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RolePermissionsRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-23 :: 12:56:58.835 || INFO :: RepositoryConfigurationExtensionSupport.java: | 327 | :: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.UserRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-23 :: 12:56:58.835 || INFO :: RepositoryConfigurationDelegate.java: | 213 | :: Finished Spring Data repository scanning in 4 ms. Found 0 Redis repository interfaces.
2026-06-23 :: 12:57:00.108 || INFO :: TomcatWebServer.java: | 111 | :: Tomcat initialized with port 8085 (http)
2026-06-23 :: 12:57:00.132 || INFO :: DirectJDKLog.java: | 168 | :: Starting service [Tomcat]
2026-06-23 :: 12:57:00.132 || INFO :: DirectJDKLog.java: | 168 | :: Starting Servlet engine: [Apache Tomcat/10.1.43]
2026-06-23 :: 12:57:00.590 || INFO :: HikariDataSource.java: | 109 | :: HikariPool-1 - Starting...
2026-06-23 :: 12:57:01.214 || INFO :: HikariPool.java: | 580 | :: HikariPool-1 - Added connection oracle.jdbc.driver.T4CConnection@31433df9
2026-06-23 :: 12:57:01.216 || INFO :: HikariDataSource.java: | 122 | :: HikariPool-1 - Start completed.
2026-06-23 :: 12:57:01.260 || INFO :: LogHelper.java: | 31 | :: HHH000204: Processing PersistenceUnitInfo [name: default]
2026-06-23 :: 12:57:01.321 || INFO :: Version.java: | 44 | :: HHH000412: Hibernate ORM core version 6.6.22.Final
2026-06-23 :: 12:57:01.360 || INFO :: RegionFactoryInitiator.java: | 50 | :: HHH000026: Second-level cache disabled
2026-06-23 :: 12:57:01.677 || INFO :: SpringPersistenceUnitInfo.java: | 87 | :: No LoadTimeWeaver setup: ignoring JPA class transformer
2026-06-23 :: 12:57:01.904 || WARN :: DialectFactoryImpl.java: | 153 | :: HHH90000025: OracleDialect does not need to be specified explicitly using 'hibernate.dialect' (remove the property setting and it will be selected by default)
2026-06-23 :: 12:57:02.002 || INFO :: JdbcEnvironmentInitiator.java: | 163 | :: HHH10001005: Database info:
        Database JDBC URL [Connecting through datasource 'HikariDataSource (HikariPool-1)']
        Database driver: undefined/unknown
        Database version: 19.28
        Autocommit mode: undefined/unknown
        Isolation level: undefined/unknown
        Minimum pool size: undefined/unknown
        Maximum pool size: undefined/unknown
2026-06-23 :: 12:57:03.122 || INFO :: JtaPlatformInitiator.java: | 59 | :: HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)
2026-06-23 :: 12:57:03.126 || INFO :: AbstractEntityManagerFactoryBean.java: | 447 | :: Initialized JPA EntityManagerFactory for persistence unit 'default'
2026-06-23 :: 12:57:04.264 || INFO :: QueryEnhancerFactory.java: | 49 | :: Hibernate is in classpath; If applicable, HQL parser will be used.
2026-06-23 :: 12:57:04.611 || INFO :: LdapConfig.java: | 52 | :: Configuring LDAP Context Source. URL: ldaps://uatrootdc1.uatad.sbi:3269
2026-06-23 :: 12:57:04.611 || INFO :: LdapConfig.java: | 62 | :: Loading External Truststore from: /etc/fincore/secrets/ad-truststore.jks
2026-06-23 :: 12:57:04.623 || INFO :: LdapConfig.java: | 84 | :: Setting LDAP Bind User (Service Account): fincorecbops@UATAD.SBI
2026-06-23 :: 12:57:05.233 || INFO :: SecurityConfig.java: | 86 | :: Loading SecurityWebFilterChain
2026-06-23 :: 12:57:05.818 || INFO :: EndpointLinksResolver.java: | 60 | :: Exposing 3 endpoints beneath base path '/actuator'
2026-06-23 :: 12:57:06.846 || INFO :: TomcatWebServer.java: | 243 | :: Tomcat started on port 8085 (http)
2026-06-23 :: 12:57:06.863 || INFO :: StartupInfoLogger.java: | 59 | :: Started LoginService in 10.643 seconds (process running for 11.193)
2026-06-23 :: 12:58:05.118 || INFO :: LoginUtility.java: | 11 | :: X-Forwarded-For ip : null
2026-06-23 :: 12:58:05.119 || INFO :: AuthController.java: | 107 | :: Check-User info user id: v1018405 , ip : 10.0.17.242
2026-06-23 :: 12:58:40.334 || INFO :: LoginUtility.java: | 11 | :: X-Forwarded-For ip : null
2026-06-23 :: 12:58:40.334 || INFO :: AuthController.java: | 147 | :: Login request for user: v1018405 from IP: 10.0.17.242
2026-06-23 :: 12:58:40.400 || INFO :: LoginServiceImpl.java: | 388 | :: Password-based login for userId=v1018405
2026-06-23 :: 12:58:40.484 || INFO :: LoginServiceImpl.java: | 635 | :: Credentials validated. Issuing token for userId=v1018405
2026-06-23 :: 12:58:40.654 || INFO :: HmacJwtUtil.java: | 52 | :: Generated exp in Seconds=2026-06-23T13:13:40.654448378Z
2026-06-23 :: 12:58:40.654 || INFO :: HmacJwtUtil.java: | 54 | :: Jti generated=4f4a2585-4ba7-4047-9baa-4f48afcda664
2026-06-23 :: 12:58:40.750 || INFO :: AuthController.java: | 202 | :: Routing user v1018405 to Direct Password Phase.
2026-06-23 :: 12:58:41.180 || INFO :: OtpSessionService.java: | 100 | :: Saved OTP State txId=52f35996-ca2b-4756-bee6-4fc07dda54e8 for user=v1018405 isResend=false
2026-06-23 :: 12:58:41.221 || INFO :: AbstractConfig.java: | 371 | :: ProducerConfig values:
        acks = -1
        auto.include.jmx.reporter = true
        batch.size = 16384
        bootstrap.servers = [kafka.uat-cbops1.svc.cluster.local:9092]
        buffer.memory = 33554432
        client.dns.lookup = use_all_dns_ips
        client.id = CommonUtilities-producer-1
        compression.gzip.level = -1
        compression.lz4.level = 9
        compression.type = none
        compression.zstd.level = 3
        connections.max.idle.ms = 540000
        delivery.timeout.ms = 120000
        enable.idempotence = true
        enable.metrics.push = true
        interceptor.classes = []
        key.serializer = class org.apache.kafka.common.serialization.StringSerializer
        linger.ms = 0
        max.block.ms = 60000
        max.in.flight.requests.per.connection = 5
        max.request.size = 1048576
        metadata.max.age.ms = 300000
        metadata.max.idle.ms = 300000
        metadata.recovery.strategy = none
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
        request.timeout.ms = 5000
        retries = 2147483647
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

2026-06-23 :: 12:58:41.266 || INFO :: KafkaMetricsCollector.java: | 270 | :: initializing Kafka metrics collector
2026-06-23 :: 12:58:41.286 || INFO :: KafkaProducer.java: | 623 | :: [Producer clientId=CommonUtilities-producer-1] Instantiated an idempotent producer.
2026-06-23 :: 12:58:41.339 || INFO :: AppInfoParser.java: | 125 | :: Kafka version: 3.9.1
2026-06-23 :: 12:58:41.339 || INFO :: AppInfoParser.java: | 126 | :: Kafka commitId: f745dfdcee2b9851
2026-06-23 :: 12:58:41.339 || INFO :: AppInfoParser.java: | 127 | :: Kafka startTimeMs: 1782219521337
2026-06-23 :: 12:58:53.368 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 11727 ms.
2026-06-23 :: 12:58:53.371 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 12:59:14.828 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 21353 ms.
2026-06-23 :: 12:59:14.829 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 12:59:39.200 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 24235 ms.
2026-06-23 :: 12:59:39.201 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 12:59:41.353 || ERROR:: LogAccessor.java: | 261 | :: Exception thrown when sending a message with key='52f35996-ca2b-4756-bee6-4fc07dda54e8' and payload='{"payload":"tAJepudnXRKiWeI5:LKFG/ArRwZa/3z7M+0XvUC3h04RV00CWL4p71/ZkM+/K1ZlCadT9x8XwwsvBByx0+UakpvA...' to topic fincore.auth.otp.priority:
org.apache.kafka.common.errors.TimeoutException: Topic fincore.auth.otp.priority not present in metadata after 60000 ms.
2026-06-23 :: 12:59:41.357 || ERROR:: LoginServiceImpl.java: | 141 | :: Infrastructure failure during OTP dispatch for txId=52f35996-ca2b-4756-bee6-4fc07dda54e8. Rolling back Redis state.
org.springframework.kafka.KafkaException: Send failed
        at org.springframework.kafka.core.KafkaTemplate.doSend(KafkaTemplate.java:863)
        at org.springframework.kafka.core.KafkaTemplate.observeSend(KafkaTemplate.java:820)
        at org.springframework.kafka.core.KafkaTemplate.send(KafkaTemplate.java:603)
        at com.fincore.gateway.Service.OtpKafkaProducer.lambda$publishOtpEvent$1(OtpKafkaProducer.java:81)
        at reactor.core.publisher.FluxFlatMap.trySubscribeScalarMap(FluxFlatMap.java:153)
        at reactor.core.publisher.MonoFlatMap.subscribeOrReturn(MonoFlatMap.java:53)
        at reactor.core.publisher.Mono.subscribe(Mono.java:4560)
        at reactor.core.publisher.MonoIgnoreThen$ThenIgnoreMain.subscribeNext(MonoIgnoreThen.java:265)
        at reactor.core.publisher.MonoIgnoreThen$ThenIgnoreMain.onComplete(MonoIgnoreThen.java:204)
        at reactor.core.publisher.MonoPeekTerminal$MonoTerminalPeekSubscriber.onComplete(MonoPeekTerminal.java:299)
        at reactor.core.publisher.MonoWhen$WhenCoordinator.signal(MonoWhen.java:213)
        at reactor.core.publisher.MonoWhen$WhenInner.onComplete(MonoWhen.java:429)
        at reactor.core.publisher.MonoNext$NextSubscriber.onComplete(MonoNext.java:102)
        at reactor.core.publisher.MonoNext$NextSubscriber.onNext(MonoNext.java:83)
        at reactor.core.publisher.FluxUsingWhen$UsingWhenSubscriber.onNext(FluxUsingWhen.java:348)
        at reactor.core.publisher.FluxMap$MapSubscriber.onNext(FluxMap.java:122)
        at reactor.core.publisher.MonoNext$NextSubscriber.onNext(MonoNext.java:82)
        at reactor.core.publisher.FluxOnErrorResume$ResumeSubscriber.onNext(FluxOnErrorResume.java:79)
        at reactor.core.publisher.MonoFlatMapMany$FlatMapManyInner.onNext(MonoFlatMapMany.java:251)
        at reactor.core.publisher.FluxSwitchIfEmpty$SwitchIfEmptySubscriber.onNext(FluxSwitchIfEmpty.java:74)
        at reactor.core.publisher.FluxMap$MapSubscriber.onNext(FluxMap.java:122)
        at reactor.core.publisher.FluxMap$MapSubscriber.onNext(FluxMap.java:122)
        at reactor.core.publisher.MonoNext$NextSubscriber.onNext(MonoNext.java:82)
        at reactor.core.publisher.MonoNext$NextSubscriber.onNext(MonoNext.java:82)
        at io.lettuce.core.RedisPublisher$ImmediateSubscriber.onNext(RedisPublisher.java:895)
        at io.lettuce.core.RedisPublisher$RedisSubscription.onNext(RedisPublisher.java:295)
        at io.lettuce.core.RedisPublisher$SubscriptionCommand.doOnComplete(RedisPublisher.java:782)
        at io.lettuce.core.protocol.CommandWrapper.complete(CommandWrapper.java:69)
        at io.lettuce.core.protocol.CommandWrapper.complete(CommandWrapper.java:67)
        at io.lettuce.core.protocol.CommandHandler.complete(CommandHandler.java:769)
        at io.lettuce.core.protocol.CommandHandler.decode(CommandHandler.java:704)
        at io.lettuce.core.protocol.CommandHandler.channelRead(CommandHandler.java:621)
        at io.netty.channel.AbstractChannelHandlerContext.invokeChannelRead(AbstractChannelHandlerContext.java:442)
        at io.netty.channel.AbstractChannelHandlerContext.invokeChannelRead(AbstractChannelHandlerContext.java:420)
        at io.netty.channel.AbstractChannelHandlerContext.fireChannelRead(AbstractChannelHandlerContext.java:412)
        at io.netty.channel.DefaultChannelPipeline$HeadContext.channelRead(DefaultChannelPipeline.java:1357)
        at io.netty.channel.AbstractChannelHandlerContext.invokeChannelRead(AbstractChannelHandlerContext.java:440)
        at io.netty.channel.AbstractChannelHandlerContext.invokeChannelRead(AbstractChannelHandlerContext.java:420)
        at io.netty.channel.DefaultChannelPipeline.fireChannelRead(DefaultChannelPipeline.java:868)
        at io.netty.channel.epoll.AbstractEpollStreamChannel$EpollStreamUnsafe.epollInReady(AbstractEpollStreamChannel.java:799)
        at io.netty.channel.epoll.EpollEventLoop.processReady(EpollEventLoop.java:501)
        at io.netty.channel.epoll.EpollEventLoop.run(EpollEventLoop.java:399)
        at io.netty.util.concurrent.SingleThreadEventExecutor$4.run(SingleThreadEventExecutor.java:998)
        at io.netty.util.internal.ThreadExecutorMap$2.run(ThreadExecutorMap.java:74)
        at io.netty.util.concurrent.FastThreadLocalRunnable.run(FastThreadLocalRunnable.java:30)
        at java.base/java.lang.Thread.run(Thread.java:1570)
Caused by: org.apache.kafka.common.errors.TimeoutException: Topic fincore.auth.otp.priority not present in metadata after 60000 ms.
2026-06-23 :: 12:59:41.365 || INFO :: OtpSessionService.java: | 202 | :: Successfully rolled back Redis state for txId=52f35996-ca2b-4756-bee6-4fc07dda54e8
2026-06-23 :: 12:59:41.369 || WARN :: GlobalExceptionHandler.java: | 20 | :: Auth Status Error: 500 INTERNAL_SERVER_ERROR - Unable to dispatch OTP due to system latency. Please try again.
2026-06-23 :: 13:00:08.722 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 29280 ms.
2026-06-23 :: 13:00:08.722 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:00:36.587 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 27426 ms.
2026-06-23 :: 13:00:36.587 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:01:05.956 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 28563 ms.
2026-06-23 :: 13:01:05.957 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:01:34.808 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 27766 ms.
2026-06-23 :: 13:01:34.809 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:02:05.828 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 30000 ms.
2026-06-23 :: 13:02:05.829 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:02:36.846 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 30000 ms.
2026-06-23 :: 13:02:36.846 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:03:07.888 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 30000 ms.
2026-06-23 :: 13:03:07.888 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:03:35.394 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 26481 ms.
2026-06-23 :: 13:03:35.395 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:04:02.354 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 25925 ms.
2026-06-23 :: 13:04:02.355 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:04:28.857 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 25430 ms.
2026-06-23 :: 13:04:28.858 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:04:59.901 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 30000 ms.
2026-06-23 :: 13:04:59.901 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:05:27.305 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 26371 ms.
2026-06-23 :: 13:05:27.306 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
2026-06-23 :: 13:05:54.114 || INFO :: NetworkClient.java: | 893 | :: [Producer clientId=CommonUtilities-producer-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 25929 ms.
2026-06-23 :: 13:05:54.115 || WARN :: NetworkClient.java: | 1178 | :: [Producer clientId=CommonUtilities-producer-1] Bootstrap broker kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
