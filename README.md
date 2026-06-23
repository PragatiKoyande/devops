
com.fincore.VoucherService.Exception.CustomExceptions$RedisOperationException: Failed to cache large dataset
        at com.fincore.VoucherService.Service.validation.ValidationStateManager.saveRowsToRedis(ValidationStateManager.java:136) ~[!/:0.0.1-SNAPSHOT]
        at com.fincore.VoucherService.Service.validation.VoucherBulkValidationService.completeRequest(VoucherBulkValidationService.java:304) ~[!/:0.0.1-SNAPSHOT]
        at com.fincore.VoucherService.Service.validation.VoucherBulkValidationService.processAsync(VoucherBulkValidationService.java:244) ~[!/:0.0.1-SNAPSHOT]
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
        at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
        at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:354) ~[spring-aop-6.1.8.jar!/:6.1.8]
        at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:196) ~[spring-aop-6.1.8.jar!/:6.1.8]
        at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:163) ~[spring-aop-6.1.8.jar!/:6.1.8]
        at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.proceed(CglibAopProxy.java:768) ~[spring-aop-6.1.8.jar!/:6.1.8]
        at org.springframework.aop.interceptor.AsyncExecutionInterceptor.lambda$invoke$0(AsyncExecutionInterceptor.java:113) ~[spring-aop-6.1.8.jar!/:6.1.8]
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:317) ~[na:na]
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1144) ~[na:na]
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:642) ~[na:na]
        at java.base/java.lang.Thread.run(Thread.java:1570) ~[na:na]
Caused by: org.springframework.data.redis.RedisConnectionFailureException: Unable to connect to Redis
        at org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory$ExceptionTranslatingConnectionProvider.translateException(LettuceConnectionFactory.java:1847) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory$ExceptionTranslatingConnectionProvider.getConnection(LettuceConnectionFactory.java:1778) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory$SharedConnection.getNativeConnection(LettuceConnectionFactory.java:1580) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory$SharedConnection.lambda$getConnection$0(LettuceConnectionFactory.java:1560) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory.doInLock(LettuceConnectionFactory.java:1521) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory$SharedConnection.getConnection(LettuceConnectionFactory.java:1557) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory.getSharedConnection(LettuceConnectionFactory.java:1243) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory.getConnection(LettuceConnectionFactory.java:1049) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.core.RedisConnectionUtils.fetchConnection(RedisConnectionUtils.java:195) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.core.RedisConnectionUtils.doGetConnection(RedisConnectionUtils.java:144) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.core.RedisConnectionUtils.getConnection(RedisConnectionUtils.java:105) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.core.RedisTemplate.execute(RedisTemplate.java:383) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.core.RedisTemplate.execute(RedisTemplate.java:363) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.core.AbstractOperations.execute(AbstractOperations.java:97) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.core.DefaultValueOperations.set(DefaultValueOperations.java:253) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at com.fincore.VoucherService.Service.validation.ValidationStateManager.saveRowsToRedis(ValidationStateManager.java:125) ~[!/:0.0.1-SNAPSHOT]
        ... 13 common frames omitted
Caused by: io.lettuce.core.RedisConnectionException: Unable to connect to redis-service/<unresolved>:6379
        at io.lettuce.core.RedisConnectionException.create(RedisConnectionException.java:78) ~[lettuce-core-6.3.2.RELEASE.jar!/:6.3.2.RELEASE/8941aea]
        at io.lettuce.core.RedisConnectionException.create(RedisConnectionException.java:56) ~[lettuce-core-6.3.2.RELEASE.jar!/:6.3.2.RELEASE/8941aea]
        at io.lettuce.core.AbstractRedisClient.getConnection(AbstractRedisClient.java:350) ~[lettuce-core-6.3.2.RELEASE.jar!/:6.3.2.RELEASE/8941aea]
        at io.lettuce.core.RedisClient.connect(RedisClient.java:215) ~[lettuce-core-6.3.2.RELEASE.jar!/:6.3.2.RELEASE/8941aea]
        at org.springframework.data.redis.connection.lettuce.StandaloneConnectionProvider.lambda$getConnection$1(StandaloneConnectionProvider.java:112) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at java.base/java.util.Optional.orElseGet(Optional.java:364) ~[na:na]
        at org.springframework.data.redis.connection.lettuce.StandaloneConnectionProvider.getConnection(StandaloneConnectionProvider.java:112) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        at org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory$ExceptionTranslatingConnectionProvider.getConnection(LettuceConnectionFactory.java:1776) ~[spring-data-redis-3.3.0.jar!/:3.3.0]
        ... 27 common frames omitted
