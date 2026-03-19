[root@fcprodkubjump Microservices]# k logs login-deployment-7dd865ddd8-pn6vl -n backend
Picked up JAVA_TOOL_OPTIONS: -Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v3.5.4)

2026-03-19 11:38:25.717 INFO  [main] o.s.b.StartupInfoLogger: Starting LoginService v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-19 11:38:25.722 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "dev"
2026-03-19 11:38:29.920 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-19 11:38:29.921 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-19 11:38:30.501 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 493 ms. Found 6 JPA repository interfaces.
2026-03-19 11:38:30.509 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-19 11:38:30.510 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data LDAP repositories in DEFAULT mode.
2026-03-19 11:38:30.515 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginAttemptRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-19 11:38:30.515 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginParamRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-19 11:38:30.516 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.MenuItemRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-19 11:38:30.516 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RefreshTokenRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-19 11:38:30.516 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RolePermissionsRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-19 11:38:30.516 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.UserRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-19 11:38:30.516 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 3 ms. Found 0 LDAP repository interfaces.
2026-03-19 11:38:30.606 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-19 11:38:30.607 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-19 11:38:30.615 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginAttemptRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 11:38:30.616 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginParamRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 11:38:30.616 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.MenuItemRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 11:38:30.616 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RefreshTokenRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 11:38:30.616 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RolePermissionsRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 11:38:30.617 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.UserRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 11:38:30.700 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 86 ms. Found 0 Redis repository interfaces.
2026-03-19 11:38:34.106 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 8085 (http)
2026-03-19 11:38:34.116 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-8085"]
2026-03-19 11:38:34.118 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
2026-03-19 11:38:34.118 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.43]
2026-03-19 11:38:35.602 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-19 11:39:07.280 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default]
2026-03-19 11:39:07.411 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.6.22.Final
2026-03-19 11:39:07.513 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled
2026-03-19 11:39:08.509 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer
2026-03-19 11:39:08.603 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-19 11:39:39.640 WARN  [main] o.h.e.j.s.SqlExceptionHelper: SQL Error: 12170, SQLState: 08006
2026-03-19 11:39:39.640 ERROR [main] o.h.e.j.s.SqlExceptionHelper: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=KpBQKyiXSji77huDv0ljsw==)
https://docs.oracle.com/error-help/db/ora-12170/
2026-03-19 11:39:39.641 WARN  [main] o.h.e.j.e.i.JdbcEnvironmentInitiator: HHH000342: Could not obtain connection to query metadata
org.hibernate.exception.JDBCConnectionException: unable to obtain isolated JDBC connection [ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=KpBQKyiXSji77huDv0ljsw==)
https://docs.oracle.com/error-help/db/ora-12170/] [n/a]
        at org.hibernate.exception.internal.SQLStateConversionDelegate.convert(SQLStateConversionDelegate.java:100)
        at org.hibernate.exception.internal.StandardSQLExceptionConverter.convert(StandardSQLExceptionConverter.java:58)
        at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:108)
        at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:94)
        at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:116)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:336)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:129)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:81)
        at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
        at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:226)
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:194)
        at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1442)
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1513)
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:66)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:419)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:400)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1873)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1822)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:607)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:529)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:339)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:373)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:207)
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:970)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:627)
        at org.springframework.boot.web.reactive.context.ReactiveWebServerApplicationContext.refresh(ReactiveWebServerApplicationContext.java:66)
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:752)
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:439)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:318)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1361)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1350)
        at com.fincore.gateway.LoginService.main(LoginService.java:12)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:102)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
Caused by: java.sql.SQLTimeoutException: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=KpBQKyiXSji77huDv0ljsw==)
https://docs.oracle.com/error-help/db/ora-12170/
        at oracle.jdbc.driver.T4CConnection.handleLogonNetException(T4CConnection.java:1853)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:1204)
        at oracle.jdbc.driver.PhysicalConnection.connect(PhysicalConnection.java:1189)
        at oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:106)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:887)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:694)
        at com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:144)
        at com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:368)
        at com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:205)
        at com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:488)
        at com.zaxxer.hikari.pool.HikariPool.checkFailFast(HikariPool.java:576)
        at com.zaxxer.hikari.pool.HikariPool.<init>(HikariPool.java:97)
        at com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:111)
        at org.hibernate.engine.jdbc.connections.internal.DatasourceConnectionProviderImpl.getConnection(DatasourceConnectionProviderImpl.java:126)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator$ConnectionProviderJdbcConnectionAccess.obtainConnection(JdbcEnvironmentInitiator.java:483)
        at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:61)
        ... 40 common frames omitted
Caused by: oracle.net.ns.NetException: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=KpBQKyiXSji77huDv0ljsw==)
https://docs.oracle.com/error-help/db/ora-12170/
        at oracle.net.nt.TcpNTAdapter.handleEstablishSocketException(TcpNTAdapter.java:385)
        at oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:350)
        at oracle.net.nt.TcpNTAdapter.connect(TcpNTAdapter.java:228)
        at oracle.net.nt.ConnOption.connect(ConnOption.java:346)
        at oracle.net.nt.ConnStrategy.executeConnOption(ConnStrategy.java:1252)
        at oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:778)
        at oracle.net.resolver.AddrResolution.resolveAndExecute(AddrResolution.java:718)
        at oracle.net.ns.NSProtocol.establishConnection(NSProtocol.java:960)
        at oracle.net.ns.NSProtocol.connect(NSProtocol.java:329)
        at oracle.jdbc.driver.T4CConnection.connectNetworkSessionProtocol(T4CConnection.java:3684)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:1083)
        ... 54 common frames omitted
2026-03-19 11:39:39.643 ERROR [main] o.s.o.j.AbstractEntityManagerFactoryBean: Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-03-19 11:39:39.643 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-03-19 11:39:39.646 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
2026-03-19 11:39:39.658 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-19 11:39:39.709 ERROR [main] o.s.b.SpringApplication: Application run failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1826)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:607)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:529)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:339)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:373)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:207)
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:970)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:627)
        at org.springframework.boot.web.reactive.context.ReactiveWebServerApplicationContext.refresh(ReactiveWebServerApplicationContext.java:66)
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:752)
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:439)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:318)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1361)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1350)
        at com.fincore.gateway.LoginService.main(LoginService.java:12)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:102)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
Caused by: org.hibernate.service.spi.ServiceException: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:276)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
        at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:226)
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:194)
        at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1442)
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1513)
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:66)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:419)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:400)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1873)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1822)
        ... 20 common frames omitted
Caused by: org.hibernate.HibernateException: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.determineDialect(DialectFactoryImpl.java:191)
        at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.buildDialect(DialectFactoryImpl.java:87)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentWithDefaults(JdbcEnvironmentInitiator.java:186)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:408)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:129)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:81)
        at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
        ... 35 common frames omitted

        what this issue is about??
