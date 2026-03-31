  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v3.5.4)

2026-03-31 06:05:35.682 INFO  [main] o.s.b.StartupInfoLogger: Starting LoginService v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-31 06:05:35.770 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "prod"
2026-03-31 06:05:41.073 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-31 06:05:41.075 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-31 06:05:41.581 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 497 ms. Found 6 JPA repository interfaces.
2026-03-31 06:05:41.665 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-31 06:05:41.666 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data LDAP repositories in DEFAULT mode.
2026-03-31 06:05:41.670 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginAttemptRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-31 06:05:41.671 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginParamRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-31 06:05:41.671 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.MenuItemRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-31 06:05:41.672 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RefreshTokenRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-31 06:05:41.672 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RolePermissionsRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-31 06:05:41.672 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data LDAP - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.UserRepository; If you want this repository to be a LDAP repository, consider annotating your entities with one of these annotations: org.springframework.ldap.odm.annotations.Entry (preferred), or consider extending one of the following types with your repository: org.springframework.data.ldap.repository.LdapRepository
2026-03-31 06:05:41.672 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 4 ms. Found 0 LDAP repository interfaces.
2026-03-31 06:05:41.766 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-31 06:05:41.768 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-31 06:05:41.781 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginAttemptRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-31 06:05:41.782 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.LoginParamRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-31 06:05:41.782 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.MenuItemRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-31 06:05:41.782 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RefreshTokenRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-31 06:05:41.783 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.RolePermissionsRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-31 06:05:41.783 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.gateway.repository.UserRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-31 06:05:41.783 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 3 ms. Found 0 Redis repository interfaces.
2026-03-31 06:05:46.065 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 8085 (http)
2026-03-31 06:05:46.078 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-8085"]
2026-03-31 06:05:46.080 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
2026-03-31 06:05:46.080 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.43]
2026-03-31 06:05:47.785 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-31 06:05:49.473 INFO  [main] c.z.h.p.HikariPool: HikariPool-1 - Added connection oracle.jdbc.driver.T4CConnection@6d7677d8
2026-03-31 06:05:49.475 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Start completed.
2026-03-31 06:05:49.671 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default]
2026-03-31 06:05:50.066 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.6.22.Final
2026-03-31 06:05:50.184 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled
2026-03-31 06:05:51.977 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer
2026-03-31 06:05:53.477 INFO  [main] o.h.e.j.e.i.JdbcEnvironmentInitiator: HHH10001005: Database info:
        Database JDBC URL [Connecting through datasource 'HikariDataSource (HikariPool-1)']
        Database driver: undefined/unknown
        Database version: 19.28
        Autocommit mode: undefined/unknown
        Isolation level: undefined/unknown
        Minimum pool size: undefined/unknown
        Maximum pool size: undefined/unknown
2026-03-31 06:05:57.980 INFO  [main] o.h.e.t.j.p.i.JtaPlatformInitiator: HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)
2026-03-31 06:05:57.983 INFO  [main] o.s.o.j.AbstractEntityManagerFactoryBean: Initialized JPA EntityManagerFactory for persistence unit 'default'
2026-03-31 06:05:58.073 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'jwtDecoderConfig': Injection of autowired dependencies failed
2026-03-31 06:05:58.073 INFO  [main] o.s.o.j.AbstractEntityManagerFactoryBean: Closing JPA EntityManagerFactory for persistence unit 'default'
2026-03-31 06:05:58.075 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Shutdown initiated...
2026-03-31 06:05:58.107 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Shutdown completed.
2026-03-31 06:05:58.109 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
2026-03-31 06:05:58.177 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-31 06:05:58.277 ERROR [main] o.s.b.SpringApplication: Application run failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'jwtDecoderConfig': Injection of autowired dependencies failed
        at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor.postProcessProperties(AutowiredAnnotationBeanPostProcessor.java:515)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1459)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:606)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:529)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:339)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:373)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.instantiateSingleton(DefaultListableBeanFactory.java:1222)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingleton(DefaultListableBeanFactory.java:1188)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:1123)
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:987)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:627)
        at org.springframework.boot.web.reactive.context.ReactiveWebServerApplicationContext.refresh(ReactiveWebServerApplicationContext.java:66)
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:752)
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:439)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:318)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1361)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1350)
        at com.fincore.gateway.LoginService.main(LoginService.java:12)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:102)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
Caused by: org.springframework.util.PlaceholderResolutionException: Could not resolve placeholder 'JWT_SECRET' in value "${JWT_SECRET}" <-- "${security.jwt.hmac-base64-secret:}"
        at org.springframework.util.PlaceholderResolutionException.withValue(PlaceholderResolutionException.java:81)
        at org.springframework.util.PlaceholderParser$ParsedValue.resolve(PlaceholderParser.java:423)
        at org.springframework.util.PlaceholderParser.replacePlaceholders(PlaceholderParser.java:128)
        at org.springframework.util.PropertyPlaceholderHelper.parseStringValue(PropertyPlaceholderHelper.java:118)
        at org.springframework.util.PropertyPlaceholderHelper.replacePlaceholders(PropertyPlaceholderHelper.java:114)
        at org.springframework.core.env.AbstractPropertyResolver.doResolvePlaceholders(AbstractPropertyResolver.java:293)
        at org.springframework.core.env.AbstractPropertyResolver.resolveRequiredPlaceholders(AbstractPropertyResolver.java:264)
        at org.springframework.context.support.PropertySourcesPlaceholderConfigurer.lambda$processProperties$0(PropertySourcesPlaceholderConfigurer.java:186)
        at org.springframework.beans.factory.support.AbstractBeanFactory.resolveEmbeddedValue(AbstractBeanFactory.java:971)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1650)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1628)
        at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.resolveFieldValue(AutowiredAnnotationBeanPostProcessor.java:785)
        at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.inject(AutowiredAnnotationBeanPostProcessor.java:768)
        at org.springframework.beans.factory.annotation.InjectionMetadata.inject(InjectionMetadata.java:146)
        at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor.postProcessProperties(AutowiredAnnotationBeanPostProcessor.java:509)
        ... 24 common frames omitted



        This is the issue can you help me what is going wrong here
