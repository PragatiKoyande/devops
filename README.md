2026-03-26 05:54:11.042 INFO  [background-preinit] o.h.v.i.u.Version: HV000001: Hibernate Validator 8.0.1.Final
 :: Spring Boot ::                (v3.3.0)

2026-03-26 05:54:11.138 INFO  [main] o.s.b.StartupInfoLogger: Starting ReportServiceApplication v0.0.1-SNAPSHOT using Java 22.0.2 with PID 1 (/app.jar started by ? in /)
2026-03-26 05:54:11.139 INFO  [main] o.s.b.SpringApplication: The following 1 profile is active: "dev"
2026-03-26 05:54:12.154 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-26 05:54:12.156 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data JPA repositories in DEFAULT mode.
2026-03-26 05:54:12.267 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 105 ms. Found 5 JPA repository interfaces.
2026-03-26 05:54:12.280 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Multiple Spring Data modules found, entering strict repository configuration mode
2026-03-26 05:54:12.281 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Bootstrapping Spring Data Redis repositories in DEFAULT mode.
2026-03-26 05:54:12.291 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.AppConfigRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-26 05:54:12.292 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.DifferenceRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-26 05:54:12.292 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.JasperReportTypeRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-26 05:54:12.293 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.NotificationRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-26 05:54:12.293 INFO  [main] o.s.d.r.c.RepositoryConfigurationExtensionSupport: Spring Data Redis - Could not safely identify store assignment for repository candidate interface com.fincore.ReportService.repository.ReportTypeRepository; If you want this repository to be a Redis repository, consider annotating your entities with one of these annotations: org.springframework.data.redis.core.RedisHash (preferred), or consider extending one of the following types with your repository: org.springframework.data.keyvalue.repository.KeyValueRepository
2026-03-26 05:54:12.293 INFO  [main] o.s.d.r.c.RepositoryConfigurationDelegate: Finished Spring Data repository scanning in 6 ms. Found 0 Redis repository interfaces.
2026-03-26 05:54:13.094 INFO  [main] o.s.b.w.e.t.TomcatWebServer: Tomcat initialized with port 9005 (http)
2026-03-26 05:54:13.102 INFO  [main] o.a.j.l.DirectJDKLog: Initializing ProtocolHandler ["http-nio-9005"]
2026-03-26 05:54:13.104 INFO  [main] o.a.j.l.DirectJDKLog: Starting service [Tomcat]
2026-03-26 05:54:13.105 INFO  [main] o.a.j.l.DirectJDKLog: Starting Servlet engine: [Apache Tomcat/10.1.24]
2026-03-26 05:54:13.131 INFO  [main] o.a.j.l.DirectJDKLog: Initializing Spring embedded WebApplicationContext
2026-03-26 05:54:13.131 INFO  [main] o.s.b.w.s.c.ServletWebServerApplicationContext: Root WebApplicationContext: initialization completed in 1894 ms
2026-03-26 05:54:13.647 INFO  [main] o.s.b.w.s.RegistrationBean: Filter mdcFilterRegistration was not registered (disabled)
2026-03-26 05:54:13.648 INFO  [main] o.s.b.w.s.RegistrationBean: Filter rbacFilterRegistration was not registered (disabled)
2026-03-26 05:54:13.872 INFO  [main] o.h.j.i.u.LogHelper: HHH000204: Processing PersistenceUnitInfo [name: default]
2026-03-26 05:54:13.919 INFO  [main] o.h.Version: HHH000412: Hibernate ORM core version 6.5.2.Final
2026-03-26 05:54:13.948 INFO  [main] o.h.c.i.RegionFactoryInitiator: HHH000026: Second-level cache disabled
2026-03-26 05:54:14.160 INFO  [main] o.s.o.j.p.SpringPersistenceUnitInfo: No LoadTimeWeaver setup: ignoring JPA class transformer
2026-03-26 05:54:14.184 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Starting...
2026-03-26 05:54:14.636 INFO  [main] c.z.h.p.HikariPool: HikariPool-1 - Added connection oracle.jdbc.driver.T4CConnection@63767d
2026-03-26 05:54:14.637 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Start completed.
2026-03-26 05:54:14.745 WARN  [main] o.h.e.j.d.i.DialectFactoryImpl: HHH90000025: OracleDialect does not need to be specified explicitly using 'hibernate.dialect' (remove the property setting and it will be selected by default)
2026-03-26 05:54:15.509 INFO  [main] o.h.e.t.j.p.i.JtaPlatformInitiator: HHH000489: No JTA platform available (set 'hibernate.transaction.jta.platform' to enable JTA platform integration)
2026-03-26 05:54:15.661 INFO  [main] o.s.o.j.AbstractEntityManagerFactoryBean: Initialized JPA EntityManagerFactory for persistence unit 'default'
2026-03-26 05:54:15.910 INFO  [main] o.s.d.j.r.q.QueryEnhancerFactory: Hibernate is in classpath; If applicable, HQL parser will be used.
2026-03-26 05:54:16.522 INFO  [main] c.f.R.c.HadoopConfig: Configuring HDFS HA for Nameservice: fincoredev
2026-03-26 05:54:16.571 INFO  [main] c.f.R.c.HadoopConfig: HDFS HA Configuration complete. Mode: Hedging. Nodes: 10.177.103.199:8022, 10.177.103.192:8022, 10.177.103.196:8022
2026-03-26 05:54:16.708 WARN  [main] o.a.h.u.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
2026-03-26 05:54:17.117 WARN  [main] o.s.c.s.AbstractApplicationContext: Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'reportController' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/ReportService/controller/ReportController.class]: Unsatisfied dependency expressed through constructor parameter 0: Error creating bean with name 'reportServiceImpl' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/ReportService/service/ReportServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 9: Error creating bean with name 'com.fincore.commonutilities.buisnessobject.ControlDateService': Invocation of init method failed
2026-03-26 05:54:17.118 INFO  [main] o.s.o.j.AbstractEntityManagerFactoryBean: Closing JPA EntityManagerFactory for persistence unit 'default'
2026-03-26 05:54:17.120 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Shutdown initiated...
2026-03-26 05:54:17.210 INFO  [main] c.z.h.HikariDataSource: HikariPool-1 - Shutdown completed.
2026-03-26 05:54:17.223 INFO  [main] o.a.j.l.DirectJDKLog: Stopping service [Tomcat]
2026-03-26 05:54:17.237 INFO  [main] o.s.b.a.l.ConditionEvaluationReportLogger:

Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2026-03-26 05:54:17.250 ERROR [main] o.s.b.SpringApplication: Application run failed
org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'reportController' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/ReportService/controller/ReportController.class]: Unsatisfied dependency expressed through constructor parameter 0: Error creating bean with name 'reportServiceImpl' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/ReportService/service/ReportServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 9: Error creating bean with name 'com.fincore.commonutilities.buisnessobject.ControlDateService': Invocation of init method failed
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:795)
        at org.springframework.beans.factory.support.ConstructorResolver.autowireConstructor(ConstructorResolver.java:237)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.autowireConstructor(AbstractAutowireCapableBeanFactory.java:1357)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1194)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:562)
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
Caused by: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'reportServiceImpl' defined in URL [jar:nested:/app.jar/!BOOT-INF/classes/!/com/fincore/ReportService/service/ReportServiceImpl.class]: Unsatisfied dependency expressed through constructor parameter 9: Error creating bean with name 'com.fincore.commonutilities.buisnessobject.ControlDateService': Invocation of init method failed
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:795)
        at org.springframework.beans.factory.support.ConstructorResolver.autowireConstructor(ConstructorResolver.java:237)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.autowireConstructor(AbstractAutowireCapableBeanFactory.java:1357)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1194)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:562)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200)
        at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:254)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1443)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1353)
        at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:904)
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:782)
        ... 24 common frames omitted
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'com.fincore.commonutilities.buisnessobject.ControlDateService': Invocation of init method failed
        at org.springframework.beans.factory.annotation.InitDestroyAnnotationBeanPostProcessor.postProcessBeforeInitialization(InitDestroyAnnotationBeanPostProcessor.java:222)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyBeanPostProcessorsBeforeInitialization(AbstractAutowireCapableBeanFactory.java:422)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1780)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522)
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337)
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234)
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335)
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200)
        at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:254)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1443)
        at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1353)
        at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:904)
        at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:782)
        ... 38 common frames omitted
