


[root@fcsitgateway SIT-Microservice]# k logs voucher-service-deployment-56477c4b8f-mtb9k
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v3.3.0)

2026-06-18T12:29:06.905Z  INFO 1 --- [VoucherService] [           main] c.f.V.VoucherServiceApplication          : Starting VoucherServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)
2026-06-18T12:29:06.909Z  INFO 1 --- [VoucherService] [           main] c.f.V.VoucherServiceApplication          : The following 1 profile is active: "sit"
2026-06-18T12:29:07.761Z  INFO 1 --- [VoucherService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Multiple Spring Data modules found, entering strict repository configuration mode
2026-06-18T12:29:07.761Z  INFO 1 --- [VoucherService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-06-18T12:29:07.919Z  INFO 1 --- [VoucherService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Finished Spring Data repository scanning in 150 ms. Found 11 JPA repository interfaces.
2026-06-18T12:29:08.223Z  INFO 1 --- [VoucherService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Multiple Spring Data modules found, entering strict repository configuration mode
2026-06-18T12:29:08.224Z  INFO 1 --- [VoucherService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-06-18T12:29:08.248Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.BranchMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.249Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.CglMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.249Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.FincoreDateRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.249Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.JournalRequestRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.249Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.JsEodMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.250Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.251Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.PermissionRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.251Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.RequestVoucherRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.251Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.VoucherLogRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.251Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.VoucherPostingRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.251Z  INFO 1 --- [VoucherService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.VoucherService.Repository.VoucherWorkflowRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-06-18T12:29:08.251Z  INFO 1 --- [VoucherService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Finished Spring Data repository scanning in 19 ms. Found 0 Redis repository interfaces.
2026-06-18T12:29:09.310Z  INFO 1 --- [VoucherService] [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port 9999 (http)
2026-06-18T12:29:09.322Z  INFO 1 --- [VoucherService] [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2026-06-18T12:29:09.322Z  INFO 1 --- [VoucherService] [           main] o.apache.catalina.core.StandardEngine    : Starting Servlet engine: [Apache Tomcat/10.1.24]
2026-06-18T12:29:09.355Z  INFO 1 --- [VoucherService] [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2026-06-18T12:29:09.356Z  INFO 1 --- [VoucherService] [           main] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 2370 ms
2026-06-18T12:29:09.463Z  INFO 1 --- [VoucherService] [           main] c.f.V.config.OracleDbConfig              : ORACLE_DB_INIT | Initializing Primary Oracle DataSource
2026-06-18T12:29:09.679Z  INFO 1 --- [VoucherService] [           main] c.f.V.config.OracleDbConfig              : ORACLE_EMF_INIT | Building EntityManagerFactory for com.fincore.VoucherService.Models
2026-06-18T12:29:09.709Z  INFO 1 --- [VoucherService] [           main] o.hibernate.jpa.internal.util.LogHelper  : HHH000204: Processing PersistenceUnitInfo [name: oracle]
2026-06-18T12:29:09.760Z  INFO 1 --- [VoucherService] [           main] org.hibernate.Version                    : HHH000412: Hibernate ORM core version 6.5.2.Final
2026-06-18T12:29:09.798Z  INFO 1 --- [VoucherService] [           main] o.h.c.internal.RegionFactoryInitiator    : HHH000026: Second-level cache disabled
2026-06-18T12:29:10.141Z  INFO 1 --- [VoucherService] [           main] o.s.o.j.p.SpringPersistenceUnitInfo      : No LoadTimeWeaver setup: ignoring JPA class transformer
2026-06-18T12:29:10.169Z  INFO 1 --- [VoucherService] [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2026-06-18T12:29:41.321Z  WARN 1 --- [VoucherService] [           main] o.h.e.j.e.i.JdbcEnvironmentInitiator     : HHH000342: Could not obtain connection to query metadata

java.lang.NullPointerException: Cannot invoke "org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(java.sql.SQLException, String)" because the return value of "org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.sqlExceptionHelper()" is null
        at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:116) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:290) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.model.relational.Database.<init>(Database.java:45) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952) ~[spring-context-6.1.8.jar!/:6.1.8]
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624) ~[spring-context-6.1.8.jar!/:6.1.8]
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:335) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at com.fincore.VoucherService.VoucherServiceApplication.main(VoucherServiceApplication.java:34) ~[!/:0.0.1-SNAPSHOT]
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
        at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91) ~[app.jar:0.0.1-SNAPSHOT]
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53) ~[app.jar:0.0.1-SNAPSHOT]
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58) ~[app.jar:0.0.1-SNAPSHOT]

2026-06-18T12:29:41.341Z  WARN 1 --- [VoucherService] [           main] org.hibernate.orm.deprecation            : HHH90000025: OracleDialect does not need to be specified explicitly using 'hibernate.dialect' (remove the property setting and it will be selected by default)
2026-06-18T12:29:42.253Z  INFO 1 --- [VoucherService] [           main] o.h.e.t.j.p.i.JtaPlatformInitiator       : HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)
2026-06-18T12:29:42.268Z  INFO 1 --- [VoucherService] [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2026-06-18T12:30:13.272Z  WARN 1 --- [VoucherService] [           main] o.h.engine.jdbc.spi.SqlExceptionHelper   : SQL Error: 17002, SQLState: 08006
2026-06-18T12:30:13.272Z ERROR 1 --- [VoucherService] [           main] o.h.engine.jdbc.spi.SqlExceptionHelper   : IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=LzUXjY5YQX6bkL7zOUE49A==)
2026-06-18T12:30:13.276Z ERROR 1 --- [VoucherService] [           main] j.LocalContainerEntityManagerFactoryBean : Failed to initialize JPA EntityManagerFactory: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=LzUXjY5YQX6bkL7zOUE49A==)] [n/a]
2026-06-18T12:30:13.277Z  WARN 1 --- [VoucherService] [           main] ConfigServletWebServerApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'oracleEntityManagerFactory' defined in class path resource [com/fincore/VoucherService/config/OracleDbConfig.class]: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=LzUXjY5YQX6bkL7zOUE49A==)] [n/a]
2026-06-18T12:30:13.279Z  INFO 1 --- [VoucherService] [           main] o.apache.catalina.core.StandardService   : Stopping service [Tomcat]
2026-06-18T12:30:13.292Z  INFO 1 --- [VoucherService] [           main] .s.b.a.l.ConditionEvaluationReportLogger :

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-06-18T12:30:13.309Z ERROR 1 --- [VoucherService] [           main] o.s.boot.SpringApplication               : Application run failed

