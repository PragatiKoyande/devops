ne limit:
1000 reached, received logs cover 52.93% (7min 56sec) of your selected time range (15min)
Total bytes processed:
1.18 MB

Download
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913543535Z stdout F 	... 35 common frames omitted
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913541825Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913540422Z stdout F 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913538981Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913537548Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.91353601Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:362)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913534563Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentWithDefaults(JdbcEnvironmentInitiator.java:152)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913533025Z stdout F 	at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.buildDialect(DialectFactoryImpl.java:87)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913531576Z stdout F 	at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.determineDialect(DialectFactoryImpl.java:191)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913529844Z stdout F Caused by: org.hibernate.HibernateException: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913527614Z stdout F 	... 20 common frames omitted
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913525187Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913519477Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913517771Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913516376Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913514899Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913513267Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913508101Z stdout F 	at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913504587Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913490821Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913488882Z stdout F 	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.91348649Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913484378Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913482206Z stdout F 	at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913480038Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913478105Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913476139Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:276)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.91347412Z stdout F Caused by: org.hibernate.service.spi.ServiceException: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913471211Z stdout F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.91346894Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913466576Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913464536Z stdout F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913461585Z stdout F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913459533Z stdout F 	at com.fincore.NotificationService.NotificationServiceApplication.main(NotificationServiceApplication.java:18)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913457468Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913454851Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913452901Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913449749Z stdout F 	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913447442Z stdout F 	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913444439Z stdout F 	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913442183Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913439866Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913437662Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913435361Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913419999Z stdout F 	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913418199Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913416676Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913415216Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913413568Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1788)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913410111Z stdout F org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 15:29:27.913	
 2026-02-26T09:59:27.913380255Z stdout F 2026-02-26 09:59:27.912 ERROR [main] o.s.b.SpringApplication: Application run failed 
2026-02-26 15:29:27.898	
 2026-02-26T09:59:27.898204188Z stdout F Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled. 
2026-02-26 15:29:27.898	
 2026-02-26T09:59:27.898201104Z stdout F 
2026-02-26 15:29:27.898	
 2026-02-26T09:59:27.898161955Z stdout F 2026-02-26 09:59:27.897 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger: 
2026-02-26 15:29:27.829	
 2026-02-26T09:59:27.828935624Z stdout F 2026-02-26 09:59:27.828 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat] 
2026-02-26 15:29:27.815	
 2026-02-26T09:59:27.815200246Z stdout F 2026-02-26 09:59:27.815 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided) 
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.81456032Z stdout F 2026-02-26 09:59:27.814 ERROR [main] o.s.o.j.AbstractEntityManagerFactoryBean: Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided) 
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813988443Z stdout F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813986967Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.81398509Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813983625Z stdout F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813981423Z stdout F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813979977Z stdout F 	at com.fincore.NotificationService.NotificationServiceApplication.main(NotificationServiceApplication.java:18)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813978249Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.81397414Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813972681Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813971171Z stdout F 	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813969529Z stdout F 	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.81396687Z stdout F 	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
2026-02-26 15:29:27.814	
 2026-02-26T09:59:27.813954151Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813952497Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813950874Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813949149Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813947738Z stdout F 	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813946282Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813944761Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813943397Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.81394188Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813940385Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813938741Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813937134Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813935649Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813934185Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813932568Z stdout F 	at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813930546Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813929046Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813926973Z stdout F 	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.81392549Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813923948Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813922337Z stdout F 	at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.81390378Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813901585Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813900162Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813898762Z stdout F 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813897445Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813895843Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.81389386Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:290)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813891735Z stdout F 	at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:116)
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813888252Z stdout F java.lang.NullPointerException: Cannot invoke "org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(java.sql.SQLException, String)" because the return value of "org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.sqlExceptionHelper()" is null
2026-02-26 15:29:27.813	
 2026-02-26T09:59:27.813846376Z stdout F 2026-02-26 09:59:27.811 WARN  [main] o.h.e.j.e.i.JdbcEnvironmentInitiator: HHH000342: Could not obtain connection to query metadata 
2026-02-26 15:29:21.026	
 2026-02-26T09:59:21.026620957Z stdout F 2026-02-26 09:59:21.026 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting... 
2026-02-26 15:29:21.002	
 2026-02-26T09:59:21.002157668Z stdout F 2026-02-26 09:59:21.001 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer 
2026-02-26 15:29:19.911	
 2026-02-26T09:59:19.911630951Z stdout F 2026-02-26 09:59:19.911 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled 
