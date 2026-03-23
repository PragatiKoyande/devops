D:\Pragati\PROD-Deployment-Test>kubectl logs journal-deployment-7777bff7d6-hg26h -n backend --kubeconfig h06vksuatcbopscls.conf
SLF4J(W): Class path contains multiple SLF4J providers.
SLF4J(W): Found provider [ch.qos.logback.classic.spi.LogbackServiceProvider@212bf671]
SLF4J(W): Found provider [org.slf4j.reload4j.Reload4jServiceProvider@14a2f921]
SLF4J(W): See https://www.slf4j.org/codes.html#multiple_bindings for an explanation.
SLF4J(I): Actual provider is of type [ch.qos.logback.classic.spi.LogbackServiceProvider@212bf671]
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v3.3.0)

2026-03-23T11:08:23.401Z  INFO 1 --- [JournalService] [           main] c.f.J.JournalServiceApplication          : Starting JournalServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-23T11:08:23.403Z  INFO 1 --- [JournalService] [           main] c.f.J.JournalServiceApplication          : The following 1 profile is active: "dev"
2026-03-23T11:08:26.214Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-23T11:08:26.215Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-23T11:08:26.796Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Finished Spring Data repository scanning in 574 ms. Found 11 JPA repository interfaces.
2026-03-23T11:08:27.706Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-23T11:08:27.707Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-23T11:08:27.894Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.BranchMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.894Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.CglMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.895Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.CurrencyMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.895Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.FincoreDateRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.895Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.GlBalanceRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.895Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.GlTransactionRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.895Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.JournalLogRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.895Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.JournalRequestRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.896Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.MasterJournalRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.897Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.898Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.PermissionRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-23T11:08:27.898Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Finished Spring Data repository scanning in 99 ms. Found 0 Redis repository interfaces.
2026-03-23T11:08:30.705Z  WARN 1 --- [JournalService] [           main] ConfigServletWebServerApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.context.ApplicationContextException: Unable to start web server
2026-03-23T11:08:30.712Z  INFO 1 --- [JournalService] [           main] .s.b.a.l.ConditionEvaluationReportLogger :

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-23T11:08:30.800Z ERROR 1 --- [JournalService] [           main] o.s.boot.SpringApplication               : Application run failed

org.springframework.context.ApplicationContextException: Unable to start web server
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.onRefresh(ServletWebServerApplicationContext.java:165) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:618) ~[spring-context-6.1.8.jar!/:6.1.8]
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:335) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at com.fincore.JournalService.JournalServiceApplication.main(JournalServiceApplication.java:13) ~[!/:0.0.1-SNAPSHOT]
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
        at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91) ~[app.jar:0.0.1-SNAPSHOT]
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53) ~[app.jar:0.0.1-SNAPSHOT]
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58) ~[app.jar:0.0.1-SNAPSHOT]
Caused by: org.springframework.boot.web.server.WebServerException: Unable to create tempDir. java.io.tmpdir is set to /tmp
        at org.springframework.boot.web.server.AbstractConfigurableWebServerFactory.createTempDir(AbstractConfigurableWebServerFactory.java:221) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.web.embedded.tomcat.TomcatServletWebServerFactory.getWebServer(TomcatServletWebServerFactory.java:204) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.createWebServer(ServletWebServerApplicationContext.java:188) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.onRefresh(ServletWebServerApplicationContext.java:162) ~[spring-boot-3.3.0.jar!/:3.3.0]
        ... 13 common frames omitted
Caused by: java.nio.file.FileSystemException: /tmp/tomcat.9999.8612083024492303173: Read-only file system
        at java.base/sun.nio.fs.UnixException.translateToIOException(UnixException.java:100) ~[na:na]
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:106) ~[na:na]
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:111) ~[na:na]
        at java.base/sun.nio.fs.UnixFileSystemProvider.createDirectory(UnixFileSystemProvider.java:438) ~[na:na]
        at java.base/java.nio.file.Files.createDirectory(Files.java:699) ~[na:na]
        at java.base/java.nio.file.TempFileHelper.create(TempFileHelper.java:134) ~[na:na]
        at java.base/java.nio.file.TempFileHelper.createTempDirectory(TempFileHelper.java:171) ~[na:na]
        at java.base/java.nio.file.Files.createTempDirectory(Files.java:1017) ~[na:na]
        at org.springframework.boot.web.server.AbstractConfigurableWebServerFactory.createTempDir(AbstractConfigurableWebServerFactory.java:215) ~[spring-boot-3.3.0.jar!/:3.3.0]
        ... 16 common frames omitted
        
I know the solution for this you will tell to add the volumes in manifest file for logback, but I dont want o create any volumes inside my pod and want to edit my application level code can you guide me for the same.



        
