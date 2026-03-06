D:\Pragati\PROD-Deployment-Test>kubectl logs journal-deployment-68cdc98bb8-rm2dw -n backend --kubeconfig h06vksuatcbopscls.conf
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

2026-03-06T05:09:56.200Z  INFO 1 --- [JournalService] [           main] c.f.J.JournalServiceApplication          : Starting JournalServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-06T05:09:56.202Z  INFO 1 --- [JournalService] [           main] c.f.J.JournalServiceApplication          : The following 1 profile is active: "dev"
2026-03-06T05:09:59.202Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-06T05:09:59.203Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-06T05:09:59.719Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Finished Spring Data repository scanning in 510 ms. Found 11 JPA repository interfaces.
2026-03-06T05:10:00.716Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-06T05:10:00.717Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-06T05:10:00.897Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.BranchMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.898Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.CglMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.898Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.CurrencyMasterRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.898Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.FincoreDateRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.898Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.GlBalanceRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.899Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.GlTransactionRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.899Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.JournalLogRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.899Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.JournalRequestRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.899Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.MasterJournalRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.900Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.901Z  INFO 1 --- [JournalService] [           main] .RepositoryConfigurationExtensionSupport : Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.JournalService.Repository.PermissionRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-06T05:10:00.901Z  INFO 1 --- [JournalService] [           main] .s.d.r.c.RepositoryConfigurationDelegate : Finished Spring Data repository scanning in 99 ms. Found 0 Redis repository interfaces.
2026-03-06T05:10:04.020Z  INFO 1 --- [JournalService] [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port 9999 (http)
2026-03-06T05:10:04.105Z  INFO 1 --- [JournalService] [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2026-03-06T05:10:04.105Z  INFO 1 --- [JournalService] [           main] o.apache.catalina.core.StandardEngine    : Starting Servlet engine: [Apache Tomcat/10.1.24]
2026-03-06T05:10:04.510Z  INFO 1 --- [JournalService] [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2026-03-06T05:10:04.511Z  INFO 1 --- [JournalService] [           main] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 8106 ms
2026-03-06T05:10:06.619Z  INFO 1 --- [JournalService] [           main] o.hibernate.jpa.internal.util.LogHelper  : HHH000204: Processing PersistenceUnitInfo [name: oracle]
2026-03-06T05:10:06.906Z  INFO 1 --- [JournalService] [           main] org.hibernate.Version                    : HHH000412: Hibernate ORM core version 6.5.2.Final
2026-03-06T05:10:07.016Z  INFO 1 --- [JournalService] [           main] o.h.c.internal.RegionFactoryInitiator    : HHH000026: Second-level cache disabled
2026-03-06T05:10:08.413Z  INFO 1 --- [JournalService] [           main] o.s.o.j.p.SpringPersistenceUnitInfo      : No LoadTimeWeaver setup: ignoring JPA class transformer
2026-03-06T05:10:08.507Z  INFO 1 --- [JournalService] [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2026-03-06T05:10:09.830Z  INFO 1 --- [JournalService] [           main] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Added connection oracle.jdbc.driver.T4CConnection@70cac22a
2026-03-06T05:10:09.831Z  INFO 1 --- [JournalService] [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Start completed.
2026-03-06T05:10:10.500Z  WARN 1 --- [JournalService] [           main] org.hibernate.orm.deprecation            : HHH90000025: OracleDialect does not need to be specified explicitly using 'hibernate.dialect' (remove the property setting and it will be selected by default)
2026-03-06T05:10:15.119Z  INFO 1 --- [JournalService] [           main] o.h.e.t.j.p.i.JtaPlatformInitiator       : HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)
2026-03-06T05:10:16.027Z  INFO 1 --- [JournalService] [           main] j.LocalContainerEntityManagerFactoryBean : Initialized JPA EntityManagerFactory for persistence unit 'oracle'
2026-03-06T05:10:18.710Z  INFO 1 --- [JournalService] [           main] o.s.d.j.r.query.QueryEnhancerFactory     : Hibernate is in classpath; If applicable, HQL parser will be used.
2026-03-06T05:10:20.215Z  WARN 1 --- [JournalService] [           main] JpaBaseConfiguration$JpaWebConfiguration : spring.jpa.open-in-view is enabled by default. Therefore, database queries may be performed during view rendering. Explicitly configure spring.jpa.open-in-view to disable this warning
2026-03-06T05:10:20.305Z  WARN 1 --- [JournalService] [           main] .s.s.UserDetailsServiceAutoConfiguration :

Using generated security password: 49182f81-6cae-4fed-b360-1a81cf95e8dd

This generated password is for development use only. Your security configuration must be updated before running your application in production.

2026-03-06T05:10:20.399Z  INFO 1 --- [JournalService] [           main] r$InitializeUserDetailsManagerConfigurer : Global AuthenticationManager configured with UserDetailsService bean with name inMemoryUserDetailsManager
2026-03-06T05:10:21.312Z  INFO 1 --- [JournalService] [           main] o.s.s.web.DefaultSecurityFilterChain     : Will secure any request with [org.springframework.security.web.session.DisableEncodeUrlFilter@1de7c0ad, org.springframework.security.web.context.request.async.WebAsyncManagerIntegrationFilter@37445c57, org.springframework.security.web.context.SecurityContextHolderFilter@1155ab2c, org.springframework.security.web.header.HeaderWriterFilter@64f248ea, org.springframework.web.filter.CorsFilter@205f573e, org.springframework.security.web.authentication.logout.LogoutFilter@6d1101eb, com.fincore.commonutilities.security.ContextRbacFilter@3d97b0a, org.springframework.security.web.savedrequest.RequestCacheAwareFilter@7d49ebf2, org.springframework.security.web.servletapi.SecurityContextHolderAwareRequestFilter@1ed28f57, org.springframework.security.web.authentication.AnonymousAuthenticationFilter@20983174, org.springframework.security.web.session.SessionManagementFilter@26db1100, org.springframework.security.web.access.ExceptionTranslationFilter@36e8e3e1, org.springframework.security.web.access.intercept.AuthorizationFilter@72bb0640]
2026-03-06T05:10:22.811Z  INFO 1 --- [JournalService] [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port 9999 (http) with context path '/'
2026-03-06T05:10:22.899Z  INFO 1 --- [JournalService] [           main] c.f.J.JournalServiceApplication          : Started JournalServiceApplication in 28.702 seconds (process running for 31.317)
2026-03-06T05:10:31.128Z  INFO 1 --- [JournalService] [nio-9999-exec-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring DispatcherServlet 'dispatcherServlet'
2026-03-06T05:10:31.128Z  INFO 1 --- [JournalService] [nio-9999-exec-1] o.s.web.servlet.DispatcherServlet        : Initializing Servlet 'dispatcherServlet'
2026-03-06T05:10:31.197Z  INFO 1 --- [JournalService] [nio-9999-exec-1] o.s.web.servlet.DispatcherServlet        : Completed initialization in 1 ms
2026-03-06T05:10:31.311Z ERROR 1 --- [JournalService] [nio-9999-exec-1] c.f.J.Exception.GlobalExceptionHandler   : Unhandled Exception:

org.springframework.web.servlet.resource.NoResourceFoundException: No static resource actuator/health.
        at org.springframework.web.servlet.resource.ResourceHttpRequestHandler.handleRequest(ResourceHttpRequestHandler.java:585) ~[spring-webmvc-6.1.8.jar!/:6.1.8]
        at org.springframework.web.servlet.mvc.HttpRequestHandlerAdapter.handle(HttpRequestHandlerAdapter.java:52) ~[spring-webmvc-6.1.8.jar!/:6.1.8]
        at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:1089) ~[spring-webmvc-6.1.8.jar!/:6.1.8]
        at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:979) ~[spring-webmvc-6.1.8.jar!/:6.1.8]
        at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1014) ~[spring-webmvc-6.1.8.jar!/:6.1.8]
        at org.springframework.web.servlet.FrameworkServlet.doGet(FrameworkServlet.java:903) ~[spring-webmvc-6.1.8.jar!/:6.1.8]
        at jakarta.servlet.http.HttpServlet.service(HttpServlet.java:564) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:885) ~[spring-webmvc-6.1.8.jar!/:6.1.8]
        at jakarta.servlet.http.HttpServlet.service(HttpServlet.java:658) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:195) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:51) ~[tomcat-embed-websocket-10.1.24.jar!/:na]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.springframework.web.filter.CompositeFilter$VirtualFilterChain.doFilter(CompositeFilter.java:108) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.security.web.FilterChainProxy.lambda$doFilterInternal$3(FilterChainProxy.java:231) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:365) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.access.intercept.AuthorizationFilter.doFilter(AuthorizationFilter.java:100) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.access.ExceptionTranslationFilter.doFilter(ExceptionTranslationFilter.java:126) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.access.ExceptionTranslationFilter.doFilter(ExceptionTranslationFilter.java:120) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.session.SessionManagementFilter.doFilter(SessionManagementFilter.java:131) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.session.SessionManagementFilter.doFilter(SessionManagementFilter.java:85) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.authentication.AnonymousAuthenticationFilter.doFilter(AnonymousAuthenticationFilter.java:100) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.servletapi.SecurityContextHolderAwareRequestFilter.doFilter(SecurityContextHolderAwareRequestFilter.java:179) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.savedrequest.RequestCacheAwareFilter.doFilter(RequestCacheAwareFilter.java:63) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at com.fincore.commonutilities.security.ContextRbacFilter.doFilterInternal(ContextRbacFilter.java:62) ~[common-utilities-0.0.1-SNAPSHOT.jar!/:0.0.1-SNAPSHOT]
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.authentication.logout.LogoutFilter.doFilter(LogoutFilter.java:107) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.authentication.logout.LogoutFilter.doFilter(LogoutFilter.java:93) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.web.filter.CorsFilter.doFilterInternal(CorsFilter.java:91) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.header.HeaderWriterFilter.doHeadersAfter(HeaderWriterFilter.java:90) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.header.HeaderWriterFilter.doFilterInternal(HeaderWriterFilter.java:75) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.context.SecurityContextHolderFilter.doFilter(SecurityContextHolderFilter.java:82) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.context.SecurityContextHolderFilter.doFilter(SecurityContextHolderFilter.java:69) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.context.request.async.WebAsyncManagerIntegrationFilter.doFilterInternal(WebAsyncManagerIntegrationFilter.java:62) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.session.DisableEncodeUrlFilter.doFilterInternal(DisableEncodeUrlFilter.java:42) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:374) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy.doFilterInternal(FilterChainProxy.java:233) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.security.web.FilterChainProxy.doFilter(FilterChainProxy.java:191) ~[spring-security-web-6.3.0.jar!/:6.3.0]
        at org.springframework.web.filter.CompositeFilter$VirtualFilterChain.doFilter(CompositeFilter.java:113) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.web.servlet.handler.HandlerMappingIntrospector.lambda$createCacheFilter$3(HandlerMappingIntrospector.java:195) ~[spring-webmvc-6.1.8.jar!/:6.1.8]
        at org.springframework.web.filter.CompositeFilter$VirtualFilterChain.doFilter(CompositeFilter.java:113) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.web.filter.CompositeFilter.doFilter(CompositeFilter.java:74) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.security.config.annotation.web.configuration.WebMvcSecurityConfiguration$CompositeFilterChainProxy.doFilter(WebMvcSecurityConfiguration.java:230) ~[spring-security-config-6.3.0.jar!/:6.3.0]
        at org.springframework.web.filter.DelegatingFilterProxy.invokeDelegate(DelegatingFilterProxy.java:352) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.web.filter.DelegatingFilterProxy.doFilter(DelegatingFilterProxy.java:268) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.springframework.web.filter.RequestContextFilter.doFilterInternal(RequestContextFilter.java:100) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.springframework.web.filter.FormContentFilter.doFilterInternal(FormContentFilter.java:93) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:201) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar!/:6.1.8]
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:167) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:90) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:482) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:115) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:93) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:74) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.valves.RemoteIpValve.invoke(RemoteIpValve.java:731) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:344) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:389) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:63) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:896) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1741) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:52) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.tomcat.util.threads.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1190) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.tomcat.util.threads.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:659) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:63) ~[tomcat-embed-core-10.1.24.jar!/:na]
        at java.base/java.lang.Thread.run(Thread.java:1570) ~[na:na]


