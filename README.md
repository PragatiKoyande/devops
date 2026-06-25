2026-06-25 11:12:41 INFO  [org.apache.kafka.clients.consumer.internals.ConsumerCoordinator] (pool-7-thread-1) [Consumer clientId=fincore-schemahistory, groupId=fincore-schemahistory] Request joining group due to: consumer pro-actively leaving the group
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.consumer for fincore-schemahistory unregistered
2026-06-25 11:12:42 INFO  [io.debezium.relational.history.SchemaHistoryMetrics] (pool-7-thread-1) Finished database schema history recovery of 617 change(s) in 4662 ms
2026-06-25 11:12:42 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Mapper for type '-3' not found.
2026-06-25 11:12:42 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Mapper for type '-3' not found.
2026-06-25 11:12:42 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."MENU_ITEMS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-06-25 11:12:42 WARN  [io.debezium.connector.oracle.OracleDefaultValueConverter] (pool-7-thread-1) Cannot parse column default value '"FINCORE"."MENU_ITEMS_SEQ"."NEXTVAL"' to type '2'.  Expression evaluation is not supported.
2026-06-25 11:12:42 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = SignalProcessor
2026-06-25 11:12:42 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = change-event-source-coordinator
2026-06-25 11:12:42 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Requested thread factory for connector OracleConnector, id = fincore named = blocking-snapshot
2026-06-25 11:12:42 INFO  [io.debezium.util.Threads] (pool-7-thread-1) Creating thread debezium-oracleconnector-fincore-change-event-source-coordinator
2026-06-25 11:12:42 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Metrics registered
2026-06-25 11:12:42 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Context created
2026-06-25 11:12:42 INFO  [io.debezium.connector.oracle.OracleSnapshotChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) The previous offset has been found.
2026-06-25 11:12:42 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Snapshot ended with SnapshotResult [status=SKIPPED, offset=OracleOffsetContext [scn=119680689, commit_scn=["119680767:1:0a001d00ed3e0100"]]]
2026-06-25 11:12:42 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Connected metrics set to 'true'
2026-06-25 11:12:42 INFO  [io.debezium.pipeline.signal.SignalProcessor] (debezium-oracleconnector-fincore-change-event-source-coordinator) SignalProcessor started. Scheduling it every 5000ms
2026-06-25 11:12:42 INFO  [io.debezium.util.Threads] (debezium-oracleconnector-fincore-change-event-source-coordinator) Creating thread debezium-oracleconnector-fincore-SignalProcessor
2026-06-25 11:12:42 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Starting streaming
2026-06-25 11:12:42 ERROR [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Mining session stopped due to error.: io.debezium.DebeziumException: Online REDO LOG files or archive log files do not contain the offset scn 119680689.  Please perform a new snapshot.
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:166)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)

2026-06-25 11:12:42 ERROR [io.debezium.pipeline.ErrorHandler] (debezium-oracleconnector-fincore-change-event-source-coordinator) Producer failure: io.debezium.DebeziumException: Online REDO LOG files or archive log files do not contain the offset scn 119680689.  Please perform a new snapshot.
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:166)
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:62)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.streamEvents(ChangeEventSourceCoordinator.java:271)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.executeChangeEventSources(ChangeEventSourceCoordinator.java:194)
        at io.debezium.pipeline.ChangeEventSourceCoordinator.lambda$start$0(ChangeEventSourceCoordinator.java:137)
        at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
        at java.base/java.lang.Thread.run(Thread.java:829)