2026-02-26 15:29:19.808	
 2026-02-26T09:59:19.808452254Z stdout F 2026-02-26 09:59:19.807 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.5.2.Final 
2026-02-26 15:29:19.613	
 2026-02-26T09:59:19.613678829Z stdout F 2026-02-26 09:59:19.608 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default] 
2026-02-26 15:29:18.903	
 2026-02-26T09:59:18.903387414Z stdout F 2026-02-26 09:59:18.903 INFO  [main] o.s.b.w.s.RegistrationBean: Filter rbacFilterRegistration was not registered (disabled) 
2026-02-26 15:29:18.903	
 2026-02-26T09:59:18.903232854Z stdout F 2026-02-26 09:59:18.902 INFO  [main] o.s.b.w.s.RegistrationBean: Filter mdcFilterRegistration was not registered (disabled) 
2026-02-26 15:29:16.709	
 2026-02-26T09:59:16.709370109Z stdout F 2026-02-26 09:59:16.709 INFO  [main] o.s.b.w.s.c.ServletWebServerApplicationContext: Root WebApplicationContext: initialization completed in 8803 ms 
2026-02-26 15:29:16.709	
 2026-02-26T09:59:16.709006157Z stdout F 2026-02-26 09:59:16.708 INFO  [main] o.a.j.l.DirectJDKLog: Initializing Spring embedded WebApplicationContext 
2026-02-26 15:29:16.421	
 2026-02-26T09:59:16.421666532Z stdout F 2026-02-26 09:59:16.421 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.24] 
2026-02-26 15:29:16.421	
 2026-02-26T09:59:16.42163498Z stdout F 2026-02-26 09:59:16.421 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat] 
2026-02-26 15:29:16.419	
 2026-02-26T09:59:16.419796476Z stdout F 2026-02-26 09:59:16.419 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-9010"] 
2026-02-26 15:29:16.411	
 2026-02-26T09:59:16.411324835Z stdout F 2026-02-26 09:59:16.410 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 9010 (http) 
2026-02-26 15:29:12.813	
 2026-02-26T09:59:12.81358637Z stdout F 2026-02-26 09:59:12.813 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 5 ms. Found 0 Redis repository interfaces. 
2026-02-26 15:29:12.813	
 2026-02-26T09:59:12.813376044Z stdout F 2026-02-26 09:59:12.813 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository 
2026-02-26 15:29:12.812	
 2026-02-26T09:59:12.812434499Z stdout F 2026-02-26 09:59:12.812 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository 
2026-02-26 15:29:12.800	
 2026-02-26T09:59:12.800499142Z stdout F 2026-02-26 09:59:12.800 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode. 
2026-02-26 15:29:12.799	
 2026-02-26T09:59:12.799215855Z stdout F 2026-02-26 09:59:12.798 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode 
2026-02-26 15:29:12.703	
 2026-02-26T09:59:12.70374639Z stdout F 2026-02-26 09:59:12.703 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 492 ms. Found 2 JPA repository interfaces. 
2026-02-26 15:29:12.202	
 2026-02-26T09:59:12.202540585Z stdout F 2026-02-26 09:59:12.202 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode. 
2026-02-26 15:29:12.200	
 2026-02-26T09:59:12.200589747Z stdout F 2026-02-26 09:59:12.200 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode 
2026-02-26 15:29:07.703	
 2026-02-26T09:59:07.703362025Z stdout F 2026-02-26 09:59:07.703 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "dev" 
2026-02-26 15:29:07.702	
 2026-02-26T09:59:07.7025779Z stdout F 2026-02-26 09:59:07.702 DEBUG [main] o.s.b.StartupInfoLogger: Running with Spring Boot v3.3.0, Spring v6.1.8 
2026-02-26 15:29:07.615	
 2026-02-26T09:59:07.615824443Z stdout F 2026-02-26 09:59:07.614 INFO  [main] o.s.b.StartupInfoLogger: Starting NotificationServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /) 
2026-02-26 15:29:07.400	
 2026-02-26T09:59:07.40049981Z stdout F 
2026-02-26 15:29:07.400	
 2026-02-26T09:59:07.400468149Z stdout F  :: Spring Boot ::                (v3.3.0)
2026-02-26 15:29:07.202	
 2026-02-26T09:59:07.202361858Z stdout F 
2026-02-26 15:29:07.202	
 2026-02-26T09:59:07.202360386Z stdout F  =========|_|==============|___/=/_/_/_/
