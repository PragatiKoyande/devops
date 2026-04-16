2026-04-16 13:14:19.673 WARN  [main] o.h.e.j.e.i.JdbcEnvironmentInitiator: HHH000342: Could not obtain connection to query metadata
java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.
        at com.zaxxer.hikari.HikariConfig.validate(HikariConfig.java:1032)
        at com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:108)
        at org.hibernate.engine.jdbc.connections.internal.DatasourceConnectionProviderImpl.getConnection(DatasourceConnectionProviderImpl.java:122)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator$ConnectionProviderJdbcConnectionAccess.obtainConnection(JdbcEnvironmentInitiator.java:437)
        at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:61)
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
        at com.fincore.DashboardService.DashboardServiceApplication.main(DashboardServiceApplication.java:12)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
{"@timestamp":"2026-04-16T18:44:19.673408949+05:30","level":"WARN","service":"DashboardService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.h.e.j.e.i.JdbcEnvironmentInitiator","message":"HHH000342: Could not obtain connection to query metadata","stack_trace":"java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.\n\tat com.zaxxer.hikari.HikariConfig.validate(HikariConfig.java:1032)\n\tat com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:108)\n\tat org.hibernate.engine.jdbc.connections.internal.DatasourceConnectionProviderImpl.getConnection(DatasourceConnectionProviderImpl.java:122)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator$ConnectionProviderJdbcConnectionAccess.obtainConnection(JdbcEnvironmentInitiator.java:437)\n\tat org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:61)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:290)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)\n\tat org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)\n\tat org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)\n"}
2026-04-16 13:14:19.688 WARN  [main] o.h.e.j.d.i.DialectFactoryImpl: HHH90000025: OracleDialect does not need to be specified explicitly using 'hibernate.dialect' (remove the property setting and it will be selected by default)
{"@timestamp":"2026-04-16T18:44:19.688240277+05:30","level":"WARN","service":"DashboardService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.hibernate.orm.deprecation","message":"HHH90000025: OracleDialect does not need to be specified explicitly using 'hibernate.dialect' (remove the property setting and it will be selected by default)","stack_trace":""}
2026-04-16 13:14:20.565 INFO  [main] o.h.e.t.j.p.i.JtaPlatformInitiator: HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)
{"@timestamp":"2026-04-16T18:44:20.565912436+05:30","level":"INFO","service":"DashboardService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.h.e.t.j.p.i.JtaPlatformInitiator","message":"HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)","stack_trace":""}
2026-04-16 13:14:20.579 ERROR [main] c.z.h.HikariConfig: HikariPool-1 - dataSource or dataSourceClassName or jdbcUrl is required.
{"@timestamp":"2026-04-16T18:44:20.5791241+05:30","level":"ERROR","service":"DashboardService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"com.zaxxer.hikari.HikariConfig","message":"HikariPool-1 - dataSource or dataSourceClassName or jdbcUrl is required.","stack_trace":""}
2026-04-16 13:14:20.581 ERROR [main] o.s.o.j.AbstractEntityManagerFactoryBean: Failed to initialize JPA EntityManagerFactory: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.
{"@timestamp":"2026-04-16T18:44:20.581160692+05:30","level":"ERROR","service":"DashboardService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.o.j.LocalContainerEntityManagerFactoryBean","message":"Failed to initialize JPA EntityManagerFactory: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.","stack_trace":""}
2026-04-16 13:14:20.581 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'oracleEntityManagerFactory' defined in class path resource [com/fincore/DashboardService/config/OracleDbConfig.class]: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.
{"@timestamp":"2026-04-16T18:44:20.581852622+05:30","level":"WARN","service":"DashboardService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.w.s.c.AnnotationConfigServletWebServerApplicationContext","message":"Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'oracleEntityManagerFactory' defined in class path resource [com/fincore/DashboardService/config/OracleDbConfig.class]: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.","stack_trace":""}
2026-04-16 13:14:20.593 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
{"@timestamp":"2026-04-16T18:44:20.59332548+05:30","level":"INFO","service":"DashboardService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.catalina.core.StandardService","message":"Stopping service [Tomcat]","stack_trace":""}
2026-04-16 13:14:20.722 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
{"@timestamp":"2026-04-16T18:44:20.722942405+05:30","level":"INFO","service":"DashboardService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.a.l.ConditionEvaluationReportLogger","message":"\n\nError starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.","stack_trace":""}
2026-04-16 13:14:20.739 ERROR [main] o.s.b.SpringApplication: Application run failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'oracleEntityManagerFactory' defined in class path resource [com/fincore/DashboardService/config/OracleDbConfig.class]: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.
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
        at com.fincore.DashboardService.DashboardServiceApplication.main(DashboardServiceApplication.java:12)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
Caused by: jakarta.persistence.PersistenceException: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:421)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
        ... 20 common frames omitted