2026-06-25 11:12:42 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) startScn=119680689, endScn=null
2026-06-25 11:12:42 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Streaming metrics dump: LogMinerStreamingChangeEventSourceMetrics{connectorConfig=io.debezium.connector.oracle.OracleConnectorConfig@453bfcdc, startTime=2026-06-25T11:12:42.352890Z, clock=SystemClock[Z], currentScn=null, offsetScn=null, commitScn=null, oldestScn=null, oldestScnTime=null, currentLogFileNames=[Ljava.lang.String;@28cc6c12, redoLogStatuses=[Ljava.lang.String;@45ac6011, databaseZoneOffset=Z, batchSize=50000, logSwitchCount=0, logMinerQueryCount=0, sleepTime=1000, minimumLogsMined=0, maximumLogsMined=0, maxBatchProcessingThroughput=0, timeDifference=0, processedRowsCount=0, activeTransactionCount=0, rolledBackTransactionCount=0, oversizedTransactionCount=0, changesCount=0, scnFreezeCount=0, batchProcessingDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@312b9e3f, fetchQueryDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@2b6c59da, commitDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@608b1c59, lagFromSourceDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@460144b1, miningSessionStartupDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@2bb6e028, parseTimeDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@62ddde0d, resultSetNextDuration=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$DurationHistogramMetric@5a0c6fdb, userGlobalAreaMemory=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$MaxLongValueMetric@16e49ce7, processGlobalAreaMemory=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$MaxLongValueMetric@a4f89b3, abandonedTransactionIds=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$LRUSet@6ee1341, rolledBackTransactionIds=io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics$LRUSet@3f25c6f0} io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSourceMetrics@b9b3fb
2026-06-25 11:12:42 INFO  [io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource] (debezium-oracleconnector-fincore-change-event-source-coordinator) Offsets: OracleOffsetContext [scn=119680689, commit_scn=["119680767:1:0a001d00ed3e0100"]]
2026-06-25 11:12:42 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Finished streaming
2026-06-25 11:12:42 INFO  [io.debezium.pipeline.ChangeEventSourceCoordinator] (debezium-oracleconnector-fincore-change-event-source-coordinator) Connected metrics set to 'false'
2026-06-25 11:12:42 INFO  [io.debezium.embedded.EmbeddedEngine] (pool-7-thread-1) Stopping the task and engine
2026-06-25 11:12:42 INFO  [io.debezium.connector.common.BaseSourceTask] (pool-7-thread-1) Stopping down connector
2026-06-25 11:12:42 INFO  [io.debezium.pipeline.signal.SignalProcessor] (pool-7-thread-1) SignalProcessor stopped
2026-06-25 11:12:42 INFO  [io.debezium.service.DefaultServiceRegistry] (pool-7-thread-1) Debezium ServiceRegistry stopped.
2026-06-25 11:12:42 INFO  [io.debezium.jdbc.JdbcConnection] (pool-9-thread-1) Connection gracefully closed
2026-06-25 11:12:42 INFO  [io.debezium.jdbc.JdbcConnection] (pool-10-thread-1) Connection gracefully closed
2026-06-25 11:12:42 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (pool-7-thread-1) [Producer clientId=fincore-schemahistory] Closing the Kafka producer with timeoutMillis = 30000 ms.
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics scheduler closed
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.metrics.Metrics] (pool-7-thread-1) Metrics reporters closed
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.utils.AppInfoParser] (pool-7-thread-1) App info kafka.producer for fincore-schemahistory unregistered
2026-06-25 11:12:42 INFO  [org.apache.kafka.connect.storage.FileOffsetBackingStore] (pool-7-thread-1) Stopped FileOffsetBackingStore
2026-06-25 11:12:42 ERROR [io.debezium.server.ConnectorLifecycle] (pool-7-thread-1) Connector completed: success = 'false', message = 'Error while trying to run connector class 'io.debezium.connector.oracle.OracleConnector'', error = 'org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.': org.apache.kafka.connect.errors.ConnectException: An exception occurred in the change event producer. This connector will be stopped.
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
Caused by: io.debezium.DebeziumException: Online REDO LOG files or archive log files do not contain the offset scn 119680689.  Please perform a new snapshot.
        at io.debezium.connector.oracle.logminer.LogMinerStreamingChangeEventSource.execute(LogMinerStreamingChangeEventSource.java:166)
        ... 9 more

2026-06-25 11:12:42 INFO  [io.debezium.server.DebeziumServer] (main) Received request to stop the engine
2026-06-25 11:12:42 INFO  [io.debezium.embedded.EmbeddedEngine] (main) Stopping the embedded engine
2026-06-25 11:12:42 INFO  [io.debezium.server.kafka.KafkaChangeConsumer] (main) consumer destroyed...
2026-06-25 11:12:42 INFO  [org.apache.kafka.clients.producer.KafkaProducer] (main) [Producer clientId=producer-1] Closing the Kafka producer with timeoutMillis = 5000 ms.
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics scheduler closed
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Closing reporter org.apache.kafka.common.metrics.JmxReporter
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.metrics.Metrics] (main) Metrics reporters closed
2026-06-25 11:12:42 INFO  [org.apache.kafka.common.utils.AppInfoParser] (main) App info kafka.producer for producer-1 unregistered
2026-06-25 11:12:42 INFO  [io.quarkus] (main) debezium-server-dist stopped in 0.047s
