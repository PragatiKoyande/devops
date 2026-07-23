log4j2.xml ::
<?xml version="1.0" encoding="UTF-8" ?>
<!--
 ~ Licensed to the Apache Software Foundation (ASF) under one
 ~ or more contributor license agreements.  See the NOTICE file
 ~ distributed with this work for additional information
 ~ regarding copyright ownership.  The ASF licenses this file
 ~ to you under the Apache License, Version 2.0 (the
 ~ "License"); you may not use this file except in compliance
 ~ with the License.  You may obtain a copy of the License at
 ~
 ~   http://www.apache.org/licenses/LICENSE-2.0
 ~
 ~ Unless required by applicable law or agreed to in writing,
 ~ software distributed under the License is distributed on an
 ~ "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
 ~ KIND, either express or implied.  See the License for the
 ~ specific language governing permissions and limitations
 ~ under the License.
-->

<Configuration status="WARN">
  <Properties>
    <!-- to change log directory, set DRUID_LOG_DIR environment variable to your directory before launching Druid -->
    <Property name="druid.log.path" value="log" />
  </Properties>

  <Appenders>
    <Console name="Console" target="SYSTEM_OUT">
      <PatternLayout pattern="%d{ISO8601} %p [%t] %c -%notEmpty{ [%markerSimpleName]} %m%n"/>
    </Console>

    <!-- Rolling Files-->
    <RollingRandomAccessFile name="FileAppender"
                             fileName="${sys:druid.log.path}/${sys:druid.node.type}.log"
                             filePattern="${sys:druid.log.path}/${sys:druid.node.type}.%d{yyyyMMdd}.log">
      <PatternLayout pattern="%d{ISO8601} %p [%t] %c -%notEmpty{ [%markerSimpleName]} %m%n"/>
      <Policies>
        <TimeBasedTriggeringPolicy interval="1" modulate="true"/>
      </Policies>
      <DefaultRolloverStrategy>
        <Delete basePath="${sys:druid.log.path}/" maxDepth="1">
          <IfFileName glob="*.log" />
          <IfLastModified age="7d" />
        </Delete>
      </DefaultRolloverStrategy>
    </RollingRandomAccessFile>

    <Routing name="RoutingAppender">
      <Routes pattern="$${ctx:task.log.id}">
        <!-- Task logs on CliIndexer should go to dedicated file -->
        <Route>
          <File name="task-${ctx:task.log.id}" fileName="${ctx:task.log.file}">
            <PatternLayout pattern="%d{ISO8601} %p [%t] %c -%notEmpty{ [%markerSimpleName]} %m%n"/>
          </File>
        </Route>

        <!-- Default route to send non-task logs to the usual FileAppender -->
        <Route key="$${ctx:task.log.id}" ref="FileAppender"/>
      </Routes>
    </Routing>

  </Appenders>

  <Loggers>
    <Root level="info">
      <AppenderRef ref="RoutingAppender"/>
    </Root>

    <!-- Set level="debug" to see stack traces for query errors -->
    <Logger name="org.apache.druid.server.QueryResource" level="info" additivity="false">
      <Appender-ref ref="RoutingAppender"/>
    </Logger>
    <Logger name="org.apache.druid.server.QueryLifecycle" level="info" additivity="false">
      <Appender-ref ref="RoutingAppender"/>
    </Logger>

    <!-- Set level="debug" or "trace" to see more Coordinator details (segment balancing, load/drop rules, etc) -->
    <Logger name="org.apache.druid.server.coordinator" level="info" additivity="false">
      <Appender-ref ref="RoutingAppender"/>
    </Logger>

    <!-- Set level="debug" to see low-level details about segments and ingestion -->
    <Logger name="org.apache.druid.segment" level="info" additivity="false">
      <Appender-ref ref="RoutingAppender"/>
    </Logger>

    <!-- Set level="debug" to see more information about extension initialization -->
    <Logger name="org.apache.druid.initialization" level="info" additivity="false">
      <Appender-ref ref="RoutingAppender"/>
    </Logger>

    <!-- Quieter logging at startup -->
    <Logger name="com.sun.jersey.guice" level="warn" additivity="false">
      <Appender-ref ref="RoutingAppender"/>
    </Logger>

    <!-- Quieter KafkaSupervisors -->
    <Logger name="org.apache.kafka.clients.consumer.internals" level="warn" additivity="false">
      <Appender-ref ref="RoutingAppender"/>
    </Logger>
    <!--Added New Conf for Request Logging -->
    <Logger name="org.apache.druid.server.LoggingRequestLogger" level="info" additivity="false">
      <Appender-ref ref="RoutingAppender"/>
    </Logger>
    <!--Added New Conf for Request Logging -->
    <Logger name="org.apache.druid.server.log" level="info" additivity="false">
      <Appender-ref ref="RoutingAppender"/>
    </Logger>
  </Loggers>
</Configuration>

broker-runtime.properties
druid.service=druid/broker
druid.host=fcproddruidbroker1
druid.enablePlaintextPort=false

# HTTP server settings
druid.server.http.numThreads=40
druid.server.http.queueSize=200

#Max Query Execution Time(30 Min)
druid.server.http.maxQueryTimeout=1800000

druid.discovery.curator.path=/druid/discovery

# ===============================
# Zookeeper Configuration
# ===============================
druid.zk.service.host=jn1:2281,jn2:2281,jn3:2281,jn4:2281,jn5:2281,jn6:2281,jn7:2281
druid.zk.paths.base=/druid

# ===============================
# Metadata Storage (PostgreSQL)
# ===============================
druid.metadata.storage.type=postgresql
druid.metadata.storage.connector.connectURI=jdbc:postgresql://fcprodhdfsjn7:5435/fincore
druid.metadata.storage.connector.user=druid
druid.metadata.storage.connector.password=Password#1234

