
2026-06-25 09:03:07.791 INFO  [main] o.s.b.StartupInfoLogger: Starting NotificationServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)
{"@timestamp":"2026-06-25T14:33:07.791359632+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.N.NotificationServiceApplication","message":"Starting NotificationServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)","stack_trace":""}
2026-06-25 09:03:07.797 DEBUG [main] o.s.b.StartupInfoLogger: Running with Spring Boot v3.3.0, Spring v6.1.8
{"@timestamp":"2026-06-25T14:33:07.797848832+05:30","level":"DEBUG","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.N.NotificationServiceApplication","message":"Running with Spring Boot v3.3.0, Spring v6.1.8","stack_trace":""}
2026-06-25 09:03:07.798 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "dev"
{"@timestamp":"2026-06-25T14:33:07.798823166+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.N.NotificationServiceApplication","message":"The following 1 profile is active: \"dev\"","stack_trace":""}
2026-06-25 09:03:08.852 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
{"@timestamp":"2026-06-25T14:33:08.852379999+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Multiple Spring Data modules found, entering strict repository configuration mode","stack_trace":""}
2026-06-25 09:03:08.854 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
{"@timestamp":"2026-06-25T14:33:08.854263625+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Bootstrapping Spring Data JPA repositories in DEFAULT mode.","stack_trace":""}
2026-06-25 09:03:08.972 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 112 ms. Found 2 JPA repository interfaces.
{"@timestamp":"2026-06-25T14:33:08.972964364+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Finished Spring Data repository scanning in 112 ms. Found 2 JPA repository interfaces.","stack_trace":""}
2026-06-25 09:03:08.990 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
{"@timestamp":"2026-06-25T14:33:08.990372873+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Multiple Spring Data modules found, entering strict repository configuration mode","stack_trace":""}
2026-06-25 09:03:08.991 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
{"@timestamp":"2026-06-25T14:33:08.991908066+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Bootstrapping Spring Data Redis repositories in DEFAULT mode.","stack_trace":""}
2026-06-25 09:03:09.005 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
{"@timestamp":"2026-06-25T14:33:09.005887985+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationExtensionSupport","message":"Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository","stack_trace":""}
2026-06-25 09:03:09.007 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
{"@timestamp":"2026-06-25T14:33:09.007134361+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationExtensionSupport","message":"Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository","stack_trace":""}
2026-06-25 09:03:09.007 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 6 ms. Found 0 Redis repository interfaces.
{"@timestamp":"2026-06-25T14:33:09.00753859+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Finished Spring Data repository scanning in 6 ms. Found 0 Redis repository interfaces.","stack_trace":""}
2026-06-25 09:03:10.098 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 9010 (http)
{"@timestamp":"2026-06-25T14:33:10.098924409+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.w.embedded.tomcat.TomcatWebServer","message":"Tomcat initialized with port 9010 (http)","stack_trace":""}
2026-06-25 09:03:10.110 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-9010"]
{"@timestamp":"2026-06-25T14:33:10.110837703+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.coyote.http11.Http11NioProtocol","message":"Initializing ProtocolHandler [\"http-nio-9010\"]","stack_trace":""}
2026-06-25 09:03:10.112 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
{"@timestamp":"2026-06-25T14:33:10.11285029+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.catalina.core.StandardService","message":"Starting service [Tomcat]","stack_trace":""}
2026-06-25 09:03:10.113 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.24]
{"@timestamp":"2026-06-25T14:33:10.113161344+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.catalina.core.StandardEngine","message":"Starting Servlet engine: [Apache Tomcat/10.1.24]","stack_trace":""}
2026-06-25 09:03:10.139 INFO  [main] o.a.j.l.DirectJDKLog: Initializing Spring embedded WebApplicationContext
{"@timestamp":"2026-06-25T14:33:10.139863363+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.a.c.c.C.[Tomcat].[localhost].[/]","message":"Initializing Spring embedded WebApplicationContext","stack_trace":""}
2026-06-25 09:03:10.141 INFO  [main] o.s.b.w.s.c.ServletWebServerApplicationContext: Root WebApplicationContext: initialization completed in 2305 ms
{"@timestamp":"2026-06-25T14:33:10.141089253+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.w.s.c.ServletWebServerApplicationContext","message":"Root WebApplicationContext: initialization completed in 2305 ms","stack_trace":""}
2026-06-25 09:03:10.816 INFO  [main] o.s.b.w.s.RegistrationBean: Filter mdcFilterRegistration was not registered (disabled)
{"@timestamp":"2026-06-25T14:33:10.816955327+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.boot.web.servlet.RegistrationBean","message":"Filter mdcFilterRegistration was not registered (disabled)","stack_trace":""}
2026-06-25 09:03:10.817 INFO  [main] o.s.b.w.s.RegistrationBean: Filter rbacFilterRegistration was not registered (disabled)
{"@timestamp":"2026-06-25T14:33:10.817341718+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.boot.web.servlet.RegistrationBean","message":"Filter rbacFilterRegistration was not registered (disabled)","stack_trace":""}
2026-06-25 09:03:11.019 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default]
{"@timestamp":"2026-06-25T14:33:11.019049979+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.hibernate.jpa.internal.util.LogHelper","message":"HHH000204: Processing PersistenceUnitInfo [name: default]","stack_trace":""}
2026-06-25 09:03:11.064 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.5.2.Final
{"@timestamp":"2026-06-25T14:33:11.064771821+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.hibernate.Version","message":"HHH000412: Hibernate ORM core version 6.5.2.Final","stack_trace":""}
2026-06-25 09:03:11.095 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled
{"@timestamp":"2026-06-25T14:33:11.095208772+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.h.c.internal.RegionFactoryInitiator","message":"HHH000026: Second-level cache disabled","stack_trace":""}
2026-06-25 09:03:11.354 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer
{"@timestamp":"2026-06-25T14:33:11.354520728+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.o.j.p.SpringPersistenceUnitInfo","message":"No LoadTimeWeaver setup: ignoring JPA class transformer","stack_trace":""}
2026-06-25 09:03:11.379 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
{"@timestamp":"2026-06-25T14:33:11.379184067+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"com.zaxxer.hikari.HikariDataSource","message":"HikariPool-1 - Starting...","stack_trace":""}
2026-06-25 09:03:22.521 WARN  [main] o.h.e.j.e.i.JdbcEnvironmentInitiator: HHH000342: Could not obtain connection to query metadata
java.lang.NullPointerException: Cannot invoke "org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(java.sql.SQLException, String)" because the return value of "org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.sqlExceptionHelper()" is null
        at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:116)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:290)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)
        at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
        at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189)
        at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431)
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502)
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
        at com.fincore.NotificationService.NotificationServiceApplication.main(NotificationServiceApplication.java:18)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
{"@timestamp":"2026-06-25T14:33:22.521437025+05:30","level":"WARN","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.h.e.j.e.i.JdbcEnvironmentInitiator","message":"HHH000342: Could not obtain connection to query metadata","stack_trace":"java.lang.NullPointerException: Cannot invoke \"org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(java.sql.SQLException, String)\" because the return value of \"org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.sqlExceptionHelper()\" is null\n\tat org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:116)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:290)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)\n\tat org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)\n\tat org.hibernate.boot.model.relational.Database.<init>(Database.java:45)\n\tat org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)\n"}
2026-06-25 09:03:22.523 ERROR [main] o.s.o.j.AbstractEntityManagerFactoryBean: Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
{"@timestamp":"2026-06-25T14:33:22.52385272+05:30","level":"ERROR","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.o.j.LocalContainerEntityManagerFactoryBean","message":"Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)","stack_trace":""}
2026-06-25 09:03:22.524 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
{"@timestamp":"2026-06-25T14:33:22.524795386+05:30","level":"WARN","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.w.s.c.AnnotationConfigServletWebServerApplicationContext","message":"Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)","stack_trace":""}
2026-06-25 09:03:22.538 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
{"@timestamp":"2026-06-25T14:33:22.538040909+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.catalina.core.StandardService","message":"Stopping service [Tomcat]","stack_trace":""}
2026-06-25 09:03:22.554 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
{"@timestamp":"2026-06-25T14:33:22.554677908+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.a.l.ConditionEvaluationReportLogger","message":"\n\nError starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.","stack_trace":""}
2026-06-25 09:03:22.568 ERROR [main] o.s.b.SpringApplication: Application run failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1788)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
        at com.fincore.NotificationService.NotificationServiceApplication.main(NotificationServiceApplication.java:18)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
