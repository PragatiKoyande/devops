  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v3.3.0)

2026-11-26 09:20:02.978 INFO  [main] o.s.b.StartupInfoLogger: Starting NotificationServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)
{"@timestamp":"2026-11-26T14:50:02.978802781+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.N.NotificationServiceApplication","message":"Starting NotificationServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)","stack_trace":""}
2026-11-26 09:20:02.986 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "preprod"
{"@timestamp":"2026-11-26T14:50:02.986071077+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.N.NotificationServiceApplication","message":"The following 1 profile is active: \"preprod\"","stack_trace":""}
2026-11-26 09:20:03.993 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
{"@timestamp":"2026-11-26T14:50:03.993900854+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Multiple Spring Data modules found, entering strict repository configuration mode","stack_trace":""}
2026-11-26 09:20:03.995 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
{"@timestamp":"2026-11-26T14:50:03.9958675+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Bootstrapping Spring Data JPA repositories in DEFAULT mode.","stack_trace":""}
2026-11-26 09:20:04.111 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 109 ms. Found 2 JPA repository interfaces.
{"@timestamp":"2026-11-26T14:50:04.111333043+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Finished Spring Data repository scanning in 109 ms. Found 2 JPA repository interfaces.","stack_trace":""}
2026-11-26 09:20:04.128 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
{"@timestamp":"2026-11-26T14:50:04.128759232+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Multiple Spring Data modules found, entering strict repository configuration mode","stack_trace":""}
2026-11-26 09:20:04.129 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
{"@timestamp":"2026-11-26T14:50:04.129986167+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Bootstrapping Spring Data Redis repositories in DEFAULT mode.","stack_trace":""}
2026-11-26 09:20:04.141 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
{"@timestamp":"2026-11-26T14:50:04.141942483+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationExtensionSupport","message":"Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository","stack_trace":""}
2026-11-26 09:20:04.142 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
{"@timestamp":"2026-11-26T14:50:04.142958465+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationExtensionSupport","message":"Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.NotificationService.repository.UserRoleRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository","stack_trace":""}
2026-11-26 09:20:04.143 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 5 ms. Found 0 Redis repository interfaces.
{"@timestamp":"2026-11-26T14:50:04.143215809+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.d.r.c.RepositoryConfigurationDelegate","message":"Finished Spring Data repository scanning in 5 ms. Found 0 Redis repository interfaces.","stack_trace":""}
2026-11-26 09:20:05.252 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 9010 (http)
{"@timestamp":"2026-11-26T14:50:05.252468416+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.w.embedded.tomcat.TomcatWebServer","message":"Tomcat initialized with port 9010 (http)","stack_trace":""}
2026-11-26 09:20:05.263 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-9010"]
{"@timestamp":"2026-11-26T14:50:05.263824941+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.coyote.http11.Http11NioProtocol","message":"Initializing ProtocolHandler [\"http-nio-9010\"]","stack_trace":""}
2026-11-26 09:20:05.266 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
{"@timestamp":"2026-11-26T14:50:05.266263855+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.catalina.core.StandardService","message":"Starting service [Tomcat]","stack_trace":""}
2026-11-26 09:20:05.266 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.24]
{"@timestamp":"2026-11-26T14:50:05.266697888+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.catalina.core.StandardEngine","message":"Starting Servlet engine: [Apache Tomcat/10.1.24]","stack_trace":""}
2026-11-26 09:20:05.304 INFO  [main] o.a.j.l.DirectJDKLog: Initializing Spring embedded WebApplicationContext
{"@timestamp":"2026-11-26T14:50:05.304389741+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.a.c.c.C.[Tomcat].[localhost].[/]","message":"Initializing Spring embedded WebApplicationContext","stack_trace":""}
2026-11-26 09:20:05.306 INFO  [main] o.s.b.w.s.c.ServletWebServerApplicationContext: Root WebApplicationContext: initialization completed in 2282 ms
{"@timestamp":"2026-11-26T14:50:05.306128976+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.w.s.c.ServletWebServerApplicationContext","message":"Root WebApplicationContext: initialization completed in 2282 ms","stack_trace":""}
2026-11-26 09:20:06.071 INFO  [main] o.s.b.w.s.RegistrationBean: Filter mdcFilterRegistration was not registered (disabled)
{"@timestamp":"2026-11-26T14:50:06.07166284+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.boot.web.servlet.RegistrationBean","message":"Filter mdcFilterRegistration was not registered (disabled)","stack_trace":""}
2026-11-26 09:20:06.072 INFO  [main] o.s.b.w.s.RegistrationBean: Filter rbacFilterRegistration was not registered (disabled)
{"@timestamp":"2026-11-26T14:50:06.072014228+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.boot.web.servlet.RegistrationBean","message":"Filter rbacFilterRegistration was not registered (disabled)","stack_trace":""}
2026-11-26 09:20:06.126 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Failed to initialize dependency 'dataSourceScriptDatabaseInitializer' of LoadTimeWeaverAware bean 'entityManagerFactory': Error creating bean with name 'dataSourceScriptDatabaseInitializer' defined in class path resource [org/springframework/boot/autoconfigure/sql/init/DataSourceInitializationConfiguration.class]: Unsatisfied dependency expressed through method 'dataSourceScriptDatabaseInitializer' parameter 0: Error creating bean with name 'dataSource' defined in class path resource [org/springframework/boot/autoconfigure/jdbc/DataSourceConfiguration$Hikari.class]: Failed to instantiate [com.zaxxer.hikari.HikariDataSource]: Factory method 'dataSource' threw exception with message: Failed to determine a suitable driver class
{"@timestamp":"2026-11-26T14:50:06.126945911+05:30","level":"WARN","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.w.s.c.AnnotationConfigServletWebServerApplicationContext","message":"Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Failed to initialize dependency 'dataSourceScriptDatabaseInitializer' of LoadTimeWeaverAware bean 'entityManagerFactory': Error creating bean with name 'dataSourceScriptDatabaseInitializer' defined in class path resource [org/springframework/boot/autoconfigure/sql/init/DataSourceInitializationConfiguration.class]: Unsatisfied dependency expressed through method 'dataSourceScriptDatabaseInitializer' parameter 0: Error creating bean with name 'dataSource' defined in class path resource [org/springframework/boot/autoconfigure/jdbc/DataSourceConfiguration$Hikari.class]: Failed to instantiate [com.zaxxer.hikari.HikariDataSource]: Factory method 'dataSource' threw exception with message: Failed to determine a suitable driver class","stack_trace":""}
2026-11-26 09:20:06.155 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
{"@timestamp":"2026-11-26T14:50:06.155530971+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.apache.catalina.core.StandardService","message":"Stopping service [Tomcat]","stack_trace":""}
2026-11-26 09:20:06.279 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
{"@timestamp":"2026-11-26T14:50:06.279866315+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.a.l.ConditionEvaluationReportLogger","message":"\n\nError starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.","stack_trace":""}
2026-11-26 09:20:06.292 ERROR [main] o.s.b.d.LoggingFailureAnalysisReporter:

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

{"@timestamp":"2026-11-26T14:50:06.292491038+05:30","level":"ERROR","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"o.s.b.d.LoggingFailureAnalysisReporter","message":"\n\n***************************\nAPPLICATION FAILED TO START\n***************************\n\nDescription:\n\nFailed to configure a DataSource: 'url' attribute is not specified and no embedded datasource could be configured.\n\nReason: Failed to determine a suitable driver class\n\n\nAction:\n\nConsider the following:\n\tIf you want an embedded database (H2, HSQL or Derby), please put it on the classpath.\n\tIf you have database settings to be loaded from a particular profile you may need to activate it (the profiles preprod are currently active).\n","stack_trace":""}
