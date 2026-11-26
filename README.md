
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v4.1.0)

2026-11-26 09:00:22.027 INFO  [main] o.s.b.StartupInfoLogger: Starting NotificationServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)
{"@timestamp":"2026-11-26T14:30:22.027931026+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.N.NotificationServiceApplication","message":"Starting NotificationServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)","stack_trace":""}
2026-11-26 09:00:22.036 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "preprod"
{"@timestamp":"2026-11-26T14:30:22.036962479+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.N.NotificationServiceApplication","message":"The following 1 profile is active: \"preprod\"","stack_trace":""}
2026-11-26 09:00:23.053 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
{"@timestamp":"2026-11-26T14:30:23.053458824+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Multiple Spring Data modules found, entering strict repository configuration mode","stack_trace":""}
2026-11-26 09:00:23.055 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
{"@timestamp":"2026-11-26T14:30:23.055500728+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Bootstrapping Spring Data JPA repositories in DEFAULT mode.","stack_trace":""}
2026-11-26 09:00:23.223 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 158 ms. Found 2 JPA repository interfaces.
{"@timestamp":"2026-11-26T14:30:23.223816774+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Finished Spring Data repository scanning in 158 ms. Found 2 JPA repository interfaces.","stack_trace":""}
2026-11-26 09:00:23.248 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
{"@timestamp":"2026-11-26T14:30:23.248821107+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Multiple Spring Data modules found, entering strict repository configuration mode","stack_trace":""}
2026-11-26 09:00:23.250 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
{"@timestamp":"2026-11-26T14:30:23.250452066+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Bootstrapping Spring Data Redis repositories in DEFAULT mode.","stack_trace":""}
2026-11-26 09:00:23.267 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
{"@timestamp":"2026-11-26T14:30:23.267614143+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationExtensionSupport","message":"Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository","stack_trace":""}
2026-11-26 09:00:23.268 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
{"@timestamp":"2026-11-26T14:30:23.26887908+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationExtensionSupport","message":"Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository","stack_trace":""}
2026-11-26 09:00:23.269 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 6 ms. Found 0 Redis repository interfaces.
{"@timestamp":"2026-11-26T14:30:23.269217637+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Finished Spring Data repository scanning in 6 ms. Found 0 Redis repository interfaces.","stack_trace":""}
2026-11-26 09:00:24.415 INFO  [main] o.s.b.t.TomcatWebServer: Tomcat initialized with port 9010 (http)
{"@timestamp":"2026-11-26T14:30:24.415062699+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.boot.tomcat.TomcatWebServer","message":"Tomcat initialized with port 9010 (http)","stack_trace":""}
2026-11-26 09:00:24.428 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-9010"]
{"@timestamp":"2026-11-26T14:30:24.428068564+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.coyote.http11.Http11NioProtocol","message":"Initializing ProtocolHandler [\"http-nio-9010\"]","stack_trace":""}
2026-11-26 09:00:24.430 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
{"@timestamp":"2026-11-26T14:30:24.430378865+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.catalina.core.StandardService","message":"Starting service [Tomcat]","stack_trace":""}
2026-11-26 09:00:24.430 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/11.0.24]
{"@timestamp":"2026-11-26T14:30:24.43070399+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.catalina.core.StandardEngine","message":"Starting Servlet engine: [Apache Tomcat/11.0.24]","stack_trace":""}
2026-11-26 09:00:24.454 INFO  [main] o.s.b.w.c.s.WebApplicationContextInitializer: Root WebApplicationContext: initialization completed in 2349 ms
{"@timestamp":"2026-11-26T14:30:24.454961786+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.w.c.s.WebApplicationContextInitializer","message":"Root WebApplicationContext: initialization completed in 2349 ms","stack_trace":""}
2026-11-26 09:00:25.240 INFO  [main] o.s.b.w.s.RegistrationBean: Filter mdcFilterRegistration was not registered (disabled)
{"@timestamp":"2026-11-26T14:30:25.240905873+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.boot.web.servlet.RegistrationBean","message":"Filter mdcFilterRegistration was not registered (disabled)","stack_trace":""}
2026-11-26 09:00:25.241 INFO  [main] o.s.b.w.s.RegistrationBean: Filter rbacFilterRegistration was not registered (disabled)
{"@timestamp":"2026-11-26T14:30:25.241386503+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.boot.web.servlet.RegistrationBean","message":"Filter rbacFilterRegistration was not registered (disabled)","stack_trace":""}
2026-11-26 09:00:25.321 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/hibernate/autoconfigure/HibernateJpaConfiguration.class]: Failed to initialize dependency 'dataSourceScriptDatabaseInitializer' of LoadTimeWeaverAware bean 'entityManagerFactory': Error creating bean with name 'dataSourceScriptDatabaseInitializer' defined in class path resource [org/springframework/boot/jdbc/autoconfigure/DataSourceInitializationAutoConfiguration.class]: Unsatisfied dependency expressed through method 'dataSourceScriptDatabaseInitializer' parameter 0: Error creating bean with name 'dataSource' defined in class path resource [org/springframework/boot/jdbc/autoconfigure/DataSourceConfiguration$Hikari.class]: Failed to instantiate [com.zaxxer.hikari.HikariDataSource]: Factory method 'dataSource' threw exception with message: Failed to determine a suitable driver class
{"@timestamp":"2026-11-26T14:30:25.321327873+05:30","level":"WARN","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.w.s.s.c.AnnotationConfigServletWebServerApplicationContext","message":"Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/hibernate/autoconfigure/HibernateJpaConfiguration.class]: Failed to initialize dependency 'dataSourceScriptDatabaseInitializer' of LoadTimeWeaverAware bean 'entityManagerFactory': Error creating bean with name 'dataSourceScriptDatabaseInitializer' defined in class path resource [org/springframework/boot/jdbc/autoconfigure/DataSourceInitializationAutoConfiguration.class]: Unsatisfied dependency expressed through method 'dataSourceScriptDatabaseInitializer' parameter 0: Error creating bean with name 'dataSource' defined in class path resource [org/springframework/boot/jdbc/autoconfigure/DataSourceConfiguration$Hikari.class]: Failed to instantiate [com.zaxxer.hikari.HikariDataSource]: Factory method 'dataSource' threw exception with message: Failed to determine a suitable driver class","stack_trace":""}
2026-11-26 09:00:25.339 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
{"@timestamp":"2026-11-26T14:30:25.339140169+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.catalina.core.StandardService","message":"Stopping service [Tomcat]","stack_trace":""}
2026-11-26 09:00:25.493 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
{"@timestamp":"2026-11-26T14:30:25.493936737+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.a.l.ConditionEvaluationReportLogger","message":"\n\nError starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.","stack_trace":""}
2026-11-26 09:00:25.506 ERROR [main] o.s.b.d.LoggingFailureAnalysisReporter:

***************************
APPLICATION FAILED TO START
***************************

Description:

Failed to configure a DataSource: 'url' attribute is not specified and no embedded datasource could be configured.

Reason: Failed to determine a suitable driver class


Action:

Consider the following:
        If you want an embedded database (H2, HSQL or Derby), please put it on the classpath.
        If you have database settings to be loaded from a particular profile you may need to activate it (the profiles preprod are currently active).

{"@timestamp":"2026-11-26T14:30:25.506622457+05:30","level":"ERROR","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.d.LoggingFailureAnalysisReporter","message":"\n\n***************************\nAPPLICATION FAILED TO START\n***************************\n\nDescription:\n\nFailed to configure a DataSource: 'url' attribute is not specified and no embedded datasource could be configured.\n\nReason: Failed to determine a suitable driver class\n\n\nAction:\n\nConsider the following:\n\tIf you want an embedded database (H2, HSQL or Derby), please put it on the classpath.\n\tIf you have database settings to be loaded from a particular profile you may need to activate it (the profiles preprod are currently active).\n","stack_trace":""}
