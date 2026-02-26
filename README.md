  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v3.3.0)

2026-02-26 11:18:07.111 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.b.StartupInfoLogger←[0;39m: Starting NotificationServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)
2026-02-26 11:18:07.201 ←[39mDEBUG←[0;39m [←[34mmain←[0;39m] ←[33mo.s.b.StartupInfoLogger←[0;39m: Running with Spring Boot v3.3.0, Spring v6.1.8
2026-02-26 11:18:07.203 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.b.SpringApplication←[0;39m: The following 1 profile is active: "dev"
2026-02-26 11:18:11.896 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.d.r.c.RepositoryConfigurationDelegate←[0;39m: Multiple Spring Data modules found, entering strict repository configuration mode
2026-02-26 11:18:11.899 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.d.r.c.RepositoryConfigurationDelegate←[0;39m: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-02-26 11:18:12.406 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.d.r.c.RepositoryConfigurationDelegate←[0;39m: Finished Spring Data repository scanning in 500 ms. Found 2 JPA repository interfaces.
2026-02-26 11:18:12.499 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.d.r.c.RepositoryConfigurationDelegate←[0;39m: Multiple Spring Data modules found, entering strict repository configuration mode
2026-02-26 11:18:12.501 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.d.r.c.RepositoryConfigurationDelegate←[0;39m: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-02-26 11:18:12.515 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.d.r.c.RepositoryConfigurationExtensionSupport←[0;39m: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-02-26 11:18:12.516 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.d.r.c.RepositoryConfigurationExtensionSupport←[0;39m: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-02-26 11:18:12.517 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.d.r.c.RepositoryConfigurationDelegate←[0;39m: Finished Spring Data repository scanning in 6 ms. Found 0 Redis repository interfaces.
2026-02-26 11:18:16.115 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.b.w.e.t.TomcatWebServer←[0;39m: Tomcat initialized with port 9010 (http)
2026-02-26 11:18:16.124 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.a.j.l.DirectJDKLog←[0;39m: Initializing ProtocolHandler ["http-nio-9010"]
2026-02-26 11:18:16.199 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.a.j.l.DirectJDKLog←[0;39m: Starting service [Tomcat]
2026-02-26 11:18:16.199 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.a.j.l.DirectJDKLog←[0;39m: Starting Servlet engine: [Apache Tomcat/10.1.24]
2026-02-26 11:18:16.415 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.a.j.l.DirectJDKLog←[0;39m: Initializing Spring embedded WebApplicationContext
2026-02-26 11:18:16.416 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.b.w.s.c.ServletWebServerApplicationContext←[0;39m: Root WebApplicationContext: initialization completed in 9011 ms
2026-02-26 11:18:18.607 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.b.w.s.RegistrationBean←[0;39m: Filter mdcFilterRegistration was not registered (disabled)
2026-02-26 11:18:18.608 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.b.w.s.RegistrationBean←[0;39m: Filter rbacFilterRegistration was not registered (disabled)
2026-02-26 11:18:19.301 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.h.j.i.u.LogHelper←[0;39m: HHH000204: Processing PersistenceUnitInfo [name: default]
2026-02-26 11:18:19.505 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.h.Version←[0;39m: HHH000412: Hibernate ORM core version 6.5.2.Final
2026-02-26 11:18:19.613 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.h.c.i.RegionFactoryInitiator←[0;39m: HHH000026: Second-level cache disabled
2026-02-26 11:18:20.711 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.o.j.p.SpringPersistenceUnitInfo←[0;39m: No LoadTimeWeaver setup: ignoring JPA class transformer
2026-02-26 11:18:20.896 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mc.z.h.HikariDataSource←[0;39m: HikariPool-1 - Starting...
2026-02-26 11:18:27.821 ←[31mWARN ←[0;39m [←[34mmain←[0;39m] ←[33mo.h.e.j.e.i.JdbcEnvironmentInitiator←[0;39m: HHH000342: Could not obtain connection to query metadata
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
2026-02-26 11:18:27.824 ←[1;31mERROR←[0;39m [←[34mmain←[0;39m] ←[33mo.s.o.j.AbstractEntityManagerFactoryBean←[0;39m: Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 11:18:27.824 ←[31mWARN ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.c.s.AbstractApplicationContext←[0;39m: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 11:18:27.842 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.a.j.l.DirectJDKLog←[0;39m: Stopping service [Tomcat]
2026-02-26 11:18:27.911 ←[34mINFO ←[0;39m [←[34mmain←[0;39m] ←[33mo.s.b.a.l.ConditionEvaluationReportLogger←[0;39m:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-02-26 11:18:28.002 ←[1;31mERROR←[0;39m [←[34mmain←[0;39m] ←[33mo.s.b.SpringApplication←[0;39m: Application run failed
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


        why this issue is coming?
           
