[root@fcprodkubjump Microservices]# k logs report-builder-deployment-765df4f9bf-4pqbf -n backend
12:36:00,566 |-ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
12:36:00,569 |-ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
        at java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
        at      at java.base/java.io.FileOutputStream.open0(Native Method)
        at      at java.base/java.io.FileOutputStream.open(FileOutputStream.java:289)
        at      at java.base/java.io.FileOutputStream.<init>(FileOutputStream.java:230)
        at      at ch.qos.logback.core.recovery.ResilientFileOutputStream.<init>(ResilientFileOutputStream.java:26)
        at      at ch.qos.logback.core.FileAppender.openFile(FileAppender.java:206)
        at      at ch.qos.logback.core.FileAppender.start(FileAppender.java:126)
        at      at ch.qos.logback.core.rolling.RollingFileAppender.start(RollingFileAppender.java:104)
        at      at ch.qos.logback.core.model.processor.AppenderModelHandler.postHandle(AppenderModelHandler.java:84)
        at      at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:257)
        at      at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
        at      at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
        at      at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
        at      at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:222)
        at      at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:136)
        at      at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
        at      at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
        at      at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
        at      at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:298)
        at      at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$2(LogbackLoggingSystem.java:260)
        at      at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:481)
        at      at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:252)
        at      at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
        at      at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
        at      at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:195)
        at      at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
        at      at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
        at      at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
        at      at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
        at      at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
        at      at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
        at      at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
        at      at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
        at      at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
        at      at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
        at      at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
        at      at java.base/java.lang.Iterable.forEach(Iterable.java:75)
        at      at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
        at      at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
        at      at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
        at      at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:353)
        at      at org.springframework.boot.SpringApplication.run(SpringApplication.java:313)
        at      at org.springframework.boot.SpringApplication.run(SpringApplication.java:1361)
        at      at org.springframework.boot.SpringApplication.run(SpringApplication.java:1350)
        at      at com.tcs.fincore.ReportBuilder.ReportbuilderApplication.main(ReportbuilderApplication.java:10)
        at      at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at      at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at      at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:106)
        at      at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
        at      at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
Logging system failed to initialize using configuration from 'null'
java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:289)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:267)
        at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
        at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:195)
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
        at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:353)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:313)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1361)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1350)
        at com.tcs.fincore.ReportBuilder.ReportbuilderApplication.main(ReportbuilderApplication.java:10)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:106)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
        Suppressed: java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
                at java.base/java.io.FileOutputStream.open0(Native Method)
                at java.base/java.io.FileOutputStream.open(FileOutputStream.java:289)
                at java.base/java.io.FileOutputStream.<init>(FileOutputStream.java:230)
                at ch.qos.logback.core.recovery.ResilientFileOutputStream.<init>(ResilientFileOutputStream.java:26)
                at ch.qos.logback.core.FileAppender.openFile(FileAppender.java:206)
                at ch.qos.logback.core.FileAppender.start(FileAppender.java:126)
                at ch.qos.logback.core.rolling.RollingFileAppender.start(RollingFileAppender.java:104)
                at ch.qos.logback.core.model.processor.AppenderModelHandler.postHandle(AppenderModelHandler.java:84)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:257)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
                at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:222)
                at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:136)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:298)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$2(LogbackLoggingSystem.java:260)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:481)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:252)
                ... 28 more
2026-03-19 12:36:00.671 ERROR [main] o.s.b.SpringApplication: Application run failed
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
        at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:353)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:313)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1361)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1350)
        at com.tcs.fincore.ReportBuilder.ReportbuilderApplication.main(ReportbuilderApplication.java:10)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:106)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
