2026-03-10 05:02:22.542 INFO  [background-preinit] o.h.v.i.u.Version: HV000001: Hibernate Validator 8.0.1.Final
 :: Spring Boot ::                (v3.3.0)

2026-03-10 05:02:22.671 INFO  [main] o.s.b.StartupInfoLogger: Starting ReportServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by root in /)
2026-03-10 05:02:22.673 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "uat"
2026-03-10 05:02:24.104 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-10 05:02:24.107 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-10 05:02:24.260 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 145 ms. Found 5 JPA repository interfaces.
2026-03-10 05:02:24.282 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-10 05:02:24.283 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-10 05:02:24.304 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.AppConfigRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-10 05:02:24.304 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.DifferenceRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-10 05:02:24.305 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.JasperReportTypeRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-10 05:02:24.307 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-10 05:02:24.308 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.ReportTypeRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-10 05:02:24.308 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 13 ms. Found 0 Redis repository interfaces.
2026-03-10 05:02:25.560 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 9005 (http)
2026-03-10 05:02:25.577 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-9005"]
2026-03-10 05:02:25.579 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
2026-03-10 05:02:25.580 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.24]
2026-03-10 05:02:25.626 INFO  [main] o.a.j.l.DirectJDKLog: Initializing Spring embedded WebApplicationContext
2026-03-10 05:02:25.627 INFO  [main] o.s.b.w.s.c.ServletWebServerApplicationContext: Root WebApplicationContext: initialization completed in 2813 ms
2026-03-10 05:02:26.498 INFO  [main] o.s.b.w.s.RegistrationBean: Filter mdcFilterRegistration was not registered (disabled)
2026-03-10 05:02:26.499 INFO  [main] o.s.b.w.s.RegistrationBean: Filter rbacFilterRegistration was not registered (disabled)
2026-03-10 05:02:26.863 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default]
2026-03-10 05:02:26.919 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.5.2.Final
2026-03-10 05:02:26.950 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled
2026-03-10 05:02:27.189 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer
2026-03-10 05:02:27.215 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-10 05:02:27.600 INFO  [main] c.z.h.p.HikariPool: HikariPool-1 - Added connection oracle.jdbc.driver.T4CConnection@37c49a55
2026-03-10 05:02:27.602 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Start completed.
2026-03-10 05:02:27.753 WARN  [main] o.h.e.j.d.i.DialectFactoryImpl: HHH90000025: OracleDialect does not need to be specified explicitly using 'hibernate.dialect' (remove the property setting and it will be selected by default)
2026-03-10 05:02:28.746 INFO  [main] o.h.e.t.j.p.i.JtaPlatformInitiator: HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)
2026-03-10 05:02:29.106 INFO  [main] o.s.o.j.AbstractEntityManagerFactoryBean: Initialized JPA EntityManagerFactory for persistence unit 'default'
2026-03-10 05:02:29.127 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'hadoopConfig': Injection of autowired dependencies failed
2026-03-10 05:02:29.128 INFO  [main] o.s.o.j.AbstractEntityManagerFactoryBean: Closing JPA EntityManagerFactory for persistence unit 'default'
2026-03-10 05:02:29.130 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Shutdown initiated...
2026-03-10 05:02:29.180 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Shutdown completed.
2026-03-10 05:02:29.195 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
2026-03-10 05:02:29.213 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-10 05:02:29.228 ERROR [main] o.s.b.SpringApplication: Application run failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'hadoopConfig': Injection of autowired dependencies failed
        at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor.postProcessProperties(AutowiredAnnotationBeanPostProcessor.java:514)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1421)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:599)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:975)
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:962)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624)
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146)
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754)
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:335)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
        at com.fincore.ReportService.ReportServiceApplication.main(ReportServiceApplication.java:10)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
Caused by: java.lang.IllegalArgumentException: Could not resolve placeholder 'hadoop.fs.nameservice' in value "${hadoop.fs.nameservice}"
        at org.springframework.util.PropertyPlaceholderHelper.parseStringValue(PropertyPlaceholderHelper.java:180)
        at org.springframework.util.PropertyPlaceholderHelper.replacePlaceholders(PropertyPlaceholderHelper.java:126)
        at org.springframework.core.env.AbstractPropertyResolver.doResolvePlaceholders(AbstractPropertyResolver.java:239)
        at org.springframework.core.env.AbstractPropertyResolver.resolveRequiredPlaceholders(AbstractPropertyResolver.java:210)
        at org.springframework.context.support.PropertySourcesPlaceholderConfigurer.lambda$processProperties$0(PropertySourcesPlaceholderConfigurer.java:200)
        at org.springframework.beans.factory.support.AbstractBeanFactory.resolveEmbeddedValue(AbstractBeanFactory.java:964)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1374)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1353)
        at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.resolveFieldValue(AutowiredAnnotationBeanPostProcessor.java:784)
        at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor$AutowiredFieldElement.inject(AutowiredAnnotationBeanPostProcessor.java:767)
        at org.springframework.beans.factory.annotation.InjectionMetadata.inject(InjectionMetadata.java:145)
        at org.springframework.beans.factory.annotation.AutowiredAnnotationBeanPostProcessor.postProcessProperties(AutowiredAnnotationBeanPostProcessor.java:508)
        ... 22 common frames omitted



        This issue I m getting and below is my manifest file:

        apiVersion: apps/v1
kind: Deployment
metadata:
  name: report-deployment
  namespace: uat-cbops1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: report-backend
  template:
    metadata:
      labels:
        app: report-backend
    spec:
      containers:
      - name: report-container
        image: h06vksharbor.corp.ad.sbi/cbops/report-service:UAT14
        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service" 
          - name: SPRING_PROFILES_ACTIVE
            value: "uat"        
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"       
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.179.85:1523/fincorepdb1"
          - name: SPRING_DATASOURCE_USERNAME			
            value: "fincore"		  
          - name: SPRING_DATASOURCE_PASSWORD			
            value: "Password#1234"
          - name: HADOOP_FS_URI			
            value: "hdfs://10.177.179.99:8022"
          - name: HADOOP_FS_USER			
            value: "root"
          - name: GLIF_REPORTS_BASE_PATH			
            value: "/reports"         
        ports:
        - containerPort: 9005
        imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: report-service
  namespace: uat-cbops1
spec:
  selector:
    app: report-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9005
  type: ClusterIP
