2026-03-19 10:56:30.916 INFO  [main] o.s.b.StartupInfoLogger: Starting DashboardServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-19 10:56:30.921 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "dev"
2026-03-19 10:56:34.512 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-19 10:56:34.514 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-19 10:56:34.931 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 412 ms. Found 8 JPA repository interfaces.
2026-03-19 10:56:35.022 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-19 10:56:35.023 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-19 10:56:35.113 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.DashboardService.repository.AnnouncementRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 10:56:35.114 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.DashboardService.repository.CalenderConfigRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 10:56:35.114 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.DashboardService.repository.CommonReqRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 10:56:35.114 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.DashboardService.repository.DashboardStatsRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 10:56:35.115 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.DashboardService.repository.JournalRequestRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 10:56:35.116 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.DashboardService.repository.NotificationOutboxRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 10:56:35.116 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.DashboardService.repository.PermissionRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 10:56:35.116 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.DashboardService.repository.UserLogsRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-19 10:56:35.116 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 6 ms. Found 0 Redis repository interfaces.
2026-03-19 10:56:38.427 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 9015 (http)
2026-03-19 10:56:38.515 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-9015"]
2026-03-19 10:56:38.516 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
2026-03-19 10:56:38.516 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.24]
2026-03-19 10:56:38.709 INFO  [main] o.a.j.l.DirectJDKLog: Initializing Spring embedded WebApplicationContext
2026-03-19 10:56:38.709 INFO  [main] o.s.b.w.s.c.ServletWebServerApplicationContext: Root WebApplicationContext: initialization completed in 7594 ms
2026-03-19 10:56:40.809 INFO  [main] o.s.b.w.s.RegistrationBean: Filter mdcFilterRegistration was not registered (disabled)
2026-03-19 10:56:40.810 INFO  [main] o.s.b.w.s.RegistrationBean: Filter rbacFilterRegistration was not registered (disabled)
2026-03-19 10:56:41.912 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-19 10:57:13.249 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default]
2026-03-19 10:57:13.421 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.5.2.Final
2026-03-19 10:57:13.514 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled
2026-03-19 10:57:14.314 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer
2026-03-19 10:57:14.334 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-19 10:57:45.337 WARN  [main] o.h.e.j.e.i.JdbcEnvironmentInitiator: HHH000342: Could not obtain connection to query metadata
java.lang.NullPointerException: Cannot invoke "org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(java.sql.SQLException, String)" because the return value of "org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.sqlExceptionHelper()" is null
        at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:116)
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
2026-03-19 10:57:45.338 ERROR [main] o.s.o.j.AbstractEntityManagerFactoryBean: Failed to initialize JPA EntityManagerFactory: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-03-19 10:57:45.339 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
2026-03-19 10:57:45.352 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
2026-03-19 10:57:45.415 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-19 10:57:45.510 ERROR [main] o.s.b.SpringApplication: Application run failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
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
Caused by: org.hibernate.service.spi.ServiceException: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:276)
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
        ... 20 common frames omitted
Caused by: org.hibernate.HibernateException: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.determineDialect(DialectFactoryImpl.java:191)
        at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.buildDialect(DialectFactoryImpl.java:87)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentWithDefaults(JdbcEnvironmentInitiator.java:152)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:362)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123)
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77)
        at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263)
        ... 35 common frames omitted

        this is my issue and below is my manifets file please alter only the chnages required to resolv ethe issue and dont aletr anything else and sen me back entire yaml with correction:

        [root@fcprodkubjump Microservices]# cat prod-dashboard-deployment.yaml
# =====================================================
# Service Account (Dedicated identity for security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: dashboard-sa
  namespace: backend
automountServiceAccountToken: false

---
# =====================================================
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: dashboard-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: dashboard-backend

---
# =====================================================
# Deployment
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: dashboard-deployment
  namespace: backend
spec:
  replicas: 2

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: dashboard-backend

  template:
    metadata:
      labels:
        app: dashboard-backend
    spec:

      serviceAccountName: dashboard-sa
      terminationGracePeriodSeconds: 30

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: dashboard-backend

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      containers:
      - name: dashboard-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/dashboard-service:PR01
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"

        ports:
        - containerPort: 9015

        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 9015
          initialDelaySeconds: 15
          periodSeconds: 10
          failureThreshold: 5

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 9015
          initialDelaySeconds: 30
          periodSeconds: 20
          failureThreshold: 5

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 9015
          failureThreshold: 30
          periodSeconds: 10

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL
        volumeMounts:
          - name: logs-volume
            mountPath: /logs
      volumes:
        - name: logs-volume
          emptyDir: {}

---
# =====================================================
# Horizontal Pod Autoscaler
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: dashboard-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: dashboard-deployment
  minReplicas: 1
  maxReplicas: 3
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
# =====================================================
# Service
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: dashboard-service
  namespace: backend
spec:
  selector:
    app: dashboard-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9015
  type: ClusterIP