2026-02-26 15:29:07.202	
 2026-02-26T09:59:07.202358788Z stdout F   '  |____| .__|_| |_|_| |_\__, | / / / /
2026-02-26 15:29:07.202	
 2026-02-26T09:59:07.20235733Z stdout F  \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
2026-02-26 15:29:07.202	
 2026-02-26T09:59:07.20235561Z stdout F ( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
2026-02-26 15:29:07.202	
 2026-02-26T09:59:07.202352719Z stdout F  /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
2026-02-26 15:29:07.202	
 2026-02-26T09:59:07.202297004Z stdout F   .   ____          _            __ _ _
2026-02-26 15:28:37.619	
 2026-02-26T09:58:37.618810011Z stdout F 	... 35 common frames omitted
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618807893Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618805956Z stdout F 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618803611Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618801424Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.6187969Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:362)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618794754Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentWithDefaults(JdbcEnvironmentInitiator.java:152)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618792733Z stdout F 	at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.buildDialect(DialectFactoryImpl.java:87)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.61879086Z stdout F 	at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.determineDialect(DialectFactoryImpl.java:191)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618788843Z stdout F Caused by: org.hibernate.HibernateException: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618785927Z stdout F 	... 20 common frames omitted
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618784018Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618782591Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618781103Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618779758Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618778354Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618776736Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618767946Z stdout F 	at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618765611Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618753175Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618751777Z stdout F 	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618750484Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618749071Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618747515Z stdout F 	at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618746187Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618744638Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618743064Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:276)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618741553Z stdout F Caused by: org.hibernate.service.spi.ServiceException: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.61873826Z stdout F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.61873676Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618735122Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618733614Z stdout F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618731571Z stdout F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618730017Z stdout F 	at com.fincore.NotificationService.NotificationServiceApplication.main(NotificationServiceApplication.java:18)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618727948Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618726309Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618724634Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618722688Z stdout F 	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618721193Z stdout F 	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618718755Z stdout F 	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618717026Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618715644Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618714186Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618712675Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618710138Z stdout F 	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618697386Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618695637Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618694202Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618692383Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1788)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618688422Z stdout F org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-02-26 15:28:37.618	
 2026-02-26T09:58:37.618653019Z stdout F 2026-02-26 09:58:37.618 ERROR [main] o.s.b.SpringApplication: Application run failed 
2026-02-26 15:28:37.604	
 2026-02-26T09:58:37.604658772Z stdout F Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled. 
2026-02-26 15:28:37.604	
 2026-02-26T09:58:37.604653851Z stdout F 
2026-02-26 15:28:37.604	
 2026-02-26T09:58:37.604625144Z stdout F 2026-02-26 09:58:37.604 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger: 
2026-02-26 15:28:37.551	
 2026-02-26T09:58:37.55186146Z stdout F 2026-02-26 09:58:37.551 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat] 
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.538929281Z stdout F 2026-02-26 09:58:37.538 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided) 
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.538271676Z stdout F 2026-02-26 09:58:37.538 ERROR [main] o.s.o.j.AbstractEntityManagerFactoryBean: Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided) 
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537881953Z stdout F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537880574Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537879151Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537877602Z stdout F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537875591Z stdout F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537874193Z stdout F 	at com.fincore.NotificationService.NotificationServiceApplication.main(NotificationServiceApplication.java:18)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537872657Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537869079Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537867664Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537866206Z stdout F 	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.53786465Z stdout F 	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537861582Z stdout F 	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537848498Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537847152Z stdout F 	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537845641Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537844233Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537842843Z stdout F 	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537840915Z stdout F 	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
2026-02-26 15:28:37.538	
 2026-02-26T09:58:37.537839332Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537837595Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537835849Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537833998Z stdout F 	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537832539Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537831126Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.53782953Z stdout F 	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.53782788Z stdout F 	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537826344Z stdout F 	at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537824401Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537822917Z stdout F 	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537821357Z stdout F 	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537819858Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537818502Z stdout F 	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537816906Z stdout F 	at org.hibernate.boot.model.relational.Database.<init>(Database.java:45)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537799897Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537797243Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.53779545Z stdout F 	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537794017Z stdout F 	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537792655Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537791126Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537789469Z stdout F 	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:290)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537786829Z stdout F 	at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:116)
2026-02-26 15:28:37.537	
 2026-02-26T09:58:37.537782443Z stdout F java.lang.NullPointerException: Cannot invoke "org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(java.sql.SQLException, String)" because the return value of "org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.sqlExceptionHelper()" is null