org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'oracleEntityManagerFactory' defined in class path resource [com/fincore/VoucherService/config/OracleDbConfig.class]: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=LzUXjY5YQX6bkL7zOUE49A==)] [n/a]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1788) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952) ~[spring-context-6.1.8.jar!/:6.1.8]
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624) ~[spring-context-6.1.8.jar!/:6.1.8]
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:335) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at com.fincore.VoucherService.VoucherServiceApplication.main(VoucherServiceApplication.java:34) ~[!/:0.0.1-SNAPSHOT]
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
        at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91) ~[app.jar:0.0.1-SNAPSHOT]
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53) ~[app.jar:0.0.1-SNAPSHOT]
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58) ~[app.jar:0.0.1-SNAPSHOT]
Caused by: jakarta.persistence.PersistenceException: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=LzUXjY5YQX6bkL7zOUE49A==)] [n/a]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:421) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784) ~[spring-beans-6.1.8.jar!/:6.1.8]
        ... 20 common frames omitted
Caused by: org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=LzUXjY5YQX6bkL7zOUE49A==)] [n/a]
        at org.hibernate.exception.internal.SQLStateConversionDelegate.convert(SQLStateConversionDelegate.java:100) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.exception.internal.StandardSQLExceptionConverter.convert(StandardSQLExceptionConverter.java:58) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:108) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:94) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:74) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:39) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.tool.schema.internal.exec.ImprovedExtractionContextImpl.getJdbcConnection(ImprovedExtractionContextImpl.java:63) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.tool.schema.extract.spi.ExtractionContext.getQueryResults(ExtractionContext.java:43) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.tool.schema.extract.internal.SequenceInformationExtractorLegacyImpl.extractMetadata(SequenceInformationExtractorLegacyImpl.java:39) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.tool.schema.extract.internal.DatabaseInformationImpl.initializeSequences(DatabaseInformationImpl.java:66) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.tool.schema.extract.internal.DatabaseInformationImpl.<init>(DatabaseInformationImpl.java:60) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.tool.schema.internal.Helper.buildDatabaseInformation(Helper.java:185) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.tool.schema.internal.AbstractSchemaValidator.doValidation(AbstractSchemaValidator.java:68) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.tool.schema.spi.SchemaManagementToolCoordinator.performDatabaseAction(SchemaManagementToolCoordinator.java:289) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.tool.schema.spi.SchemaManagementToolCoordinator.lambda$process$5(SchemaManagementToolCoordinator.java:144) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at java.base/java.util.HashMap.forEach(HashMap.java:1429) ~[na:na]
        at org.hibernate.tool.schema.spi.SchemaManagementToolCoordinator.process(SchemaManagementToolCoordinator.java:141) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.internal.SessionFactoryObserverForSchemaExport.sessionFactoryCreated(SessionFactoryObserverForSchemaExport.java:37) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.internal.SessionFactoryObserverChain.sessionFactoryCreated(SessionFactoryObserverChain.java:35) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.internal.SessionFactoryImpl.<init>(SessionFactoryImpl.java:322) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.internal.SessionFactoryBuilderImpl.build(SessionFactoryBuilderImpl.java:457) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1506) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409) ~[spring-orm-6.1.8.jar!/:6.1.8]
        ... 24 common frames omitted
