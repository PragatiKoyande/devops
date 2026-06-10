Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
{"@timestamp":"2026-06-10T12:02:53.559534469+05:30","level":"INFO","service":"HelpService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.s.b.a.l.ConditionEvaluationReportLogger","message":"\n\nError starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.","stack_trace":""}
2026-06-10 06:32:53.582 ERROR [main] o.s.b.SpringApplication: Application run failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: [PersistenceUnit: default] Unable to build Hibernate SessionFactory; nested exception is org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)] [n/a]
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
        at com.fincore.helpservice.HelpServiceApplication.main(HelpServiceApplication.java:12)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
Caused by: jakarta.persistence.PersistenceException: [PersistenceUnit: default] Unable to build Hibernate SessionFactory; nested exception is org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)] [n/a]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:421)
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)
        ... 20 common frames omitted
Caused by: org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)] [n/a]
        at org.hibernate.exception.internal.SQLStateConversionDelegate.convert(SQLStateConversionDelegate.java:100)
        at org.hibernate.exception.internal.StandardSQLExceptionConverter.convert(StandardSQLExceptionConverter.java:58)
        at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:108)
        at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:94)
        at org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:74)
        at org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:39)
        at org.hibernate.tool.schema.internal.exec.ImprovedExtractionContextImpl.getJdbcConnection(ImprovedExtractionContextImpl.java:63)
        at org.hibernate.tool.schema.extract.spi.ExtractionContext.getQueryResults(ExtractionContext.java:43)
        at org.hibernate.tool.schema.extract.internal.SequenceInformationExtractorLegacyImpl.extractMetadata(SequenceInformationExtractorLegacyImpl.java:39)
        at org.hibernate.tool.schema.extract.internal.DatabaseInformationImpl.initializeSequences(DatabaseInformationImpl.java:66)
        at org.hibernate.tool.schema.extract.internal.DatabaseInformationImpl.<init>(DatabaseInformationImpl.java:60)
        at org.hibernate.tool.schema.internal.Helper.buildDatabaseInformation(Helper.java:185)
        at org.hibernate.tool.schema.internal.AbstractSchemaValidator.doValidation(AbstractSchemaValidator.java:68)
        at org.hibernate.tool.schema.spi.SchemaManagementToolCoordinator.performDatabaseAction(SchemaManagementToolCoordinator.java:289)
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
Caused by: java.sql.SQLRecoverableException: IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)
        at oracle.jdbc.driver.T4CConnection.handleLogonNetException(T4CConnection.java:902)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:707)
        at oracle.jdbc.driver.PhysicalConnection.connect(PhysicalConnection.java:1094)
        at oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:89)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:732)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:648)
        at com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:137)
        at com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:360)
        at com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:202)
        at com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:461)
        at com.zaxxer.hikari.pool.HikariPool.checkFailFast(HikariPool.java:550)
        at com.zaxxer.hikari.pool.HikariPool.<init>(HikariPool.java:98)
        at com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:111)
        at org.hibernate.engine.jdbc.connections.internal.DatasourceConnectionProviderImpl.getConnection(DatasourceConnectionProviderImpl.java:122)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator$ConnectionProviderJdbcConnectionAccess.obtainConnection(JdbcEnvironmentInitiator.java:437)
        at org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:46)
        ... 44 common frames omitted
Caused by: oracle.net.ns.NetException: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)
        at oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:715)
        at oracle.net.resolver.AddrResolution.resolveAndExecute(AddrResolution.java:584)
        at oracle.net.ns.NSProtocol.establishConnection(NSProtocol.java:964)
        at oracle.net.ns.NSProtocol.connect(NSProtocol.java:350)
        at oracle.jdbc.driver.T4CConnection.connect(T4CConnection.java:2627)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:666)
        ... 58 common frames omitted
Caused by: java.io.IOException: Socket read timed out, socket connect lapse 30000 ms. 10.177.179.85 1523  30000 (1/1) true
        at oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:403)
        at oracle.net.nt.TcpNTAdapter.doLocalDNSLookupConnect(TcpNTAdapter.java:307)
        at oracle.net.nt.TcpNTAdapter.connect(TcpNTAdapter.java:269)
        at oracle.net.nt.ConnOption.connect(ConnOption.java:230)
        at oracle.net.nt.ConnStrategy.executeConnOption(ConnStrategy.java:1014)
        at oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:673)
        ... 63 common frames omitted