Caused by: org.hibernate.service.spi.ServiceException: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:276)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
        at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189)
        at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431)
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502)
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
        ... 20 common frames omitted
Caused by: org.hibernate.HibernateException: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.determineDialect(DialectFactoryImpl.java:191)
        at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.buildDialect(DialectFactoryImpl.java:87)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentWithDefaults(JdbcEnvironmentInitiator.java:152)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:362)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)
        at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
        ... 35 common frames omitted
{"@timestamp":"2026-06-25T14:33:22.568872646+05:30","level":"ERROR","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.springframework.boot.SpringApplication","message":"Application run failed","stack_trace":"org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1788)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)\n\tat org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)\n\tat org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)\n\tat org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)\n\tat org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)\nCaused by: org.hibernate.service.spi.ServiceException: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:276)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)\n\tat org.hibernate.boot.model.relational.Database.<init>(Database.java:45)\n\tat org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)\n\tat org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189)\n\tat org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)\n\tat org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431)\n\tat org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502)\n\tat org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)\nCaused by: org.hibernate.HibernateException: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)\n\tat org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.determineDialect(DialectFactoryImpl.java:191)\n\tat org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.buildDialect(DialectFactoryImpl.java:87)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentWithDefaults(JdbcEnvironmentInitiator.java:152)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:362)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)\n\tat org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)\n"}


[root@fcsitgateway Network]# k get networkpolicy -A
NAMESPACE   NAME                       POD-SELECTOR                  AGE
cbops       allow-dns                  app=voucher-service-backend   47h
cbops       allow-dns-notification     app=notification-backend      59m
cbops       allow-egress-to-oracle     app=voucher-service-backend   6d19h
cbops       allow-kafka-notification   app=notification-backend      59m
cbops       allow-oracle               app=voucher-service-backend   6d19h
cbops       allow-oracle-db-egress     app=fincore-app               185d
cbops       allow-postgres-db-egress   app=fincore-app               175d
cbops       allow-postgres-egress      <none>                        92s
cbops       allow-redis                app=voucher-service-backend   47h


I have mentioned this below networpolicy :


apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-postgres-egress
  namespace: cbops
spec:
  egress:
  - ports:
    - port: 5435
      protocol: TCP
    to:
    - ipBlock:
        cidr: 10.177.179.51/32
  podSelector: {}
  policyTypes:
  - Egress
 
 
 