Caused by: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:289)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:267)
        at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
        at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:195)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
        ... 24 common frames omitted
        Suppressed: java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
                at java.base/java.io.FileOutputStream.open0(Native Method)
                at java.base/java.io.FileOutputStream.open(FileOutputStream.java:289)
                at java.base/java.io.FileOutputStream.<init>(FileOutputStream.java:230)
                at ch.qos.logback.core.recovery.ResilientFileOutputStream.<init>(ResilientFileOutputStream.java:26)
                at ch.qos.logback.core.FileAppender.openFile(FileAppender.java:206)
                at ch.qos.logback.core.FileAppender.start(FileAppender.java:126)
                at ch.qos.logback.core.rolling.RollingFileAppender.start(RollingFileAppender.java:104)
                at ch.qos.logback.core.model.processor.AppenderModelHandler.postHandle(AppenderModelHandler.java:84)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:257)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
                at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:222)
                at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:136)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:298)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$2(LogbackLoggingSystem.java:260)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:481)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:252)
                ... 28 common frames omitted
12:36:00,673 |-WARN in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Attempted to append to non started appender [JSON_FILE].
Exception in thread "main" java.lang.reflect.InvocationTargetException
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:118)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:106)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
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
        at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:353)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:313)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1361)
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1350)
        at com.tcs.fincore.ReportBuilder.ReportbuilderApplication.main(ReportbuilderApplication.java:10)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        ... 4 more
Caused by: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:289)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:267)
        at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
        at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
        at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:195)
        at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
        ... 24 more
        Suppressed: java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
                at java.base/java.io.FileOutputStream.open0(Native Method)
                at java.base/java.io.FileOutputStream.open(FileOutputStream.java:289)
                at java.base/java.io.FileOutputStream.<init>(FileOutputStream.java:230)
                at ch.qos.logback.core.recovery.ResilientFileOutputStream.<init>(ResilientFileOutputStream.java:26)
                at ch.qos.logback.core.FileAppender.openFile(FileAppender.java:206)
                at ch.qos.logback.core.FileAppender.start(FileAppender.java:126)
                at ch.qos.logback.core.rolling.RollingFileAppender.start(RollingFileAppender.java:104)
                at ch.qos.logback.core.model.processor.AppenderModelHandler.postHandle(AppenderModelHandler.java:84)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:257)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
                at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:222)
                at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:136)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
                at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:298)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$2(LogbackLoggingSystem.java:260)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:481)
                at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:252)
                ... 28 more

                this issue is coming and below is the maifest file please alter only the required changes to the manifest for above issue and sen me back the entire file:

                # --------------------------------------------
# Service Account (security baseline)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: report-builder-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: report-builder-deployment
  namespace: backend

spec:
  replicas: 2
  revisionHistoryLimit: 5

  # Zero-downtime rolling updates
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: report-builder-app

  template:
    metadata:
      labels:
        app: report-builder-app

    spec:
      # Dedicated service account for RBAC/security
      serviceAccountName: report-builder-sa

      # Graceful shutdown timing
      terminationGracePeriodSeconds: 30

      # Avoid automatic service env variable injection
      enableServiceLinks: false

      # Pod-level security hardening
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      # Spread pods across nodes for HA readiness
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: report-builder-app

      containers:
      - name: template-config-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/report-builder-service:PR01
        imagePullPolicy: Always

        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: HADOOP_FS_URI
            value: "hdfs://10.177.103.199:8022"
          - name: HADOOP_FS_USER
            value: "root"
          - name: GLIF_REPORTS_BASE_PATH
            value: "/reports"

        ports:
        - containerPort: 8091

        # Resource management for stable scheduling and HPA
        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        # Startup probe prevents restart loops during slow startup
        startupProbe:
          tcpSocket:
            port: 8091
          failureThreshold: 30
          periodSeconds: 10

        # Liveness probe enables self-healing
        livenessProbe:
          tcpSocket:
            port: 8091
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        # Readiness probe ensures traffic only when ready
        readinessProbe:
          tcpSocket:
            port: 8091
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
# Service (internal communication)
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: report-builder-service
  namespace: backend

spec:
  selector:
    app: report-builder-app

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8091

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler (CPU-based)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: report-builder-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: report-builder-deployment

  minReplicas: 1
  maxReplicas: 5

  # Stabilization to avoid scaling flaps
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
# Keeps service available during maintenance
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: report-builder-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: report-builder-app

---