Caused by: oracle.net.nt.TimeoutInterruptHandler$IOReadTimeoutException: Socket read timed out
        at oracle.net.nt.TimeoutSocketChannel.handleInterrupt(TimeoutSocketChannel.java:543)
        at oracle.net.nt.TimeoutSocketChannel.connect(TimeoutSocketChannel.java:196)
        at oracle.net.nt.TimeoutSocketChannel.<init>(TimeoutSocketChannel.java:157)
        at oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:384)
        ... 68 common frames omitted
{"@timestamp":"2026-06-10T12:02:53.582057444+05:30","level":"ERROR","service":"HelpService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.springframework.boot.SpringApplication","message":"Application run failed","stack_trace":"org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: [PersistenceUnit: default] Unable to build Hibernate SessionFactory; nested exception is org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)] [n/a]\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1788)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)\n\tat org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205)\n\tat org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952)\n\tat org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)\n\tat org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)\nCaused by: jakarta.persistence.PersistenceException: [PersistenceUnit: default] Unable to build Hibernate SessionFactory; nested exception is org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)] [n/a]\n\tat org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:421)\n\tat org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396)\n\tat org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)\n\tat org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)\n\tat org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)\n\tat org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)\nCaused by: org.hibernate.exception.JDBCConnectionException: Unable to open JDBC Connection for DDL execution [IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)] [n/a]\n\tat org.hibernate.exception.internal.SQLStateConversionDelegate.convert(SQLStateConversionDelegate.java:100)\n\tat org.hibernate.exception.internal.StandardSQLExceptionConverter.convert(StandardSQLExceptionConverter.java:58)\n\tat org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:108)\n\tat org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:94)\n\tat org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:74)\n\tat org.hibernate.resource.transaction.backend.jdbc.internal.DdlTransactionIsolatorNonJtaImpl.getIsolatedConnection(DdlTransactionIsolatorNonJtaImpl.java:39)\n\tat org.hibernate.tool.schema.internal.exec.ImprovedExtractionContextImpl.getJdbcConnection(ImprovedExtractionContextImpl.java:63)\n\tat org.hibernate.tool.schema.extract.spi.ExtractionContext.getQueryResults(ExtractionContext.java:43)\n\tat org.hibernate.tool.schema.extract.internal.SequenceInformationExtractorLegacyImpl.extractMetadata(SequenceInformationExtractorLegacyImpl.java:39)\n\tat org.hibernate.tool.schema.extract.internal.DatabaseInformationImpl.initializeSequences(DatabaseInformationImpl.java:66)\nCaused by: java.sql.SQLRecoverableException: IO Error: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)\n\tat oracle.jdbc.driver.T4CConnection.handleLogonNetException(T4CConnection.java:902)\n\tat oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:707)\n\tat oracle.jdbc.driver.PhysicalConnection.connect(PhysicalConnection.java:1094)\n\tat oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:89)\n\tat oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:732)\n\tat oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:648)\n\tat com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:137)\n\tat com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:360)\n\tat com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:202)\n\tat com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:461)\nCaused by: oracle.net.ns.NetException: The Network Adapter could not establish the connection (CONNECTION_ID=hbaSNaV9SKmqUSODin4HDg==)\n\tat oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:715)\n\tat oracle.net.resolver.AddrResolution.resolveAndExecute(AddrResolution.java:584)\n\tat oracle.net.ns.NSProtocol.establishConnection(NSProtocol.java:964)\n\tat oracle.net.ns.NSProtocol.connect(NSProtocol.java:350)\n\tat oracle.jdbc.driver.T4CConnection.connect(T4CConnection.java:2627)\n\tat oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:666)\n\tat oracle.jdbc.driver.PhysicalConnection.connect(PhysicalConnection.java:1094)\n\tat oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:89)\n\tat oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:732)\n\tat oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:648)\nCaused by: java.io.IOException: Socket read timed out, socket connect lapse 30000 ms. 10.177.179.85 1523  30000 (1/1) true\n\tat oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:403)\n\tat oracle.net.nt.TcpNTAdapter.doLocalDNSLookupConnect(TcpNTAdapter.java:307)\n\tat oracle.net.nt.TcpNTAdapter.connect(TcpNTAdapter.java:269)\n\tat oracle.net.nt.ConnOption.connect(ConnOption.java:230)\n\tat oracle.net.nt.ConnStrategy.executeConnOption(ConnStrategy.java:1014)\n\tat oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:673)\n\tat oracle.net.resolver.AddrResolution.resolveAndExecute(AddrResolution.java:584)\n\tat oracle.net.ns.NSProtocol.establishConnection(NSProtocol.java:964)\n\tat oracle.net.ns.NSProtocol.connect(NSProtocol.java:350)\n\tat oracle.jdbc.driver.T4CConnection.connect(T4CConnection.java:2627)\nCaused by: oracle.net.nt.TimeoutInterruptHandler$IOReadTimeoutException: Socket read timed out\n\tat oracle.net.nt.TimeoutSocketChannel.handleInterrupt(TimeoutSocketChannel.java:543)\n\tat oracle.net.nt.TimeoutSocketChannel.connect(TimeoutSocketChannel.java:196)\n\tat oracle.net.nt.TimeoutSocketChannel.<init>(TimeoutSocketChannel.java:157)\n\tat oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:384)\n\tat oracle.net.nt.TcpNTAdapter.doLocalDNSLookupConnect(TcpNTAdapter.java:307)\n\tat oracle.net.nt.TcpNTAdapter.connect(TcpNTAdapter.java:269)\n\tat oracle.net.nt.ConnOption.connect(ConnOption.java:230)\n\tat oracle.net.nt.ConnStrategy.executeConnOption(ConnStrategy.java:1014)\n\tat oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:673)\n\tat oracle.net.resolver.AddrResolution.resolveAndExecute(AddrResolution.java:584)\n"}





this issue I m getting although i have craeted this below networkpolicy 

apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-help-service-egress-to-oracle-db
  namespace: backend
spec:
  podSelector:
    matchLabels:
      app: help-service-backend

  policyTypes:
  - Egress

  egress:
  - to:
    - ipBlock:
        cidr: 10.177.179.85/32
    ports:
    - protocol: TCP
      port: 1523