Caused by: io.netty.resolver.dns.DnsResolveContext$SearchDomainUnknownHostException: Failed to resolve 'redis-service' [A(1)] and search domain query for configured domains failed as well: [cbops.svc.cluster.local, svc.cluster.local, cluster.local]
        at io.netty.resolver.dns.DnsResolveContext.finishResolve(DnsResolveContext.java:1151) ~[netty-resolver-dns-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.resolver.dns.DnsResolveContext.tryToFinishResolve(DnsResolveContext.java:1098) ~[netty-resolver-dns-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.resolver.dns.DnsResolveContext.query(DnsResolveContext.java:457) ~[netty-resolver-dns-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.resolver.dns.DnsResolveContext.access$700(DnsResolveContext.java:69) ~[netty-resolver-dns-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.resolver.dns.DnsResolveContext$2.operationComplete(DnsResolveContext.java:526) ~[netty-resolver-dns-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.DefaultPromise.notifyListener0(DefaultPromise.java:590) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.DefaultPromise.notifyListeners0(DefaultPromise.java:583) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.DefaultPromise.notifyListenersNow(DefaultPromise.java:559) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.DefaultPromise.notifyListeners(DefaultPromise.java:492) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.DefaultPromise.setValue0(DefaultPromise.java:636) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.DefaultPromise.setFailure0(DefaultPromise.java:629) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.DefaultPromise.tryFailure(DefaultPromise.java:118) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.resolver.dns.DnsQueryContext.finishFailure(DnsQueryContext.java:380) ~[netty-resolver-dns-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.resolver.dns.DnsQueryContext$5.run(DnsQueryContext.java:315) ~[netty-resolver-dns-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.PromiseTask.runTask(PromiseTask.java:98) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.ScheduledFutureTask.run(ScheduledFutureTask.java:153) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.AbstractEventExecutor.runTask(AbstractEventExecutor.java:173) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.AbstractEventExecutor.safeExecute(AbstractEventExecutor.java:166) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.SingleThreadEventExecutor.runAllTasks(SingleThreadEventExecutor.java:469) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.channel.epoll.EpollEventLoop.run(EpollEventLoop.java:408) ~[netty-transport-classes-epoll-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.SingleThreadEventExecutor$4.run(SingleThreadEventExecutor.java:994) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.internal.ThreadExecutorMap$2.run(ThreadExecutorMap.java:74) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        at io.netty.util.concurrent.FastThreadLocalRunnable.run(FastThreadLocalRunnable.java:30) ~[netty-common-4.1.110.Final.jar!/:4.1.110.Final]
        ... 1 common frames omitted
Caused by: io.netty.resolver.dns.DnsNameResolverTimeoutException: [6076: /10.96.0.10:53] DefaultDnsQuestion(redis-service.cbops.svc.cluster.local. IN A) query '6076' via UDP timed out after 5000 milliseconds (no stack trace available)

2026-06-23T07:05:59.622Z ERROR 1 --- [VoucherService] [    BulkCoord-1] c.f.V.S.v.VoucherBulkValidationService   : ASYNC_PROCESS_CRASH | ReqID: 5cf28122-b390-478d-be41-69e0fce6957f | Reason: A critical system error occurred during processing.
2026-06-23T07:06:04.625Z ERROR 1 --- [VoucherService] [    BulkCoord-1] c.f.V.S.v.ValidationStateManager         : REDIS_READ_FAIL | ReqID: 5cf28122-b390-478d-be41-69e0fce6957f | Type: RedisConnectionFailureException
2026-06-23T07:06:09.627Z ERROR 1 --- [VoucherService] [    BulkCoord-1] c.f.V.S.v.ValidationStateManager         : REDIS_WRITE_FAIL | ReqID: 5cf28122-b390-478d-be41-69e0fce6957f | Status: Connection/Persistence failure
2026-06-23T07:06:39.539Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:06:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:07:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:08:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:09:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:10:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:11:44.543Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:11:49.551Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:12:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:13:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:14:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:15:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:16:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:16:54.510Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:17:49.509Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:18:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:19:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:20:49.509Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:21:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:21:59.514Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:22:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:23:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:24:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:25:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:26:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:27:04.518Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:27:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:28:49.509Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:29:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:30:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:31:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:32:09.522Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:32:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:33:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:34:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:35:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:36:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:37:14.525Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:37:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:38:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:39:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:40:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:41:49.505Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:42:19.529Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:42:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:43:49.505Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:44:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:45:49.509Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:46:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:47:24.531Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:47:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:48:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:49:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:50:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:51:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:52:29.534Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:52:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:53:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:54:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:55:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:56:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:57:34.539Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T07:57:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:58:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T07:59:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:00:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:01:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:02:39.542Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:02:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:03:49.505Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:04:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:05:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:06:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:07:44.546Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:07:49.551Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:08:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:09:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:10:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:11:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:12:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:12:54.510Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:13:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:14:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:15:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:16:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:17:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:17:59.514Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:18:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:19:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:20:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:21:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:22:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:23:04.518Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:23:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:24:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:25:49.510Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:26:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:27:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:28:09.522Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:28:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:29:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:30:49.505Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:31:49.505Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:32:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:33:14.527Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:33:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:34:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:35:49.505Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:36:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:37:49.524Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:38:19.531Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:38:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:39:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:40:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:41:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:42:49.507Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:43:24.535Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:43:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:44:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:45:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:46:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:47:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:48:29.538Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.schedule.HdfsRecoveryService     : HDFS_RECOVERY_REDIS_FAIL | Cannot acquire distributed lock.
2026-06-23T08:48:49.508Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:49:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
2026-06-23T08:50:49.506Z ERROR 1 --- [VoucherService] [   scheduling-1] c.f.V.S.s.VoucherExecutionScheduler      : SCHEDULER_CRITICAL_ERROR | Unable to connect to Redis