Caused by: org.springframework.dao.EmptyResultDataAccessException: Incorrect result size: expected 1, actual 0
        at org.springframework.dao.support.DataAccessUtils.nullableSingleResult(DataAccessUtils.java:190)
        at org.springframework.jdbc.core.JdbcTemplate.queryForObject(JdbcTemplate.java:520)
        at com.fincore.commonutilities.buisnessobject.ControlDateService.getControlDates(ControlDateService.java:22)
        at com.fincore.commonutilities.buisnessobject.ControlDateService.validate(ControlDateService.java:19)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.beans.factory.annotation.InitDestroyAnnotationBeanPostProcessor$LifecycleMethod.invoke(InitDestroyAnnotationBeanPostProcessor.java:457)
        at org.springframework.beans.factory.annotation.InitDestroyAnnotationBeanPostProcessor$LifecycleMetadata.invokeInitMethods(InitDestroyAnnotationBeanPostProcessor.java:401)
        at org.springframework.beans.factory.annotation.InitDestroyAnnotationBeanPostProcessor.postProcessBeforeInitialization(InitDestroyAnnotationBeanPostProcessor.java:219)
        ... 51 common frames omitted


        whats the issue here?

        This is my yaml manisfest file:

        [root@fcprodkubjump Microservices]# cat prod-report-deployment.yaml