# HTTP client settings
druid.broker.http.numConnections=80
druid.broker.http.maxQueuedBytes=104857600

# Processing threads and buffers
druid.processing.numThreads=7
druid.processing.buffer.sizeBytes=268435456
druid.processing.numMergeBuffers=2
druid.processing.tmpDir=var/druid/processing

# Query cache disabled -- push down caching and merging instead
druid.cache.type=caffeine
#2 GB Cache
druid.cache.sizeInBytes=1073741824
druid.broker.cache.useCache=true
druid.broker.cache.populateCache=true

# Enable HTTPS
druid.enableTlsPort=true
druid.server.https.enable=true
druid.tlsPort=8283
druid.server.https.keyStorePath=/media/production-setup/apache-druid-34.0.0/ssl/druid-keystore.jks
druid.server.https.keyStorePassword=DruidPass123

# Shared Truststore (common for all nodes)
druid.server.https.trustStoreType=JKS
druid.server.https.trustStorePath=/media/production-setup/apache-druid-34.0.0/ssl/truststore.jks
druid.server.https.trustStorePassword=DruidPass123

druid.request.logging.type=slf4j
#druid.request.logging.dir=/media/production-setup/apache-druid-34.0.0/log/
#druid.request.logging.filePattern='broker.'yyyy-mm-dd'.log'
#druid.request.logging.durationToRetain=P7D
#druid.request.logging.manager.type=log
#druid.emitter=noop


common-runtime.properties

# ===============================
# Extensions
# ===============================
druid.extensions.directory=extensions
druid.extensions.loadList=["postgresql-metadata-storage","simple-client-sslcontext","druid-parquet-extensions","druid-avro-extensions","druid-kafka-indexing-service","druid-deltalake-extensions"]
#druid.extensions.loadList=["postgresql-metadata-storage","simple-client-sslcontext","druid-hdfs-storage","druid-parquet-extensions","druid-deltalake-extensions","druid-avro-extensions","druid-kafka-indexing-service"]
#druid.extensions.hadoopDependenciesDir=hadoop-dependencies

# ===============================
# Metadata Storage (PostgreSQL)
# ===============================
#druid.metadata.storage.type=postgresql
#druid.metadata.storage.connector.connectURI=jdbc:postgresql://fcprodhdfsjn7:5435/druid
#druid.metadata.storage.connector.user=druid
#druid.metadata.storage.connector.password=Password#1234

# ===============================
# Zookeeper Configuration
# ===============================
druid.zk.service.host=jn1:2281,jn2:2281,jn3:2281,jn4:2281,jn5:2281
druid.zk.paths.base=/druid

# ===============================
# Deep Storage
# ===============================
#druid.storage.type=local
#druid.storage.storageDirectory=var/druid/segments


# Add the new HDFS deep storage settings


# ===============================
# Indexing Logs (MiddleManager Task Logs)
# ===============================
#druid.indexer.logs.type=file
#druid.indexer.logs.directory=var/druid/indexing-logs

# ===============================
# Service Discovery (used by all nodes)
# ===============================
druid.selectors.indexing.serviceName=druid/overlord
druid.selectors.coordinator.serviceName=druid/coordinator

# ===============================
# Coordinator and Overlord Properties
# ===============================
druid.coordinator.startDelay=PT30S
druid.coordinator.period=PT30S

druid.indexer.queue.startDelay=PT30S
druid.indexer.runner.type=remote
druid.indexer.storage.type=metadata

# ===============================
# Logging Configuration
# ===============================
#druid.monitoring.monitors=["org.apache.druid.java.util.metrics.JvmMonitor"]
#druid.emitter=logging
#druid.emitter.logging.logLevel=info
#druid.startup.logging.logProperties=true

# ===============================
# Time and Locale
# ===============================
user.timezone=UTC
user.language=en

####################################################################
# HTTPS / SSL Configuration (applies to all nodes)
####################################################################

# --- Enable HTTPS globally ---
druid.enableTlsPort=true
druid.server.https.enable=true
# Each node will define its own druid.server.https.port and druid.server.https.keyStorePath in its runtime.properties

# --- Enforce secure inter-node communication ---
druid.internal.http.useSSL=true
druid.client.https.enabled=true

# --- Keystore (each node overrides path and password in its runtime.properties) ---
druid.server.https.keyStoreType=JKS

# --- Common Truststore (shared by all nodes) ---
druid.server.https.trustStoreType=JKS
druid.server.https.trustStorePath=/media/production-setup/apache-druid-34.0.0/ssl/truststore.jks
druid.server.https.trustStorePassword=DruidPass123

# --- Druid Internal HTTPS Client (used by nodes to talk securely) ---
druid.client.https.trustStoreType=JKS
druid.client.https.trustStorePath=/media/production-setup/apache-druid-34.0.0/ssl/truststore.jks
druid.client.https.trustStorePassword=DruidPass123

####################################################################
# Optional: JVM / Threading / Misc tuning
####################################################################
# Node-specific JVM tuning goes into each node’s jvm.config

#druid.request.logging.type=slf4j
#druid.request.logging.dir=/media/production-setup/apache-druid-34.0.0/log/
#druid.request.logging.filePattern='router.'yyyymmdd'.log'
#druid.request.logging.durationToRetain=P7D
#druid.request.logging.manager.type=log

#druid.request.logging.setMDC=true
#druid.request.logging.setCont:WqextMDC=true
# BEGIN ANSIBLE MANAGED ZK PATHS
druid.zk.paths.base=/druid
druid.zk.paths.announcementsPath=/druid/announcements
druid.zk.paths.indexer.announcementsPath=/druid/indexer/announcements
# END ANSIBLE MANAGED ZK PATHS