Caused by: java.sql.SQLRecoverableException: IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=LzUXjY5YQX6bkL7zOUE49A==)
        at oracle.jdbc.driver.T4CConnection.handleLogonNetException(T4CConnection.java:902) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:707) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.jdbc.driver.PhysicalConnection.connect(PhysicalConnection.java:1094) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:89) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:732) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:648) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:137) ~[HikariCP-5.1.0.jar!/:na]
        at com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:360) ~[HikariCP-5.1.0.jar!/:na]
        at com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:202) ~[HikariCP-5.1.0.jar!/:na]
        at com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:461) ~[HikariCP-5.1.0.jar!/:na]
        at com.zaxxer.hikari.pool.HikariPool.checkFailFast(HikariPool.java:550) ~[HikariCP-5.1.0.jar!/:na]
        at com.zaxxer.hikari.pool.HikariPool.<init>(HikariPool.java:98) ~[HikariCP-5.1.0.jar!/:na]
        at com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:111) ~[HikariCP-5.1.0.jar!/:na]
        at org.hibernate.engine.jdbc.connections.internal.DatasourceConnectionProviderImpl.getConnection(DatasourceConnectionProviderImpl.java:122) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator$ConnectionProviderJdbcConnectionAccess.obtainConnection(JdbcEnvironmentInitiator.java:437) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:46) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        ... 44 common frames omitted
Caused by: oracle.net.ns.NetException: The Network Adapter could not establish the connection (CONNECTION_ID=LzUXjY5YQX6bkL7zOUE49A==)
        at oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:715) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.resolver.AddrResolution.resolveAndExecute(AddrResolution.java:584) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.ns.NSProtocol.establishConnection(NSProtocol.java:964) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.ns.NSProtocol.connect(NSProtocol.java:350) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.jdbc.driver.T4CConnection.connect(T4CConnection.java:2627) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:666) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        ... 58 common frames omitted
Caused by: java.io.IOException: Socket read timed out, socket connect lapse 30000 ms. 10.177.103.192 1523  30000 (1/1) true
        at oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:403) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.nt.TcpNTAdapter.doLocalDNSLookupConnect(TcpNTAdapter.java:307) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.nt.TcpNTAdapter.connect(TcpNTAdapter.java:269) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.nt.ConnOption.connect(ConnOption.java:230) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.nt.ConnStrategy.executeConnOption(ConnStrategy.java:1014) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:673) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        ... 63 common frames omitted
Caused by: oracle.net.nt.TimeoutInterruptHandler$IOReadTimeoutException: Socket read timed out
        at oracle.net.nt.TimeoutSocketChannel.handleInterrupt(TimeoutSocketChannel.java:543) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.nt.TimeoutSocketChannel.connect(TimeoutSocketChannel.java:196) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.nt.TimeoutSocketChannel.<init>(TimeoutSocketChannel.java:157) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        at oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:384) ~[ojdbc11-21.9.0.0.jar!/:21.9.0.0.0]
        ... 68 common frames omitted


still i m getting the same issue
