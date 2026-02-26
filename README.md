2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.31702681Z stdout F 	... 35 common frames omitted
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317025223Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317023832Z stdout F 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.31702242Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.31702079Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.31701944Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:362)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317017954Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentWithDefaults(JdbcEnvironmentInitiator.java:152)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317016572Z stdout F 	at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.buildDialect(DialectFactoryImpl.java:87)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317015125Z stdout F 	at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.determineDialect(DialectFactoryImpl.java:191)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317013632Z stdout F Caused by: org.hibernate.HibernateException: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317011488Z stdout F 	... 20 common frames omitted
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317009301Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.31700787Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317006295Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.31700495Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317003584Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.317002143Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316998285Z stdout F 	at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316994635Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.31698552Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316984144Z stdout F 	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.31698268Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316981012Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316979623Z stdout F 	at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316978135Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316976708Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316975132Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:276)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316973632Z stdout F Caused by: org.hibernate.service.spi.ServiceException: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316971589Z stdout F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316969964Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316968228Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316966416Z stdout F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316964276Z stdout F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316962636Z stdout F 	at com.fincore.NotificationService.NotificationServiceApplication.main(NotificationServiceApplication.java:18)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316961204Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316959647Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 12:34:23.317	
 2026-02-26T07:04:23.316958024Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316955535Z stdout F 	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316954051Z stdout F 	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316951959Z stdout F 	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316950509Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316949063Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316947661Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316946283Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316943935Z stdout F 	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.31692975Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316928293Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.31692686Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316925123Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1788)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.316918559Z stdout F org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 12:34:23.316	
 2026-02-26T07:04:23.31688667Z stdout F 2026-02-26 07:04:23.316 ERROR [main] o.s.b.SpringApplication: Application run failed 
2026-02-26 12:34:23.302	
 2026-02-26T07:04:23.302659116Z stdout F Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled. 
2026-02-26 12:34:23.302	
 2026-02-26T07:04:23.302655129Z stdout F 
2026-02-26 12:34:23.302	
 2026-02-26T07:04:23.302623936Z stdout F 2026-02-26 07:04:23.302 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger: 
2026-02-26 12:34:23.243	
 2026-02-26T07:04:23.243285505Z stdout F 2026-02-26 07:04:23.242 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat] 
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.225830611Z stdout F 2026-02-26 07:04:23.225 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided) 
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.22487607Z stdout F 2026-02-26 07:04:23.224 ERROR [main] o.s.o.j.AbstractEntityManagerFactoryBean: Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided) 
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224297226Z stdout F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224295709Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224294178Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224292704Z stdout F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224290791Z stdout F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224289265Z stdout F 	at com.fincore.NotificationService.NotificationServiceApplication.main(NotificationServiceApplication.java:18)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224287822Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224277405Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224275897Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224274476Z stdout F 	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224272965Z stdout F 	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224270786Z stdout F 	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224260882Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224259428Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224257891Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224256316Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.22425483Z stdout F 	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224253195Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224251735Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
2026-02-26 12:34:23.227	
 2026-02-26T07:04:23.224250156Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224248262Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224246622Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224244803Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224243269Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224241755Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224240191Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224238513Z stdout F 	at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.22423626Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224234885Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224233391Z stdout F 	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224231993Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224230622Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224228888Z stdout F 	at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224216776Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224214881Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224213538Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224212035Z stdout F 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224210391Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.22420836Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224206397Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:290)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224203652Z stdout F 	at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:116)
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224197397Z stdout F java.lang.NullPointerException: Cannot invoke "org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(java.sql.SQLException, String)" because the return value of "org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.sqlExceptionHelper()" is null
2026-02-26 12:34:23.224	
 2026-02-26T07:04:23.224160997Z stdout F 2026-02-26 07:04:23.221 WARN  [main] o.h.e.j.e.i.JdbcEnvironmentInitiator: HHH000342: Could not obtain connection to query metadata 
2026-02-26 12:34:16.411	
 2026-02-26T07:04:16.411062224Z stdout F 2026-02-26 07:04:16.410 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting... 
2026-02-26 12:34:16.310	
 2026-02-26T07:04:16.310768759Z stdout F 2026-02-26 07:04:16.310 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer 
