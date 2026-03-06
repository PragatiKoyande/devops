D:\Pragati\PROD-Deployment-Test>kubectl logs user-deployment-dbcfd9dd5-4hdgn -n backend --kubeconfig h06vksuatcbopscls.conf
Picked up JAVA_TOOL_OPTIONS: -Djava.net.preferIPv4Stack=true
Logging system failed to initialize using configuration from 'null'
java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
        at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
        at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
        at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
        at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
        at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
        at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
        at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
        at java.base/java.lang.Iterable.forEach(Iterable.java:75)
        at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
        at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
        at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
        at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:370)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:330)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
        at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
        Suppressed: java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
                at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:445)
                at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:592)
                at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:103)
                at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91)
                at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:525)
                at ch.qos.logback.core.util.Loader.loadClass(Loader.java:132)
                at ch.qos.logback.core.model.processor.ImplicitModelHandler.doComplex(ImplicitModelHandler.java:134)
                at ch.qos.logback.core.model.processor.ImplicitModelHandler.handle(ImplicitModelHandler.java:94)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:241)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
                at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:216)
                at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:132)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:292)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$1(LogbackLoggingSystem.java:254)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:472)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:248)
                ... 28 more
2026-03-06 12:41:01.295 ERROR [main] o.s.b.SpringApplication: Application run failed
java.lang.IllegalStateException: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
        at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:347)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
        at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
        at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
        at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
        at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
        at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
        at java.base/java.lang.Iterable.forEach(Iterable.java:75)
        at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
        at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
        at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
        at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:370)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:330)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
        at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
Caused by: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
        at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
        at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
        ... 24 common frames omitted
        Suppressed: java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
                at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:445)
                at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:592)
                at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:103)
                at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91)
                at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:525)
                at ch.qos.logback.core.util.Loader.loadClass(Loader.java:132)
                at ch.qos.logback.core.model.processor.ImplicitModelHandler.doComplex(ImplicitModelHandler.java:134)
                at ch.qos.logback.core.model.processor.ImplicitModelHandler.handle(ImplicitModelHandler.java:94)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:241)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
                at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:216)
                at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:132)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:292)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$1(LogbackLoggingSystem.java:254)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:472)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:248)
                ... 28 common frames omitted
Exception in thread "main" java.lang.reflect.InvocationTargetException
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:118)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
Caused by: java.lang.IllegalStateException: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
        at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:347)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
        at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
        at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
        at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
        at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
        at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
        at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
        at java.base/java.lang.Iterable.forEach(Iterable.java:75)
        at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
        at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
        at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
        at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:370)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:330)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
        at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        ... 4 more
Caused by: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
        at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
        at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
        ... 24 more
        Suppressed: java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
                at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:445)
                at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:592)
                at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:103)
                at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91)
                at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:525)
                at ch.qos.logback.core.util.Loader.loadClass(Loader.java:132)
                at ch.qos.logback.core.model.processor.ImplicitModelHandler.doComplex(ImplicitModelHandler.java:134)
                at ch.qos.logback.core.model.processor.ImplicitModelHandler.handle(ImplicitModelHandler.java:94)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:241)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
                at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:216)
                at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:132)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:292)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$1(LogbackLoggingSystem.java:254)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:472)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:248)
                ... 28 more



                This is other issue which is failing and below is my manifest file:

                # --------------------------------------------
# Service Account
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: user-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-deployment
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
      app: user-backend

  template:
    metadata:
      labels:
        app: user-backend

    spec:
      serviceAccountName: user-sa
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
            app: user-backend

      volumes:
      - name: logs-volume
        emptyDir: {}

      containers:
      - name: user-container
        image: h06vksharbor.corp.ad.sbi/cbops/user-service:TEST-1
        imagePullPolicy: Always

        volumeMounts:
        - name: logs-volume
          mountPath: /logs

        env:

        # FIXED JAVA OPTIONS
        - name: JAVA_TOOL_OPTIONS
          value: "-Djava.net.preferIPv4Stack=true"

        # Kafka
        - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
          value: "kafka-0.kafka.backend.svc.cluster.local:9092"

        - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
          value: "kafka-0.kafka.backend.svc.cluster.local:9092"

        - name: SPRING_KAFKA_CONSUMER_GROUP_ID
          value: "rbac-cache-group"

        # Redis
        - name: SPRING_DATA_REDIS_HOST
          value: "redis-service"

        - name: SPRING_DATA_REDIS_PORT
          value: "6379"

        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: "lettuce"

        ports:
        - containerPort: 8087

        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        startupProbe:
          tcpSocket:
            port: 8087
          failureThreshold: 30
          periodSeconds: 10

        livenessProbe:
          tcpSocket:
            port: 8087
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        readinessProbe:
          tcpSocket:
            port: 8087
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

---
# --------------------------------------------
# Service
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: user-service
  namespace: backend
spec:
  selector:
    app: user-backend

  ports:
  - name: http
    protocol: TCP
    port: 80
    targetPort: 8087

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: user-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: user-deployment

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
  name: user-pdb
  namespace: backend

spec:
  minAvailable: 1

  selector:
    matchLabels:
      app: user-backend
