2026-02-24 :: 07:07:12.712 || INFO :: SecurityConfig.java: | 86 | :: RedisValidationFilter invoked for path=/api/auth/check-user
2026-02-24 :: 07:07:12.712 || INFO :: LoginUtility.java: | 12 | :: X-Forwarded-For ip : null
2026-02-24 :: 07:07:12.713 || INFO :: AuthController.java: | 137 | :: Check-User info user id: 2222222 , ip : /10.0.19.45:53854
2026-02-24 :: 07:07:42.713 || WARN :: SqlExceptionHelper.java: | 145 | :: SQL Error: 257, SQLState: 64000
2026-02-24 :: 07:07:42.713 || ERROR:: SqlExceptionHelper.java: | 150 | :: HikariPool-1 - Connection is not available, request timed out after 30000ms (total=0, active=0, idle=0, waiting=0)
2026-02-24 :: 07:07:42.713 || ERROR:: SqlExceptionHelper.java: | 150 | :: ORA-00257: Archiver error. Connect AS SYSDBA only until resolved.

https://docs.oracle.com/error-help/db/ora-00257/
2026-02-24 :: 07:07:42.714 || ERROR:: GlobalExceptionHandler.java: | 56 | :: System Error
org.springframework.transaction.CannotCreateTransactionException: Could not open JPA EntityManager for transaction
        at org.springframework.orm.jpa.JpaTransactionManager.doBegin(JpaTransactionManager.java:466)
        Suppressed: reactor.core.publisher.FluxOnAssembly$OnAssemblyException:
Error has been observed at the following site(s):
        *__checkpoint ⇢ Handler com.fincore.gateway.Controller.AuthController#checkUser(ServerHttpRequest, Map) [DispatcherHandler]
Original Stack Trace:
                at org.springframework.orm.jpa.JpaTransactionManager.doBegin(JpaTransactionManager.java:466)
                at org.springframework.transaction.support.AbstractPlatformTransactionManager.startTransaction(AbstractPlatformTransactionManager.java:532)
                at org.springframework.transaction.support.AbstractPlatformTransactionManager.getTransaction(AbstractPlatformTransactionManager.java:405)
                at org.springframework.transaction.interceptor.TransactionAspectSupport.createTransactionIfNecessary(TransactionAspectSupport.java:639)
                at org.springframework.transaction.interceptor.TransactionAspectSupport.invokeWithinTransaction(TransactionAspectSupport.java:374)
                at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:119)
                at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
                at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:728)
                at com.fincore.gateway.Service.LoginServiceImpl$$SpringCGLIB$$0.checkUser(<generated>)
                at com.fincore.gateway.Controller.AuthController.lambda$checkUser$0(AuthController.java:151)
                at reactor.core.publisher.MonoCallable.call(MonoCallable.java:72)
                at reactor.core.publisher.FluxSubscribeOnCallable$CallableSubscribeOnSubscription.run(FluxSubscribeOnCallable.java:228)
                at reactor.core.scheduler.SchedulerTask.call(SchedulerTask.java:68)
                at reactor.core.scheduler.SchedulerTask.call(SchedulerTask.java:28)
                at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:317)
                at java.base/java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:304)
                at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1144)
                at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:642)
                at java.base/java.lang.Thread.run(Thread.java:1570)