This issue/error I am getting and below is my manifest file could you please help resolving this issue

# ============================================
# Service Account
# ============================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: journal-sa
  namespace: backend

---
# ============================================
# Deployment
# ============================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: journal-deployment
  namespace: backend
spec:
  replicas: 2
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: journal-app

  template:
    metadata:
      labels:
        app: journal-app

    spec:
      serviceAccountName: journal-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      volumes:
        - name: logs-volume
          emptyDir: {}
        - name: tmp-volume
          emptyDir: {}

      containers:
        - name: journal-container
          image: h06vksharbor.corp.ad.sbi/cbops/journal-service:DEV04
          imagePullPolicy: Always

          ports:
            - containerPort: 9999

          volumeMounts:
            - name: logs-volume
              mountPath: /logs
            - name: tmp-volume
              mountPath: /tmp

          resources:
            requests:
              cpu: "200m"
              memory: "256Mi"
            limits:
              cpu: "500m"
              memory: "512Mi"

          # =========================
          # PROBES (Actuator Based)
          # =========================
          startupProbe:
            httpGet:
              path: /actuator/health
              port: 9999
            failureThreshold: 30
            periodSeconds: 10

          readinessProbe:
            httpGet:
              path: /actuator/health/readiness
              port: 9999
            initialDelaySeconds: 20
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 3

          livenessProbe:
            httpGet:
              path: /actuator/health/liveness
              port: 9999
            initialDelaySeconds: 40
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 3

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: true
            capabilities:
              drop:
                - ALL

---
# ============================================
# Service
# ============================================
apiVersion: v1
kind: Service
metadata:
  name: journal-service
  namespace: backend
spec:
  selector:
    app: journal-app
  ports:
    - name: http
      port: 80
      targetPort: 9999
  type: ClusterIP

---
# ============================================
# Horizontal Pod Autoscaler
# ============================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: journal-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: journal-deployment
  minReplicas: 1
  maxReplicas: 5
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
# ============================================
# Pod Disruption Budget
# ============================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: journal-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: journal-app
