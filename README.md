apiVersion: v1
kind: ConfigMap
metadata:
  name: debezium-server-config
  namespace: uat-cbops1
data:
  application.properties: |
    debezium.source.connector.class=io.debezium.connector.oracle.OracleConnector
    debezium.source.tasks.max=1

    debezium.source.database.hostname=10.177.179.85
    debezium.source.database.port=1523
    debezium.source.database.user=c##debezium
    debezium.source.database.password=Debe#123
    debezium.source.database.dbname=fincorepdb1
    debezium.source.database.pdb.name=fincorepdb1
    debezium.source.database.sid=fincorepdb1
    debezium.source.database.server.name=fincorepdb1

    debezium.source.topic.prefix=fincore
    debezium.source.table.include.list=fincore.NOTIFICATIONS,fincore.USER_ROLES,fincore.PROCESS_STATUS,fincore.PERMISSIONS,fincore.ROLE_PERMISSIONS

    debezium.source.decimal.handling.mode=string
    debezium.source.database.connection.adapter=logminer

    debezium.source.schema.history.internal.kafka.bootstrap.servers=kafka.uat-cbops1.svc.cluster.local:9092
    debezium.source.schema.history.internal.kafka.topic=schema-changes.oracle.fresh

    debezium.source.log.mining.strategy=online_catalog
    debezium.source.log.mining.continuous.mine=false
    debezium.source.log.mining.batch.size.default=50000
    debezium.source.log.mining.batch.size.max=100000
    debezium.source.log.mining.sleep.time.default=50
    debezium.source.log.mining.sleep.time.max=2000

    debezium.source.heartbeat.interval.ms=2000
    debezium.source.heartbeat.topics.prefix=heartbeat

    debezium.sink.type=kafka
    debezium.sink.kafka.producer.bootstrap.servers=kafka.uat-cbops1.svc.cluster.local:9092
    debezium.sink.kafka.key.serializer=org.apache.kafka.common.serialization.StringSerializer
    debezium.sink.kafka.value.serializer=org.apache.kafka.common.serialization.StringSerializer
    debezium.sink.kafka.producer.key.serializer=org.apache.kafka.common.serialization.StringSerializer
    debezium.sink.kafka.producer.value.serializer=org.apache.kafka.common.serialization.StringSerializer

    debezium.format.key=json
    debezium.format.value=json

    debezium.source.offset.storage.file.filename=/debezium/data/offsets_fresh.dat
    debezium.source.offset.flush.interval.ms=60000
    debezium.source.snapshot.mode=initial

    quarkus.log.level=INFO
    quarkus.log.console.json=false
    quarkus.log.console.format=%d{yyyy-MM-dd HH:mm:ss} %-5p [%c] (%t) %s%e%n
    debezium.history.skip.unparseable.ddl=true
    include.schema.changes=false
    logging.level.io.debezium=DEBUG

---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: debezium-pvc
  namespace: uat-cbops1
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: h06-vks-sp-5
  resources:
    requests:
      storage: 5Gi

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: debezium-server
  namespace: uat-cbops1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: debezium-server
  template:
    metadata:
      labels:
        app: debezium-server
    spec:
      securityContext:
        fsGroup: 1000
      containers:
        - name: debezium-server
          image: h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1
          imagePullPolicy: IfNotPresent

          securityContext:
            runAsUser: 1000
            runAsGroup: 1000

          env:
            - name: JAVA_OPTS
              value: "-Xms512m -Xmx2g"

          ports:
            - containerPort: 8080

          volumeMounts:
            - name: config-volume
              mountPath: /debezium/conf
            - name: data-volume
              mountPath: /debezium/data

          resources:
            requests:
              cpu: "500m"
              memory: "1Gi"
            limits:
              cpu: "2"
              memory: "3Gi"

      volumes:
        - name: config-volume
          configMap:
            name: debezium-server-config

        - name: data-volume
          persistentVolumeClaim:
            claimName: debezium-pvc

---
apiVersion: v1
kind: Service
metadata:
  name: debezium-server
  namespace: uat-cbops1
spec:
  selector:
    app: debezium-server
  ports:
    - name: http
      port: 8080
      targetPort: 8080
  type: ClusterIP


I am having this devezium deployment yaml 

getting issue as per below 
2026-07-29 07:09:07 INFO  [org.apache.kafka.connect.storage.FileOffsetBackingStore] (pool-7-thread-1) Stopped FileOffsetBackingStore
2026-07-29 07:09:07 ERROR [io.debezium.server.ConnectorLifecycle] (pool-7-thread-1) Connector completed: success = 'false', message = 'Error while trying to run connector class 'io.debezium.connector.oracle.OracleConnector'', error = 'org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.': org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.
        at io.debezium.pipeline.ErrorHandler.setProducerThrowable(ErrorHandler.java:67)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:269)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)
Caused by: io.debezium.text.ParsingException: DDL statement couldn't be parsed. Please open a Jira issue with the statement 'ALTER TABLE dr_view_dimension
MODIFY ID GENERATED ALWAYS AS IDENTITY (NOCACHE);'
mismatched input 'GENERATED' expecting {<EOF>, '/', ';'}
        at io.debezium.antlr.ParsingErrorListener.syntaxError(ParsingErrorListener.java:43)
        at org.antlr.v4.runtime.ProxyErrorListener.syntaxError(ProxyErrorListener.java:41)
        at org.antlr.v4.runtime.Parser.notifyErrorListeners(Parser.java:543)
        at org.antlr.v4.runtime.DefaultErrorStrategy.reportInputMismatch(DefaultErrorStrategy.java:327)
        at org.antlr.v4.runtime.DefaultErrorStrategy.reportError(DefaultErrorStrategy.java:139)
        at io.debezium.ddl.parser.oracle.generated.PlSqlParser.sql_script(PlSqlParser.java:2197)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parseTree(OracleDdlParser.java:73)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parseTree(OracleDdlParser.java:32)
        at io.debezium.antlr.AntlrDdlParser.parse(AntlrDdlParser.java:78)
        at io.debezium.connector.oracle.antlr.OracleDdlParser.parse(OracleDdlParser.java:68)
        at io.debezium.connector.oracle.OracleSchemaChangeEventEmitter.emitSchemaChangeEvent(OracleSchemaChangeEventEmitter.java:84)
        at io.debezium.pipeline.EventDispatcher.dispatchSchemaChangeEvent(EventDispatcher.java:379)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.handleSchemaChange(AbstractLogMinerEventProcessor.java:773)
        at io.debezium.connector.oracle.logminer.processor.memory.MemoryLogMinerEventProcessor.handleSchemaChange(MemoryLogMinerEventProcessor.java:176)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.processRow(AbstractLogMinerEventProcessor.java:368)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.processResults(AbstractLogMinerEventProcessor.java:314)
        at io.debezium.connector.oracle.logminer.processor.AbstractLogMinerEventProcessor.process(AbstractLogMinerEventProcessor.java:235)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:248)
        ... 9 more
Caused by: org.antlr.v4.runtime.InputMismatchException
        at org.antlr.v4.runtime.DefaultErrorStrategy.sync(DefaultErrorStrategy.java:270)
        at io.debezium.ddl.parser.oracle.generated.PlSqlParser.sql_script(PlSqlParser.java:2129)
        ... 21 more
