[root@fcprodkubjump Microservices]# k logs report-deployment-77f8f4ff75-6d8rt -n backend
Logging system failed to initialize using configuration from 'null'
java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
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
        at com.fincore.ReportService.ReportServiceApplication.main(ReportServiceApplication.java:10)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
        Suppressed: java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
                at java.base/java.io.FileOutputStream.open0(Native Method)
                at java.base/java.io.FileOutputStream.open(FileOutputStream.java:289)
                at java.base/java.io.FileOutputStream.<init>(FileOutputStream.java:230)
                at ch.qos.logback.core.recovery.ResilientFileOutputStream.<init>(ResilientFileOutputStream.java:26)
                at ch.qos.logback.core.FileAppender.openFile(FileAppender.java:206)
                at ch.qos.logback.core.FileAppender.start(FileAppender.java:126)
                at ch.qos.logback.core.rolling.RollingFileAppender.start(RollingFileAppender.java:103)
                at ch.qos.logback.core.model.processor.AppenderModelHandler.postHandle(AppenderModelHandler.java:84)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:257)
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
2026-03-19 10:35:53.103 ERROR [main] o.s.b.SpringApplication: Application run failed
java.lang.IllegalStateException: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
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
        at com.fincore.ReportService.ReportServiceApplication.main(ReportServiceApplication.java:10)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
Caused by: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
        at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
        at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
        ... 24 common frames omitted
        Suppressed: java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
                at java.base/java.io.FileOutputStream.open0(Native Method)
                at java.base/java.io.FileOutputStream.open(FileOutputStream.java:289)
                at java.base/java.io.FileOutputStream.<init>(FileOutputStream.java:230)
                at ch.qos.logback.core.recovery.ResilientFileOutputStream.<init>(ResilientFileOutputStream.java:26)
                at ch.qos.logback.core.FileAppender.openFile(FileAppender.java:206)
                at ch.qos.logback.core.FileAppender.start(FileAppender.java:126)
                at ch.qos.logback.core.rolling.RollingFileAppender.start(RollingFileAppender.java:103)
                at ch.qos.logback.core.model.processor.AppenderModelHandler.postHandle(AppenderModelHandler.java:84)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:257)
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
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
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
        at com.fincore.ReportService.ReportServiceApplication.main(ReportServiceApplication.java:10)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        ... 4 more
Caused by: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
        at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
        at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
        ... 24 more
        Suppressed: java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
                at java.base/java.io.FileOutputStream.open0(Native Method)
                at java.base/java.io.FileOutputStream.open(FileOutputStream.java:289)
                at java.base/java.io.FileOutputStream.<init>(FileOutputStream.java:230)
                at ch.qos.logback.core.recovery.ResilientFileOutputStream.<init>(ResilientFileOutputStream.java:26)
                at ch.qos.logback.core.FileAppender.openFile(FileAppender.java:206)
                at ch.qos.logback.core.FileAppender.start(FileAppender.java:126)
                at ch.qos.logback.core.rolling.RollingFileAppender.start(RollingFileAppender.java:103)
                at ch.qos.logback.core.model.processor.AppenderModelHandler.postHandle(AppenderModelHandler.java:84)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:257)
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


                this issue i m getting and below is my manifest file only do changes related to this issue dont alter anything else: and send me back entire yaml

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

  # Keep previous ReplicaSets for rollback
  revisionHistoryLimit: 5

  # Zero-downtime rolling updates
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
      # Dedicated service account for RBAC/security
      serviceAccountName: report-sa

      # Graceful shutdown duration
      terminationGracePeriodSeconds: 30

      # Disable automatic service env vars
      enableServiceLinks: false

      # Pod-level security hardening
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      # Spread pods across nodes (HA readiness)
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

        # Existing resources kept exactly as provided
        resources:
          requests:
            memory: "1Gi"
            cpu: "500m"
          limits:
            memory: "8Gi"
            cpu: "4"

        ports:
        - containerPort: 9005

        # Startup probe prevents restart loops during boot
        startupProbe:
          tcpSocket:
            port: 9005
          failureThreshold: 30
          periodSeconds: 10

        # Liveness probe for self-healing
        livenessProbe:
          tcpSocket:
            port: 9005
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        # Readiness probe controls traffic routing
        readinessProbe:
          tcpSocket:
            port: 9005
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        # Graceful shutdown hook
        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

---
# --------------------------------------------
# Service (internal cluster communication)
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
# Horizontal Pod Autoscaler (CPU-based scaling)
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

  # Stabilization avoids scale flapping
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
# Ensures availability during maintenance
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
