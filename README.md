
2026-03-19 12:20:26 INFO  com.tcs.userservice.UserServiceApplication - Starting UserServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-19 12:20:26 INFO  com.tcs.userservice.UserServiceApplication - The following 1 profile is active: "dev"
2026-03-19 12:20:30 INFO  org.springframework.data.repository.config.RepositoryConfigurationDelegate - Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-19 12:20:30 INFO  org.springframework.data.repository.config.RepositoryConfigurationDelegate - Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationDelegate - Finished Spring Data repository scanning in 496 ms. Found 10 JPA repository interfaces.
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationDelegate - Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationDelegate - Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.PermissionsRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.RolePermissionRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.RolePermissionsRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.RoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.RoleRequestRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.UserLogsRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.UserRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.UserRequestRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationExtensionSupport - Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.tcs.userservice.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 12:20:31 INFO  org.springframework.data.repository.config.RepositoryConfigurationDelegate - Finished Spring Data repository scanning in 89 ms. Found 0 Redis repository interfaces.
2026-03-19 12:20:35 INFO  org.springframework.boot.web.embedded.tomcat.TomcatWebServer - Tomcat initialized with port 8087 (http)
2026-03-19 12:20:35 INFO  org.apache.coyote.http11.Http11NioProtocol - Initializing ProtocolHandler ["http-nio-8087"]
2026-03-19 12:20:35 INFO  org.apache.catalina.core.StandardService - Starting service [Tomcat]
2026-03-19 12:20:35 INFO  org.apache.catalina.core.StandardEngine - Starting Servlet engine: [Apache Tomcat/10.1.24]
2026-03-19 12:20:36 INFO  org.apache.catalina.core.ContainerBase.[Tomcat].[localhost].[/] - Initializing Spring embedded WebApplicationContext
2026-03-19 12:20:36 INFO  org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext - Root WebApplicationContext: initialization completed in 9402 ms
2026-03-19 12:20:39 INFO  org.springframework.boot.web.servlet.RegistrationBean - Filter mdcFilterRegistration was not registered (disabled)
2026-03-19 12:20:39 INFO  org.springframework.boot.web.servlet.RegistrationBean - Filter rbacFilterRegistration was not registered (disabled)
2026-03-19 12:20:40 INFO  com.zaxxer.hikari.HikariDataSource - HikariPool-1 - Starting...
2026-03-19 12:21:11 INFO  org.hibernate.jpa.internal.util.LogHelper - HHH000204: Processing PersistenceUnitInfo [name: default]
2026-03-19 12:21:11 INFO  org.hibernate.Version - HHH000412: Hibernate ORM core version 6.5.2.Final
2026-03-19 12:21:12 INFO  org.hibernate.cache.internal.RegionFactoryInitiator - HHH000026: Second-level cache disabled
2026-03-19 12:21:12 INFO  org.springframework.orm.jpa.persistenceunit.SpringPersistenceUnitInfo - No LoadTimeWeaver setup: ignoring JPA class transformer
2026-03-19 12:21:12 INFO  com.zaxxer.hikari.HikariDataSource - HikariPool-1 - Starting...
2026-03-19 12:21:43 WARN  org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator - HHH000342: Could not obtain connection to query metadata
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
        at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-03-19 12:21:43 ERROR org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean - Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-03-19 12:21:43 WARN  org.springframework.boot.web.servlet.context.AnnotationConfigServletWebServerApplicationContext - Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-03-19 12:21:43 INFO  org.apache.catalina.core.StandardService - Stopping service [Tomcat]
2026-03-19 12:21:44 INFO  org.springframework.boot.autoconfigure.logging.ConditionEvaluationReportLogger -

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-19 12:21:44 ERROR org.springframework.boot.SpringApplication - Application run failed
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
        at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
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

        this issue is coming
        