Caused by: org.hibernate.exception.JDBCConnectionException: Unable to acquire JDBC Connection [HikariPool-1 - Connection is not available, request timed out after 30000ms (total=0, active=0, idle=0, waiting=0)] [n/a]
        at org.hibernate.exception.internal.SQLExceptionTypeDelegate.convert(SQLExceptionTypeDelegate.java:51)
        at org.hibernate.exception.internal.StandardSQLExceptionConverter.convert(StandardSQLExceptionConverter.java:58)
        at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:108)
        at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:94)
        at org.hibernate.resource.jdbc.internal.LogicalConnectionManagedImpl.acquireConnectionIfNeeded(LogicalConnectionManagedImpl.java:129)
        at org.hibernate.resource.jdbc.internal.LogicalConnectionManagedImpl.getPhysicalConnection(LogicalConnectionManagedImpl.java:156)
        at org.springframework.orm.jpa.vendor.HibernateJpaDialect.beginTransaction(HibernateJpaDialect.java:164)
        at org.springframework.orm.jpa.JpaTransactionManager.doBegin(JpaTransactionManager.java:420)
        at org.springframework.transaction.support.AbstractPlatformTransactionManager.startTransaction(AbstractPlatformTransactionManager.java:532)
        at org.springframework.transaction.support.AbstractPlatformTransactionManager.getTransaction(AbstractPlatformTransactionManager.java:405)
        at org.springframework.transaction.interceptor.TransactionAspectSupport.createTransactionIfNecessary(TransactionAspectSupport.java:639)
        at org.springframework.transaction.interceptor.TransactionAspectSupport.invokeWithinTransaction(TransactionAspectSupport.java:374)
        at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:119)
        at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
        at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:728)
        at com.fincore.gateway.Service.LoginServiceImpl$$SpringCGLIB$$0.checkUser(<generated>)
        at com.fincore.gateway.Controller.AuthController.lambda$checkUser$0(AuthController.java:151)
        at reactor.core.publisher.MonoCallable.call(MonoCallable.java:72)
        at reactor.core.publisher.FluxSubscribeOnCallable$CallableSubscribeOnSubscription.run(FluxSubscribeOnCallable.java:228)
        at reactor.core.scheduler.SchedulerTask.call(SchedulerTask.java:68)
        at reactor.core.scheduler.SchedulerTask.call(SchedulerTask.java:28)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:317)
        at java.base/java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:304)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1144)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:642)
        at java.base/java.lang.Thread.run(Thread.java:1570)
Caused by: java.sql.SQLTransientConnectionException: HikariPool-1 - Connection is not available, request timed out after 30000ms (total=0, active=0, idle=0, waiting=0)
        at com.zaxxer.hikari.pool.HikariPool.createTimeoutException(HikariPool.java:714)
        at com.zaxxer.hikari.pool.HikariPool.getConnection(HikariPool.java:184)
        at com.zaxxer.hikari.pool.HikariPool.getConnection(HikariPool.java:142)
        at com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:127)
        at org.hibernate.engine.jdbc.connections.internal.DatasourceConnectionProviderImpl.getConnection(DatasourceConnectionProviderImpl.java:126)
        at org.hibernate.internal.NonContextualJdbcConnectionAccess.obtainConnection(NonContextualJdbcConnectionAccess.java:46)
        at org.hibernate.resource.jdbc.internal.LogicalConnectionManagedImpl.acquireConnectionIfNeeded(LogicalConnectionManagedImpl.java:126)
        ... 21 common frames omitted
Caused by: java.sql.SQLException: ORA-00257: Archiver error. Connect AS SYSDBA only until resolved.

https://docs.oracle.com/error-help/db/ora-00257/
        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:715)
        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:610)
        at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:605)
        at oracle.jdbc.driver.T4CTTIoauthenticate.processError(T4CTTIoauthenticate.java:932)
        at oracle.jdbc.driver.T4CTTIfun.receive(T4CTTIfun.java:969)
        at oracle.jdbc.driver.T4CTTIfun.doRPC(T4CTTIfun.java:237)
        at oracle.jdbc.driver.T4CTTIoauthenticate.doOSESSKEY(T4CTTIoauthenticate.java:859)
        at oracle.jdbc.driver.T4CConnection.authenticateWithPassword(T4CConnection.java:2277)
        at oracle.jdbc.driver.T4CConnection.authenticateUserForLogon(T4CConnection.java:2231)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:1155)
        at oracle.jdbc.driver.PhysicalConnection.connect(PhysicalConnection.java:1189)
        at oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:106)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:887)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:694)
        at com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:144)
        at com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:368)
        at com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:205)
        at com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:488)
        at com.zaxxer.hikari.pool.HikariPool$PoolEntryCreator.call(HikariPool.java:752)
        at com.zaxxer.hikari.pool.HikariPool$PoolEntryCreator.call(HikariPool.java:731)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:317)
        ... 3 common frames omitted



getting thios error
