
2026-03-20 08:24:57.990 INFO  [main] o.s.b.StartupInfoLogger: Starting LoginService v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-20 08:24:57.996 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "dev"
2026-03-20 08:25:02.286 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-20 08:25:02.287 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-20 08:25:02.689 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 394 ms. Found 6 JPA repository interfaces.
2026-03-20 08:25:02.697 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-20 08:25:02.697 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data LDAP repositories in DEFAULT mode.
2026-03-20 08:25:02.782 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginAttemptRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-20 08:25:02.782 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginParamRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-20 08:25:02.783 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.MenuItemRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-20 08:25:02.783 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RefreshTokenRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-20 08:25:02.783 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RolePermissionsRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-20 08:25:02.783 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.UserRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-20 08:25:02.784 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 84 ms. Found 0 LDAP repository interfaces.
2026-03-20 08:25:02.880 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-20 08:25:02.882 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-20 08:25:02.891 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginAttemptRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 08:25:02.891 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginParamRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 08:25:02.891 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.MenuItemRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 08:25:02.892 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RefreshTokenRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 08:25:02.892 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RolePermissionsRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 08:25:02.892 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.UserRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 08:25:02.892 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 3 ms. Found 0 Redis repository interfaces.
2026-03-20 08:25:06.296 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 8085 (http)
2026-03-20 08:25:06.305 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-8085"]
2026-03-20 08:25:06.379 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
2026-03-20 08:25:06.380 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.43]
2026-03-20 08:25:07.780 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-20 08:25:39.345 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default]
2026-03-20 08:25:39.493 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.6.22.Final
2026-03-20 08:25:39.599 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled
2026-03-20 08:25:40.697 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer
2026-03-20 08:25:41.096 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-20 08:26:12.134 WARN  [main] o.h.e.j.s.SqlExceptionHelper: SQL Error: 12170, SQLState: 08006
2026-03-20 08:26:12.135 ERROR [main] o.h.e.j.s.SqlExceptionHelper: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=/U3/qvYRQ3axvz3x/AzJTg==)
https://docs.oracle.com/error-help/db/ora-12170/
2026-03-20 08:26:12.136 WARN  [main] o.h.e.j.e.i.JdbcEnvironmentInitiator: HHH000342: Could not obtain connection to query metadata
org.hibernate.exception.JDBCConnectionException: unable to obtain isolated JDBC connection [ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=/U3/qvYRQ3axvz3x/AzJTg==)
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
Caused by: java.sql.SQLTimeoutException: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=/U3/qvYRQ3axvz3x/AzJTg==)
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
Caused by: oracle.net.ns.NetException: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=/U3/qvYRQ3axvz3x/AzJTg==)
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
2026-03-20 08:26:12.138 ERROR [main] o.s.o.j.AbstractEntityManagerFactoryBean: Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-03-20 08:26:12.139 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-03-20 08:26:12.142 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
2026-03-20 08:26:12.154 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-20 08:26:12.182 ERROR [main] o.s.b.SpringApplication: Application run failed
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

        now this is another issue you tell me in my manifest whatt details to add for above issue:

        # =====================================================
# Service Account
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: login-sa
  namespace: backend
automountServiceAccountToken: false

---
# =====================================================
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: login-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: login-backend

---
# =====================================================
# Deployment
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: login-deployment
  namespace: backend
spec:
  replicas: 2
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: login-backend

  template:
    metadata:
      labels:
        app: login-backend

    spec:
      serviceAccountName: login-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      hostAliases:
        - ip: "10.189.42.83"
          hostnames:
            - "uatrootdc1.uatad.sbi"
        - ip: "10.176.53.145"
          hostnames:
            - "CORPDCMDGBL01.CORP.AD.SBI"
        - ip: "10.176.54.30"
          hostnames:
            - "CORPDCMDGBL02.CORP.AD.SBI"
        - ip: "10.176.54.31"
          hostnames:
            - "CORPDCMDGBL03.CORP.AD.SBI"
        - ip: "10.176.54.32"
          hostnames:
            - "CORPDCMDGBL04.CORP.AD.SBI"
        - ip: "10.189.37.135"
          hostnames:
            - "CORPDCMDRBL01.CORP.AD.SBI"
        - ip: "10.189.37.136"
          hostnames:
            - "CORPDCMDRBL02.CORP.AD.SBI"
        - ip: "10.189.37.137"
          hostnames:
            - "CORPDCMDRBL03.CORP.AD.SBI"
        - ip: "10.189.37.138"
          hostnames:
            - "CORPDCMDRBL04.CORP.AD.SBI"

      # =================================================
      # Volumes
      # =================================================
      volumes:
        - name: truststore-volume
          secret:
            secretName: ldap-truststore-file
            items:
              - key: ad-truststore.jks
                path: ad-truststore.jks

        - name: logs-volume
          emptyDir: {}

      containers:
        - name: login-backend-container
          image: a2p05vksharbor.corp.ad.sbi/cbops/login-service:PR01
          imagePullPolicy: Always

          ports:
            - containerPort: 8085

          # =================================================
          # Volume Mounts
          # =================================================
          volumeMounts:
            - name: truststore-volume
              mountPath: "/etc/fincore/secrets"
              readOnly: true

            # Mount writable logs directory
            - name: logs-volume
              mountPath: /logs

          # =================================================
          # Environment Variables
          # =================================================
          env:
            - name: SPRING_LDAP_URLS
              value: "ldaps://uatrootdc1.uatad.sbi:3269"

            - name: JAVA_TOOL_OPTIONS
              value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"

            - name: SPRING_DATA_REDIS_HOST
              value: "redis-service.backend.svc.cluster.local"

            - name: SPRING_DATA_REDIS_PORT
              value: "6379"

            - name: SPRING_DATA_REDIS_CLIENT_TYPE
              value: "lettuce"

            - name: SPRING_PROFILES_ACTIVE
              value: "dev"

            - name: LDAP_TRUSTSTORE_PATH
              value: "file:/etc/fincore/secrets/ad-truststore.jks"

            - name: LDAP_TRUSTSTORE_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: ldap-creds
                  key: truststore-password

          # =================================================
          # Resources
          # =================================================
          resources:
            requests:
              cpu: "250m"
              memory: "512Mi"
            limits:
              cpu: "500m"
              memory: "1Gi"

          # =================================================
          # Probes (TCP Safe Since No Actuator Yet)
          # =================================================
          readinessProbe:
            tcpSocket:
              port: 8085
            initialDelaySeconds: 15
            periodSeconds: 10
            failureThreshold: 5

          livenessProbe:
            tcpSocket:
              port: 8085
            initialDelaySeconds: 30
            periodSeconds: 20
            failureThreshold: 5

          startupProbe:
            tcpSocket:
              port: 8085
            failureThreshold: 30
            periodSeconds: 10

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: false
            capabilities:
              drop:
                - ALL

---
# =====================================================
# Horizontal Pod Autoscaler
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: login-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: login-deployment
  minReplicas: 1
  maxReplicas: 3
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
# =====================================================
# Service
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: login-service
  namespace: backend
spec:
  selector:
    app: login-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8085
  type: ClusterIP

  please alter and send me back: dont alter anyother things only add env  realted to above issue