2026-02-26 12:34:15.222	
 2026-02-26T07:04:15.222869519Z stdout F 2026-02-26 07:04:15.222 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled 
2026-02-26 12:34:15.118	
 2026-02-26T07:04:15.118798275Z stdout F 2026-02-26 07:04:15.118 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.5.2.Final 
2026-02-26 12:34:14.910	
 2026-02-26T07:04:14.910161339Z stdout F 2026-02-26 07:04:14.908 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default] 
2026-02-26 12:34:14.118	
 2026-02-26T07:04:14.11895729Z stdout F 2026-02-26 07:04:14.118 INFO  [main] o.s.b.w.s.RegistrationBean: Filter rbacFilterRegistration was not registered (disabled) 
2026-02-26 12:34:14.118	
 2026-02-26T07:04:14.118846296Z stdout F 2026-02-26 07:04:14.118 INFO  [main] o.s.b.w.s.RegistrationBean: Filter mdcFilterRegistration was not registered (disabled) 
2026-02-26 12:34:11.812	
 2026-02-26T07:04:11.812759753Z stdout F 2026-02-26 07:04:11.812 INFO  [main] o.s.b.w.s.c.ServletWebServerApplicationContext: Root WebApplicationContext: initialization completed in 8999 ms 
2026-02-26 12:34:11.812	
 2026-02-26T07:04:11.812411504Z stdout F 2026-02-26 07:04:11.811 INFO  [main] o.a.j.l.DirectJDKLog: Initializing Spring embedded WebApplicationContext 
2026-02-26 12:34:11.608	
 2026-02-26T07:04:11.608317235Z stdout F 2026-02-26 07:04:11.608 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.24] 
2026-02-26 12:34:11.608	
 2026-02-26T07:04:11.608087037Z stdout F 2026-02-26 07:04:11.607 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat] 
2026-02-26 12:34:11.606	
 2026-02-26T07:04:11.606363322Z stdout F 2026-02-26 07:04:11.605 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-9010"] 
2026-02-26 12:34:11.519	
 2026-02-26T07:04:11.519615379Z stdout F 2026-02-26 07:04:11.519 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 9010 (http) 
2026-02-26 12:34:07.810	
 2026-02-26T07:04:07.810723728Z stdout F 2026-02-26 07:04:07.810 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 7 ms. Found 0 Redis repository interfaces. 
2026-02-26 12:34:07.810	
 2026-02-26T07:04:07.810429807Z stdout F 2026-02-26 07:04:07.810 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository 
2026-02-26 12:34:07.809	
 2026-02-26T07:04:07.809113677Z stdout F 2026-02-26 07:04:07.808 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository 
2026-02-26 12:34:07.722	
 2026-02-26T07:04:07.721959372Z stdout F 2026-02-26 07:04:07.721 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode. 
2026-02-26 12:34:07.720	
 2026-02-26T07:04:07.720762584Z stdout F 2026-02-26 07:04:07.720 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode 
2026-02-26 12:34:07.705	
 2026-02-26T07:04:07.705555006Z stdout F 2026-02-26 07:04:07.705 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 506 ms. Found 2 JPA repository interfaces. 
2026-02-26 12:34:07.116	
 2026-02-26T07:04:07.116877919Z stdout F 2026-02-26 07:04:07.116 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode. 
2026-02-26 12:34:07.115	
 2026-02-26T07:04:07.115284392Z stdout F 2026-02-26 07:04:07.114 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode 
2026-02-26 12:34:02.705	
 2026-02-26T07:04:02.705295905Z stdout F 2026-02-26 07:04:02.704 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "dev" 
2026-02-26 12:34:02.704	
 2026-02-26T07:04:02.704276509Z stdout F 2026-02-26 07:04:02.703 DEBUG [main] o.s.b.StartupInfoLogger: Running with Spring Boot v3.3.0, Spring v6.1.8 
2026-02-26 12:34:02.698	
 2026-02-26T07:04:02.698843059Z stdout F 2026-02-26 07:04:02.697 INFO  [main] o.s.b.StartupInfoLogger: Starting NotificationServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /) 
