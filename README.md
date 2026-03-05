D:\Pragati\PROD-Deployment-Test>kubectl logs login-deployment-749db6f74-r84lc -n backend --kubeconfig h06vksuatcbopscls.conf
Picked up JAVA_TOOL_OPTIONS: -Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake
13:42:04,719 |-ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
13:42:04,794 |-ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
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
        at      at com.fincore.gateway.LoginService.main(LoginService.java:12)
        at      at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at      at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at      at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:102)
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
        at com.fincore.gateway.LoginService.main(LoginService.java:12)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:102)
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
2026-03-05 13:42:04.900 ERROR [main] o.s.b.SpringApplication: Application run failed
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
        at com.fincore.gateway.LoginService.main(LoginService.java:12)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:102)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
13:42:04,902 |-WARN in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Attempted to append to non started appender [JSON_FILE].
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
Exception in thread "main" java.lang.reflect.InvocationTargetException
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:118)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:102)
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:64)
                at ch.qos.logback.core.recovery.ResilientFileOutputStream.<init>(ResilientFileOutputStream.java:26)
                at ch.qos.logback.core.FileAppender.openFile(FileAppender.java:206)
                at ch.qos.logback.core.FileAppender.start(FileAppender.java:126)
                at ch.qos.logback.core.rolling.RollingFileAppender.start(RollingFileAppender.java:104)
                at ch.qos.logback.core.model.processor.AppenderModelHandler.postHandle(AppenderModelHandler.java:84)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:257)
                at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
                at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
                at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:40)
Caused by: java.lang.IllegalStateException: java.lang.IllegalStateException: Logback configuration error detected:
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - Failed to create parent directories for [/logs/application-json.log]
ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - openFile(logs/application-json.log,true) call failed. java.io.FileNotFoundException: logs/application-json.log (No such file or directory)
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
        at com.fincore.gateway.LoginService.main(LoginService.java:12)
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



                I am getting this error
                My config file is :

                # =====================================================
# Service Account (Dedicated Identity for Pod Security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: login-sa
  namespace: backend
automountServiceAccountToken: false   # Prevent unnecessary token mounting

---
# =====================================================
# Pod Disruption Budget
# Prevents voluntary eviction during maintenance
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: login-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: login-backend

---
# =====================================================
# Deployment (Enterprise Hardened)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: login-deployment
  namespace: backend
spec:
  replicas: 2

  # Keep old ReplicaSets for rollback safety
  revisionHistoryLimit: 5

  # Rolling update for zero-downtime deployments
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: login-backend

  template:
    metadata:
      labels:
        app: login-backend
    spec:

      # Attach dedicated Service Account
      serviceAccountName: login-sa

      # Graceful shutdown window
      terminationGracePeriodSeconds: 30

      # Disable automatic service environment variables
      enableServiceLinks: false

      # Spread pods across nodes if scaled in future
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: login-backend

      # Pod-level security hardening
      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      # Existing hostAliases (UNCHANGED)
      hostAliases:
      - ip: "10.189.42.83"
        hostnames:
        - "uatrootdc1.uatad.sbi"

      # Existing volume (UNCHANGED)
      volumes:
      - name: truststore-volume
        secret:
          secretName: ldap-truststore-file
          items:
            - key: ad-truststore.jks
              path: ad-truststore.jks

      containers:
      - name: login-backend-container
        image: h06vksharbor.corp.ad.sbi/cbops/login-service:DEV09
        imagePullPolicy: Always

        # Existing volume mount (UNCHANGED)
        volumeMounts:
        - name: truststore-volume
          mountPath: "/etc/fincore/secrets"
          readOnly: true

        # Existing environment variables (UNCHANGED)
        env:
        - name: SPRING_LDAP_URLS
          value: "ldaps://uatrootdc1.uatad.sbi:3269"
        - name: JAVA_TOOL_OPTIONS
          value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"
        - name: SPRING_DATA_REDIS_HOST
          value: "redis-service.backend.svc.cluster.local"
        - name: SPRING_DATA_REDIS_PORT
          value: "6379"
        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: "lettuce"
        - name: SPRING_PROFILES_ACTIVE
          value: "dev"
        - name: LDAP_TRUSTSTORE_PATH
          value: "file:/etc/fincore/secrets/ad-truststore.jks"
        - name: LDAP_TRUSTSTORE_PASSWORD
          valueFrom:
            secretKeyRef:
              name: ldap-creds
              key: truststore-password

        ports:
        - containerPort: 8085

        # =================================================
        # Resource Management (Prevents Noisy Neighbor)
        # =================================================
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        # =================================================
        # Health Probes (Safe Spring Boot Defaults)
        # =================================================
        readinessProbe:
          tcpSocket:
            port: 8085
          initialDelaySeconds: 15
          periodSeconds: 10
          failureThreshold: 5

        livenessProbe:
          tcpSocket:
            port: 8085
          initialDelaySeconds: 30
          periodSeconds: 20
          failureThreshold: 5

        startupProbe:
          tcpSocket:
            port: 8085
          failureThreshold: 30
          periodSeconds: 10

        # =================================================
        # Graceful Shutdown Hook
        # =================================================
        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

        # =================================================
        # Container-level Security Hardening
        # =================================================
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false   # Disabled because truststore is mounted
          capabilities:
            drop:
              - ALL

---
# =====================================================
# Horizontal Pod Autoscaler (CPU Based)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: login-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: login-deployment
  minReplicas: 1
  maxReplicas: 3
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
# =====================================================
# Service (Unchanged Logic)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: login-service
  namespace: backend
spec:
  selector:
    app: login-backend
  ports:
  - name: http
    protocol: TCP
    port: 80
    targetPort: 8085
  type: ClusterIP


I have created secrets:

kubectl create secret generic ldap-truststore-file --from-file=ad-truststore.jks=./ad-truststore.jks --namespace=backend  --kubeconfig h06vksuatcbopscls.conf
kubectl create secret generic ldap-creds --from-literal=truststore-password=changeit --namespace=backend  --kubeconfig h06vksuatcbopscls.conf