Caused by: java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.
        at com.zaxxer.hikari.HikariConfig.validate(HikariConfig.java:1032)
        at com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:108)
        at org.hibernate.engine.jdbc.connections.internal.DatasourceConnectionProviderImpl.getConnection(DatasourceConnectionProviderImpl.java:122)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator$ConnectionProviderJdbcConnectionAccess.obtainConnection(JdbcEnvironmentInitiator.java:437)
        at org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:46)
        at org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:39)
        at org.hibernate.tool.schema.internal.exec.ImprovedExtractionContextImpl.getJdbcConnection(ImprovedExtractionContextImpl.java:63)
        at org.hibernate.tool.schema.extract.spi.ExtractionContext.getQueryResults(ExtractionContext.java:43)
        at org.hibernate.tool.schema.extract.internal.SequenceInformationExtractorLegacyImpl.extractMetadata(SequenceInformationExtractorLegacyImpl.java:39)
        at org.hibernate.tool.schema.extract.internal.DatabaseInformationImpl.initializeSequences(DatabaseInformationImpl.java:66)
        at org.hibernate.tool.schema.extract.internal.DatabaseInformationImpl.<init>(DatabaseInformationImpl.java:60)
        at org.hibernate.tool.schema.internal.Helper.buildDatabaseInformation(Helper.java:185)
        at org.hibernate.tool.schema.internal.AbstractSchemaMigrator.doMigration(AbstractSchemaMigrator.java:98)
        at org.hibernate.tool.schema.spi.SchemaManagementToolCoordinator.performDatabaseAction(SchemaManagementToolCoordinator.java:280)
        at org.hibernate.tool.schema.spi.SchemaManagementToolCoordinator.lambda$process$5(SchemaManagementToolCoordinator.java:144)
        at java.base/java.util.HashMap.forEach(HashMap.java:1429)
        at org.hibernate.tool.schema.spi.SchemaManagementToolCoordinator.process(SchemaManagementToolCoordinator.java:141)
        at org.hibernate.boot.internal.SessionFactoryObserverForSchemaExport.sessionFactoryCreated(SessionFactoryObserverForSchemaExport.java:37)
        at org.hibernate.internal.SessionFactoryObserverChain.sessionFactoryCreated(SessionFactoryObserverChain.java:35)
        at org.hibernate.internal.SessionFactoryImpl.<init>(SessionFactoryImpl.java:322)
        at org.hibernate.boot.internal.SessionFactoryBuilderImpl.build(SessionFactoryBuilderImpl.java:457)
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1506)
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409)
        ... 24 common frames omitted
{"@timestamp":"2026-04-16T18:44:20.739307481+05:30","level":"ERROR","service":"DashboardService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.springframework.boot.SpringApplication","message":"Application run failed","stack_trace":"org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'oracleEntityManagerFactory' defined in class path resource [com/fincore/DashboardService/config/OracleDbConfig.class]: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1788)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)\n\tat org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)\n\tat org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)\n\tat org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)\n\tat org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)\nCaused by: jakarta.persistence.PersistenceException: [PersistenceUnit: oracle] Unable to build Hibernate SessionFactory; nested exception is java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.\n\tat org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:421)\n\tat org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)\n\tat org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)\n\tat org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)\nCaused by: java.lang.IllegalArgumentException: dataSource or dataSourceClassName or jdbcUrl is required.\n\tat com.zaxxer.hikari.HikariConfig.validate(HikariConfig.java:1032)\n\tat com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:108)\n\tat org.hibernate.engine.jdbc.connections.internal.DatasourceConnectionProviderImpl.getConnection(DatasourceConnectionProviderImpl.java:122)\n\tat org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator$ConnectionProviderJdbcConnectionAccess.obtainConnection(JdbcEnvironmentInitiator.java:437)\n\tat org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:46)\n\tat org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:39)\n\tat org.hibernate.tool.schema.internal.exec.ImprovedExtractionContextImpl.getJdbcConnection(ImprovedExtractionContextImpl.java:63)\n\tat org.hibernate.tool.schema.extract.spi.ExtractionContext.getQueryResults(ExtractionContext.java:43)\n\tat org.hibernate.tool.schema.extract.internal.SequenceInformationExtractorLegacyImpl.extractMetadata(SequenceInformationExtractorLegacyImpl.java:39)\n\tat org.hibernate.tool.schema.extract.internal.DatabaseInformationImpl.initializeSequences(DatabaseInformationImpl.java:66)\n"}




Below is my manifest file :

apiVersion: apps/v1
kind: Deployment
metadata:
  name: dashboard-deployment
  namespace: be-test
spec:
  replicas: 1
  selector:
    matchLabels:
      app: dashboard-backend
  template:
    metadata:
      labels:
        app: dashboard-backend
    spec:
      containers:
      - name: dashboard-container
        image: h06vksharbor.corp.ad.sbi/cbops/dashboard-service:TS02
        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"        
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"       
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.179.46:1523/fincorepdb1"
          - name: SPRING_DATASOURCE_USERNAME			
            value: "fincore"		  
          - name: SPRING_DATASOURCE_PASSWORD			
            value: "Password#1234"             
        ports:
        - containerPort: 9015
        imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: dashboard-service
  namespace: be-test
spec:
  selector:
    app: dashboard-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9015
  type: ClusterIP


