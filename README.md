2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394428886Z stderr F 		... 28 more
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394427258Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:248)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394425737Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:472)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394424245Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$1(LogbackLoggingSystem.java:254)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394422742Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:292)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394418981Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394417617Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394416102Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394413925Z stderr F 		at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:132)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394404241Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:216)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394256428Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394233362Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.39422712Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394204396Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394198025Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:241)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394150235Z stderr F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.handle(ImplicitModelHandler.java:94)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394145596Z stderr F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.doComplex(ImplicitModelHandler.java:134)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394142877Z stderr F 		at ch.qos.logback.core.util.Loader.loadClass(Loader.java:132)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394110303Z stderr F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:525)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394099481Z stderr F 		at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394057672Z stderr F 		at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:103)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394047979Z stderr F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:592)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394025144Z stderr F 		at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:445)
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.394022105Z stderr F 	Suppressed: java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.39399643Z stderr F 	... 24 more
2026-02-26 16:22:06.394	
 2026-02-26T10:52:06.393989957Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393978601Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393938893Z stderr F 	at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393931496Z stderr F 	at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393929657Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393919081Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393864072Z stderr F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393862379Z stderr F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393859558Z stderr F Caused by: java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393821083Z stderr F 	... 4 more
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.3937973Z stderr F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393772058Z stderr F 	at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393769147Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393767623Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393765647Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:330)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393741303Z stderr F 	at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:370)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393738496Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393700193Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393698729Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393696377Z stderr F 	at java.base/java.lang.Iterable.forEach(Iterable.java:75)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393657843Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393655297Z stderr F 	at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393615196Z stderr F 	at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393613578Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393611115Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393573889Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.39357201Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393568745Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393510804Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393508867Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393485084Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:347)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393481888Z stderr F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393480184Z stderr F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393477967Z stderr F Caused by: java.lang.IllegalStateException: java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393446176Z stderr F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393416596Z stderr F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393398895Z stderr F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393393124Z stderr F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393390191Z stderr F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:118)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.393369864Z stderr F Exception in thread "main" java.lang.reflect.InvocationTargetException
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.39284165Z stdout F 		... 28 common frames omitted
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392839652Z stdout F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:248)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.3928376Z stdout F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:472)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392835639Z stdout F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$1(LogbackLoggingSystem.java:254)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392833861Z stdout F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:292)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392831923Z stdout F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392829965Z stdout F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392827984Z stdout F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392826077Z stdout F 		at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:132)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392821192Z stdout F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:216)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392819203Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392817143Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392815192Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392813403Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392811394Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:241)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392809414Z stdout F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.handle(ImplicitModelHandler.java:94)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392807405Z stdout F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.doComplex(ImplicitModelHandler.java:134)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392805392Z stdout F 		at ch.qos.logback.core.util.Loader.loadClass(Loader.java:132)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.39280343Z stdout F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:525)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392801362Z stdout F 		at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392799331Z stdout F 		at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:103)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392797271Z stdout F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:592)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392795058Z stdout F 		at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:445)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392793083Z stdout F 	Suppressed: java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392790889Z stdout F 	... 24 common frames omitted
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392788416Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392786361Z stdout F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392784271Z stdout F 	at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.39278162Z stdout F 	at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392766488Z stdout F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392764551Z stdout F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392762628Z stdout F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392760373Z stdout F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392757782Z stdout F Caused by: java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.39275562Z stdout F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.39275363Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392751803Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392749885Z stdout F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 16:22:06.393	
 2026-02-26T10:52:06.392736555Z stdout F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392734662Z stdout F 	at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.39273253Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392730552Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392728539Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:330)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392726171Z stdout F 	at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:370)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.39272369Z stdout F 	at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392721726Z stdout F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392719245Z stdout F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392717188Z stdout F 	at java.base/java.lang.Iterable.forEach(Iterable.java:75)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392714917Z stdout F 	at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392712836Z stdout F 	at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392710688Z stdout F 	at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392708363Z stdout F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392706251Z stdout F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392704004Z stdout F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392701352Z stdout F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392698531Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392693316Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392690535Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392688267Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:347)
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392686198Z stdout F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392683429Z stdout F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392679478Z stdout F java.lang.IllegalStateException: java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:22:06.392	
 2026-02-26T10:52:06.392646059Z stdout F 2026-02-26 10:52:06.390 ERROR [main] o.s.b.SpringApplication: Application run failed 
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280191083Z stderr F 		... 28 more
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.28018313Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:248)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280181113Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:472)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280168186Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$1(LogbackLoggingSystem.java:254)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280120992Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:292)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280117798Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280116272Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280114606Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280110796Z stderr F 		at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:132)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280046826Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:216)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280043637Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280007307Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.280005446Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.2799852Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.279965114Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:241)
2026-02-26 16:22:06.280	
 2026-02-26T10:52:06.279960697Z stderr F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.handle(ImplicitModelHandler.java:94)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279943068Z stderr F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.doComplex(ImplicitModelHandler.java:134)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279928877Z stderr F 		at ch.qos.logback.core.util.Loader.loadClass(Loader.java:132)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279912488Z stderr F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:525)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279899391Z stderr F 		at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279882833Z stderr F 		at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:103)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279858998Z stderr F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:592)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279839222Z stderr F 		at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:445)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279834656Z stderr F 	Suppressed: java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279791312Z stderr F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.27972638Z stderr F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279714798Z stderr F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279711326Z stderr F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279708633Z stderr F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.27967881Z stderr F 	at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279675826Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279642557Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279635295Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:330)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279633583Z stderr F 	at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:370)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279631962Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279628449Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279627052Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279625474Z stderr F 	at java.base/java.lang.Iterable.forEach(Iterable.java:75)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279623524Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279622127Z stderr F 	at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279619395Z stderr F 	at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279568127Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279566456Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279564525Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279558991Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279481611Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279473415Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279471688Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279469973Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279464743Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279421042Z stderr F 	at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279419189Z stderr F 	at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279417702Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279414914Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279154798Z stderr F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.279150849Z stderr F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.27913613Z stderr F java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:22:06.279	
 2026-02-26T10:52:06.27907414Z stderr F Logging system failed to initialize using configuration from 'null'
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277658627Z stderr F 		... 28 more
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277610847Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:248)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277608659Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:472)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277593937Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$1(LogbackLoggingSystem.java:254)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277577721Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:292)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277567334Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277563984Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277562381Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277559788Z stderr F 		at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:132)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277514876Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:216)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277510754Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277489435Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277467076Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277464061Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277462362Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:241)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277460254Z stderr F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.handle(ImplicitModelHandler.java:94)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277442916Z stderr F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.doComplex(ImplicitModelHandler.java:134)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277402387Z stderr F 		at ch.qos.logback.core.util.Loader.loadClass(Loader.java:132)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277389344Z stderr F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:525)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277381152Z stderr F 		at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277372373Z stderr F 		at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:103)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277347695Z stderr F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:592)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277320689Z stderr F 		at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:445)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277316536Z stderr F 	Suppressed: java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.27728457Z stderr F 	... 24 more
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277281939Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277254921Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277248735Z stderr F 	at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277246281Z stderr F 	at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277242867Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277214667Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277198445Z stderr F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277195972Z stderr F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.27719306Z stderr F Caused by: java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277154929Z stderr F 	... 4 more
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277134611Z stderr F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277121225Z stderr F 	at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277114277Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277110805Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277090589Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:330)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277077309Z stderr F 	at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:370)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277050716Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277030879Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277029149Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277007448Z stderr F 	at java.base/java.lang.Iterable.forEach(Iterable.java:75)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.277004937Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.276991435Z stderr F 	at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.276967814Z stderr F 	at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
2026-02-26 16:20:37.277	
 2026-02-26T10:50:37.276964127Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276958646Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276956708Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276946574Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276922175Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276918033Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276863319Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276860165Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:347)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276851811Z stderr F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276850127Z stderr F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276847588Z stderr F Caused by: java.lang.IllegalStateException: java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276842433Z stderr F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276840567Z stderr F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276838165Z stderr F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276829452Z stderr F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276729213Z stderr F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:118)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276682896Z stderr F Exception in thread "main" java.lang.reflect.InvocationTargetException
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276199098Z stdout F 		... 28 common frames omitted
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276197644Z stdout F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:248)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276196264Z stdout F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:472)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276194785Z stdout F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$1(LogbackLoggingSystem.java:254)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276193389Z stdout F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:292)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276191373Z stdout F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276189569Z stdout F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276187551Z stdout F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276185675Z stdout F 		at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:132)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276181238Z stdout F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:216)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276179485Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276177394Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276175529Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276173432Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276171798Z stdout F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:241)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.2761705Z stdout F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.handle(ImplicitModelHandler.java:94)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.27616907Z stdout F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.doComplex(ImplicitModelHandler.java:134)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276167635Z stdout F 		at ch.qos.logback.core.util.Loader.loadClass(Loader.java:132)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276166103Z stdout F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:525)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276164797Z stdout F 		at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276163493Z stdout F 		at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:103)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276161871Z stdout F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:592)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276160528Z stdout F 		at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:445)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276159232Z stdout F 	Suppressed: java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276157838Z stdout F 	... 24 common frames omitted
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.27615592Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276154556Z stdout F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276153248Z stdout F 	at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276151924Z stdout F 	at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276147879Z stdout F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276146525Z stdout F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276145204Z stdout F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276143733Z stdout F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276142221Z stdout F Caused by: java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276140931Z stdout F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276139594Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276138147Z stdout F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276136415Z stdout F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276123696Z stdout F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276121649Z stdout F 	at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276119739Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276117718Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276115761Z stdout F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:330)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276113341Z stdout F 	at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:370)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276110974Z stdout F 	at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276109499Z stdout F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276108192Z stdout F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276106721Z stdout F 	at java.base/java.lang.Iterable.forEach(Iterable.java:75)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.27610537Z stdout F 	at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276103961Z stdout F 	at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276102585Z stdout F 	at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276101155Z stdout F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276099781Z stdout F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276098281Z stdout F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276096925Z stdout F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276095156Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276093664Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.27609173Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276090283Z stdout F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:347)
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276088628Z stdout F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276085819Z stdout F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276082224Z stdout F java.lang.IllegalStateException: java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:20:37.276	
 2026-02-26T10:50:37.276047103Z stdout F 2026-02-26 10:50:37.193 ERROR [main] o.s.b.SpringApplication: Application run failed 
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.0858191Z stderr F 		... 28 more
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085816806Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:248)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085806194Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.withLoggingSuppressed(LogbackLoggingSystem.java:472)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085765233Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.lambda$loadConfiguration$1(LogbackLoggingSystem.java:254)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085761488Z stderr F 		at org.springframework.boot.logging.logback.LogbackLoggingSystem.configureByResourceUrl(LogbackLoggingSystem.java:292)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085747395Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:66)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085714423Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:123)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085707281Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.doConfigure(GenericXMLConfigurator.java:178)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085681537Z stderr F 		at org.springframework.boot.logging.logback.SpringBootJoranConfigurator.processModel(SpringBootJoranConfigurator.java:132)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085665399Z stderr F 		at ch.qos.logback.core.joran.GenericXMLConfigurator.processModel(GenericXMLConfigurator.java:216)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.08566277Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.process(DefaultProcessor.java:106)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085625535Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.traversalLoop(DefaultProcessor.java:90)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085621732Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085612395Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:253)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085610872Z stderr F 		at ch.qos.logback.core.model.processor.DefaultProcessor.secondPhaseTraverse(DefaultProcessor.java:241)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085609114Z stderr F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.handle(ImplicitModelHandler.java:94)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085606832Z stderr F 		at ch.qos.logback.core.model.processor.ImplicitModelHandler.doComplex(ImplicitModelHandler.java:134)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.08559313Z stderr F 		at ch.qos.logback.core.util.Loader.loadClass(Loader.java:132)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085525433Z stderr F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:525)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085523355Z stderr F 		at org.springframework.boot.loader.launch.LaunchedClassLoader.loadClass(LaunchedClassLoader.java:91)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085520177Z stderr F 		at org.springframework.boot.loader.net.protocol.jar.JarUrlClassLoader.loadClass(JarUrlClassLoader.java:103)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085472607Z stderr F 		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:592)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085465761Z stderr F 		at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:445)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085461969Z stderr F 	Suppressed: java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085374941Z stderr F 	at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085348838Z stderr F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085347252Z stderr F 	at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085344138Z stderr F 	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085297116Z stderr F 	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085295055Z stderr F 	at com.tcs.userservice.UserServiceApplication.main(UserServiceApplication.java:15)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085293321Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085287046Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085277364Z stderr F 	at org.springframework.boot.SpringApplication.run(SpringApplication.java:330)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.08527417Z stderr F 	at org.springframework.boot.SpringApplication.prepareEnvironment(SpringApplication.java:370)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085262374Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.environmentPrepared(SpringApplicationRunListeners.java:63)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085181211Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:112)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085172102Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.doWithListeners(SpringApplicationRunListeners.java:118)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085170002Z stderr F 	at java.base/java.lang.Iterable.forEach(Iterable.java:75)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.08516765Z stderr F 	at org.springframework.boot.SpringApplicationRunListeners.lambda$environmentPrepared$2(SpringApplicationRunListeners.java:64)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.08516557Z stderr F 	at org.springframework.boot.context.event.EventPublishingRunListener.environmentPrepared(EventPublishingRunListener.java:81)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085159706Z stderr F 	at org.springframework.boot.context.event.EventPublishingRunListener.multicastInitialEvent(EventPublishingRunListener.java:136)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085157366Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085155479Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:156)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085153173Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:178)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085139974Z stderr F 	at org.springframework.context.event.SimpleApplicationEventMulticaster.doInvokeListener(SimpleApplicationEventMulticaster.java:185)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085090674Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEvent(LoggingApplicationListener.java:223)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085082855Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.onApplicationEnvironmentPreparedEvent(LoggingApplicationListener.java:246)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085080905Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initialize(LoggingApplicationListener.java:298)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085079208Z stderr F 	at org.springframework.boot.context.logging.LoggingApplicationListener.initializeSystem(LoggingApplicationListener.java:332)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085077686Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.initialize(LogbackLoggingSystem.java:193)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085076047Z stderr F 	at org.springframework.boot.logging.AbstractLoggingSystem.initialize(AbstractLoggingSystem.java:61)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085074202Z stderr F 	at org.springframework.boot.logging.AbstractLoggingSystem.initializeWithConventions(AbstractLoggingSystem.java:81)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085072052Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.loadConfiguration(LogbackLoggingSystem.java:260)
2026-02-26 16:20:37.085	
 2026-02-26T10:50:37.085058937Z stderr F 	at org.springframework.boot.logging.logback.LogbackLoggingSystem.reportConfigurationErrorsIfNecessary(LogbackLoggingSystem.java:282)
2026-02-26 16:20:37.084	
 2026-02-26T10:50:37.084753103Z stderr F ERROR in ch.qos.logback.core.rolling.RollingFileAppender[JSON_FILE] - No encoder set for the appender named "JSON_FILE".
2026-02-26 16:20:37.084	
 2026-02-26T10:50:37.084750385Z stderr F ERROR in ch.qos.logback.core.model.processor.ImplicitModelHandler - Could not create component [encoder] of type [net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder] java.lang.ClassNotFoundException: net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder
2026-02-26 16:20:37.084	
 2026-02-26T10:50:37.084746403Z stderr F java.lang.IllegalStateException: Logback configuration error detected: 
2026-02-26 16:20:37.084	
 2026-02-26T10:50:37.084706854Z stderr F Logging system failed to initialize using configuration from 'null'


why this issue is coming?




 wj