# --------------------------------------------
# Service Account (security baseline)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: report-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: report-deployment
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
      app: report-backend

  template:
    metadata:
      labels:
        app: report-backend

    spec:
      serviceAccountName: report-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: report-backend

      containers:
      - name: report-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/report-service:PR01
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
            value: "kafka.backend.svc.cluster.local:9092"
          - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
            value: "kafka.backend.svc.cluster.local:9092"
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.190.224.79:1523/fincorepdb1"
          - name: SPRING_DATASOURCE_USERNAME
            value: "fincore"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "Password#1234"
          - name: SPRING_DATASOURCE_DRIVER_CLASS_NAME
            value: "oracle.jdbc.OracleDriver"
        # -----------------------------
        # Hadoop
        # -----------------------------
          - name: HADOOP_FS_HA_NN1
            value: "hdfs://10.177.224.102:8022"
          - name: HADOOP_FS_HA_NN2
            value: "hdfs://10.177.224.103:8022"
          - name: HADOOP_FS_HA_NN3
            value: "hdfs://10.177.224.104:8022"
          - name: HADOOP_FS_HA_NN4
            value: "hdfs://10.177.224.105:8022"
          - name: HADOOP_FS_HA_NN5
            value: "hdfs://10.177.224.106:8022"
          - name: HADOOP_FS_USER
            value: "root"
          - name: HADOOP_FS_URI
            value: "hdfs://fincore"
          - name: GLIF_REPORTS_BASE_PATH
            value: "/reports"

        resources:
          requests:
            memory: "1Gi"
            cpu: "500m"
          limits:
            memory: "8Gi"
            cpu: "4"

        ports:
        - containerPort: 9005

        startupProbe:
          tcpSocket:
            port: 9005
          failureThreshold: 30
          periodSeconds: 10

        livenessProbe:
          tcpSocket:
            port: 9005
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        readinessProbe:
          tcpSocket:
            port: 9005
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]
        volumeMounts:
          - name: logs-volume
            mountPath: /logs
      volumes:
        - name: logs-volume
          emptyDir: {}

---
# --------------------------------------------
# Service
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: report-service
  namespace: backend

spec:
  selector:
    app: report-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9005

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: report-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: report-deployment

  minReplicas: 1
  maxReplicas: 5

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
# --------------------------------------------
# Pod Disruption Budget
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: report-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: report-backend
