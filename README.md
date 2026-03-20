2026-03-20 10:02:31.911 INFO  [main] o.s.b.StartupInfoLogger: Starting ProcessStatusApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-20 10:02:31.917 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "dev"
2026-03-20 10:02:36.609 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-20 10:02:36.611 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-20 10:02:37.116 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 418 ms. Found 11 JPA repository interfaces.
2026-03-20 10:02:37.211 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-20 10:02:37.212 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-20 10:02:37.299 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.ControlFileMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.300 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.FileSummaryRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.300 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.FileTypeRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.301 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.FincoreDagRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.301 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.FincoreDateRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.301 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.FincoreProcessRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.301 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.FincoreProcessStageRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.301 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.ProcessRunRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.302 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.ProcessRunStageRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.302 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.ProcessStagesRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.302 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.process_status_service.repository.ProcessStatusRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-20 10:02:37.302 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 83 ms. Found 0 Redis repository interfaces.
2026-03-20 10:02:41.805 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 3000 (http)
2026-03-20 10:02:41.813 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-3000"]
2026-03-20 10:02:41.815 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
2026-03-20 10:02:41.815 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.24]
2026-03-20 10:02:42.100 INFO  [main] o.a.j.l.DirectJDKLog: Initializing Spring embedded WebApplicationContext
2026-03-20 10:02:42.101 INFO  [main] o.s.b.w.s.c.ServletWebServerApplicationContext: Root WebApplicationContext: initialization completed in 9902 ms
2026-03-20 10:02:44.919 INFO  [main] o.s.b.w.s.RegistrationBean: Filter mdcFilterRegistration was not registered (disabled)
2026-03-20 10:02:44.919 INFO  [main] o.s.b.w.s.RegistrationBean: Filter rbacFilterRegistration was not registered (disabled)
2026-03-20 10:02:46.207 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-20 10:02:47.719 INFO  [main] c.z.h.p.HikariPool: HikariPool-1 - Added connection oracle.jdbc.driver.T4CConnection@6a8ab98f
2026-03-20 10:02:47.721 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Start completed.
2026-03-20 10:02:47.908 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default]
2026-03-20 10:02:48.206 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.5.2.Final
2026-03-20 10:02:48.404 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled
2026-03-20 10:02:49.707 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer
2026-03-20 10:02:52.299 INFO  [main] o.h.v.i.u.Version: HV000001: Hibernate Validator 8.0.1.Final
2026-03-20 10:02:56.105 INFO  [main] o.h.e.t.j.p.i.JtaPlatformInitiator: HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)
2026-03-20 10:02:56.108 INFO  [main] o.s.o.j.AbstractEntityManagerFactoryBean: Initialized JPA EntityManagerFactory for persistence unit 'default'
2026-03-20 10:02:59.107 INFO  [main] o.s.d.j.r.q.QueryEnhancerFactory: Hibernate is in classpath; If applicable, HQL parser will be used.
2026-03-20 10:02:59.806 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'pysparkKafkaConsumerService' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/process_status_service/consumer/PysparkKafkaConsumerService.class]: Unsatisfied dependency expressed through constructor parameter 0: Error creating bean with name 'ProcessStatusService' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/process_status_service/service/ProcessStatusServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 3: Error creating bean with name 'fileServiceImpl' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/process_status_service/service/FileServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 1: Error creating bean with name 'com.fincore.commonutilities.buisnessobject.ControlDateService': Invocation of init method failed
2026-03-20 10:02:59.807 INFO  [main] o.s.o.j.AbstractEntityManagerFactoryBean: Closing JPA EntityManagerFactory for persistence unit 'default'
2026-03-20 10:02:59.808 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Shutdown initiated...
2026-03-20 10:02:59.935 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Shutdown completed.
2026-03-20 10:03:00.003 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
2026-03-20 10:03:00.098 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-20 10:03:00.111 ERROR [main] o.s.b.SpringApplication: Application run failed
org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'pysparkKafkaConsumerService' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/process_status_service/consumer/PysparkKafkaConsumerService.class]: Unsatisfied dependency expressed through constructor parameter 0: Error creating bean with name 'ProcessStatusService' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/process_status_service/service/ProcessStatusServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 3: Error creating bean with name 'fileServiceImpl' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/process_status_service/service/FileServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 1: Error creating bean with name 'com.fincore.commonutilities.buisnessobject.ControlDateService': Invocation of init method failed
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:795)
        at org.springframework.beans.factory.support.ConstructorResolver.autowireConstructor(ConstructorResolver.java:237)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.autowireConstructor(AbstractAutowireCapableBeanFactory.java:1357)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1194)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:562)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:975)
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:962)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
        at com.fincore.process_status_service.ProcessStatusApplication.main(ProcessStatusApplication.java:12)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
Caused by: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'ProcessStatusService' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/process_status_service/service/ProcessStatusServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 3: Error creating bean with name 'fileServiceImpl' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/process_status_service/service/FileServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 1: Error creating bean with name 'com.fincore.commonutilities.buisnessobject.ControlDateService': Invocation of init method failed
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:795)
        at org.springframework.beans.factory.support.ConstructorResolver.autowireConstructor(ConstructorResolver.java:237)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.autowireConstructor(AbstractAutowireCapableBeanFactory.java:1357)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1194)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:562)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200)
        at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:254)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1443)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1353)
        at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:904)
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:782)
        ... 24 common frames omitted
Caused by: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'fileServiceImpl' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/process_status_service/service/FileServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 1: Error creating bean with name 'com.fincore.commonutilities.buisnessobject.ControlDateService': Invocation of init method failed
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:795)
        at org.springframework.beans.factory.support.ConstructorResolver.autowireConstructor(ConstructorResolver.java:237)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.autowireConstructor(AbstractAutowireCapableBeanFactory.java:1357)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1194)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:562)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200)
        at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:254)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1443)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1353)
        at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:904)
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:782)
        ... 38 common frames omitted
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'com.fincore.commonutilities.buisnessobject.ControlDateService': Invocation of init method failed
        at org.springframework.beans.factory.annotation.InitDestroyAnnotationBeanPostProcessor.postProcessBeforeInitialization(InitDestroyAnnotationBeanPostProcessor.java:222)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyBeanPostProcessorsBeforeInitialization(AbstractAutowireCapableBeanFactory.java:422)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1780)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200)
        at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:254)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1443)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1353)
        at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:904)
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:782)
        ... 52 common frames omitted
Caused by: org.springframework.dao.EmptyResultDataAccessException: Incorrect result size: expected 1, actual 0
        at org.springframework.dao.support.DataAccessUtils.nullableSingleResult(DataAccessUtils.java:190)
        at org.springframework.jdbc.core.JdbcTemplate.queryForObject(JdbcTemplate.java:520)
        at com.fincore.commonutilities.buisnessobject.ControlDateService.getControlDates(ControlDateService.java:22)
        at com.fincore.commonutilities.buisnessobject.ControlDateService.validate(ControlDateService.java:19)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.beans.factory.annotation.InitDestroyAnnotationBeanPostProcessor$LifecycleMethod.invoke(InitDestroyAnnotationBeanPostProcessor.java:457)
        at org.springframework.beans.factory.annotation.InitDestroyAnnotationBeanPostProcessor$LifecycleMetadata.invokeInitMethods(InitDestroyAnnotationBeanPostProcessor.java:401)
        at org.springframework.beans.factory.annotation.InitDestroyAnnotationBeanPostProcessor.postProcessBeforeInitialization(InitDestroyAnnotationBeanPostProcessor.java:219)
        ... 65 common frames omitted

        what is the issue?
