
{"@timestamp":"2026-06-26T11:17:55.865127054+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.clients.consumer.ConsumerConfig","message":"ConsumerConfig values: \n\tallow.auto.create.topics = true\n\tauto.commit.interval.ms = 5000\n\tauto.include.jmx.reporter = true\n\tauto.offset.reset = earliest\n\tbootstrap.servers = [kafka-0.kafka.uat-cbops1.svc.cluster.local:9092]\n\tcheck.crcs = true\n\tclient.dns.lookup = use_all_dns_ips\n\tclient.id = consumer-notification-service-group-2\n\tclient.rack = \n\tconnections.max.idle.ms = 540000\n\tdefault.api.timeout.ms = 60000\n\tenable.auto.commit = false\n\tenable.metrics.push = true\n\texclude.internal.topics = true\n\tfetch.max.bytes = 52428800\n\tfetch.max.wait.ms = 500\n\tfetch.min.bytes = 1\n\tgroup.id = notification-service-group\n\tgroup.instance.id = null\n\tgroup.protocol = classic\n\tgroup.remote.assignor = null\n\theartbeat.interval.ms = 3000\n\tinterceptor.classes = []\n\tinternal.leave.group.on.close = true\n\tinternal.throw.on.fetch.stable.offset.unsupported = false\n\tisolation.level = read_uncommitted\n\tkey.deserializer = class org.apache.kafka.common.serialization.StringDeserializer\n\tmax.partition.fetch.bytes = 1048576\n\tmax.poll.interval.ms = 300000\n\tmax.poll.records = 500\n\tmetadata.max.age.ms = 300000\n\tmetric.reporters = []\n\tmetrics.num.samples = 2\n\tmetrics.recording.level = INFO\n\tmetrics.sample.window.ms = 30000\n\tpartition.assignment.strategy = [class org.apache.kafka.clients.consumer.RangeAssignor, class org.apache.kafka.clients.consumer.CooperativeStickyAssignor]\n\treceive.buffer.bytes = 65536\n\treconnect.backoff.max.ms = 1000\n\treconnect.backoff.ms = 50\n\trequest.timeout.ms = 30000\n\tretry.backoff.max.ms = 1000\n\tretry.backoff.ms = 100\n\tsasl.client.callback.handler.class = null\n\tsasl.jaas.config = null\n\tsasl.kerberos.kinit.cmd = /usr/bin/kinit\n\tsasl.kerberos.min.time.before.relogin = 60000\n\tsasl.kerberos.service.name = null\n\tsasl.kerberos.ticket.renew.jitter = 0.05\n\tsasl.kerberos.ticket.renew.window.factor = 0.8\n\tsasl.login.callback.handler.class = null\n\tsasl.login.class = null\n\tsasl.login.connect.timeout.ms = null\n\tsasl.login.read.timeout.ms = null\n\tsasl.login.refresh.buffer.seconds = 300\n\tsasl.login.refresh.min.period.seconds = 60\n\tsasl.login.refresh.window.factor = 0.8\n\tsasl.login.refresh.window.jitter = 0.05\n\tsasl.login.retry.backoff.max.ms = 10000\n\tsasl.login.retry.backoff.ms = 100\n\tsasl.mechanism = GSSAPI\n\tsasl.oauthbearer.clock.skew.seconds = 30\n\tsasl.oauthbearer.expected.audience = null\n\tsasl.oauthbearer.expected.issuer = null\n\tsasl.oauthbearer.jwks.endpoint.refresh.ms = 3600000\n\tsasl.oauthbearer.jwks.endpoint.retry.backoff.max.ms = 10000\n\tsasl.oauthbearer.jwks.endpoint.retry.backoff.ms = 100\n\tsasl.oauthbearer.jwks.endpoint.url = null\n\tsasl.oauthbearer.scope.claim.name = scope\n\tsasl.oauthbearer.sub.claim.name = sub\n\tsasl.oauthbearer.token.endpoint.url = null\n\tsecurity.protocol = PLAINTEXT\n\tsecurity.providers = null\n\tsend.buffer.bytes = 131072\n\tsession.timeout.ms = 45000\n\tsocket.connection.setup.timeout.max.ms = 30000\n\tsocket.connection.setup.timeout.ms = 10000\n\tssl.cipher.suites = null\n\tssl.enabled.protocols = [TLSv1.2, TLSv1.3]\n\tssl.endpoint.identification.algorithm = https\n\tssl.engine.factory.class = null\n\tssl.key.password = null\n\tssl.keymanager.algorithm = SunX509\n\tssl.keystore.certificate.chain = null\n\tssl.keystore.key = null\n\tssl.keystore.location = null\n\tssl.keystore.password = null\n\tssl.keystore.type = JKS\n\tssl.protocol = TLSv1.3\n\tssl.provider = null\n\tssl.secure.random.implementation = null\n\tssl.trustmanager.algorithm = PKIX\n\tssl.truststore.certificates = null\n\tssl.truststore.location = null\n\tssl.truststore.password = null\n\tssl.truststore.type = JKS\n\tvalue.deserializer = class org.springframework.kafka.support.serializer.JsonDeserializer\n","stack_trace":""}
2026-06-26 05:47:55.866 INFO  [main] o.a.k.c.t.i.KafkaMetricsCollector$StateLedger: initializing Kafka metrics collector
{"@timestamp":"2026-06-26T11:17:55.866035835+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.c.t.i.KafkaMetricsCollector","message":"initializing Kafka metrics collector","stack_trace":""}
2026-06-26 05:47:55.874 INFO  [main] o.a.k.c.u.AppInfoParser$AppInfo: Kafka version: 3.7.0
{"@timestamp":"2026-06-26T11:17:55.874028978+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.kafka.common.utils.AppInfoParser","message":"Kafka version: 3.7.0","stack_trace":""}
2026-06-26 05:47:55.874 INFO  [main] o.a.k.c.u.AppInfoParser$AppInfo: Kafka commitId: 2ae524ed625438c5
{"@timestamp":"2026-06-26T11:17:55.874401931+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.kafka.common.utils.AppInfoParser","message":"Kafka commitId: 2ae524ed625438c5","stack_trace":""}
2026-06-26 05:47:55.874 INFO  [main] o.a.k.c.u.AppInfoParser$AppInfo: Kafka startTimeMs: 1782452875873
{"@timestamp":"2026-06-26T11:17:55.874509779+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.kafka.common.utils.AppInfoParser","message":"Kafka startTimeMs: 1782452875873","stack_trace":""}
2026-06-26 05:47:55.874 INFO  [main] o.a.k.c.c.i.LegacyKafkaConsumer: [Consumer clientId=consumer-notification-service-group-2, groupId=notification-service-group] Subscribed to topic(s): fincore.FINCORE.NOTIFICATIONS
{"@timestamp":"2026-06-26T11:17:55.87486188+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.c.c.internals.LegacyKafkaConsumer","message":"[Consumer clientId=consumer-notification-service-group-2, groupId=notification-service-group] Subscribed to topic(s): fincore.FINCORE.NOTIFICATIONS","stack_trace":""}
2026-06-26 05:47:55.877 INFO  [main] o.a.k.c.c.AbstractConfig: ConsumerConfig values:
        allow.auto.create.topics = true
        auto.commit.interval.ms = 5000
        auto.include.jmx.reporter = true
        auto.offset.reset = earliest
        bootstrap.servers = [kafka-0.kafka.uat-cbops1.svc.cluster.local:9092]
        check.crcs = true
        client.dns.lookup = use_all_dns_ips
        client.id = consumer-notification-dispatch-workers-3
        client.rack =
        connections.max.idle.ms = 540000
        default.api.timeout.ms = 60000
        enable.auto.commit = false
        enable.metrics.push = true
        exclude.internal.topics = true
        fetch.max.bytes = 52428800
        fetch.max.wait.ms = 500
        fetch.min.bytes = 1
        group.id = notification-dispatch-workers
        group.instance.id = null
        group.protocol = classic
        group.remote.assignor = null
        heartbeat.interval.ms = 3000
        interceptor.classes = []
        internal.leave.group.on.close = true
        internal.throw.on.fetch.stable.offset.unsupported = false
        isolation.level = read_uncommitted
        key.deserializer = class org.apache.kafka.common.serialization.StringDeserializer
        max.partition.fetch.bytes = 1048576
        max.poll.interval.ms = 300000
        max.poll.records = 500
        metadata.max.age.ms = 300000
        metric.reporters = []
        metrics.num.samples = 2
        metrics.recording.level = INFO
        metrics.sample.window.ms = 30000
        partition.assignment.strategy = [class org.apache.kafka.clients.consumer.RangeAssignor, class org.apache.kafka.clients.consumer.CooperativeStickyAssignor]
        receive.buffer.bytes = 65536
        reconnect.backoff.max.ms = 1000
        reconnect.backoff.ms = 50
        request.timeout.ms = 30000
        retry.backoff.max.ms = 1000
        retry.backoff.ms = 100
        sasl.client.callback.handler.class = null
        sasl.jaas.config = null
        sasl.kerberos.kinit.cmd = /usr/bin/kinit
        sasl.kerberos.min.time.before.relogin = 60000
        sasl.kerberos.service.name = null
        sasl.kerberos.ticket.renew.jitter = 0.05
        sasl.kerberos.ticket.renew.window.factor = 0.8
        sasl.login.callback.handler.class = null
        sasl.login.class = null
        sasl.login.connect.timeout.ms = null
        sasl.login.read.timeout.ms = null
        sasl.login.refresh.buffer.seconds = 300
        sasl.login.refresh.min.period.seconds = 60
        sasl.login.refresh.window.factor = 0.8
        sasl.login.refresh.window.jitter = 0.05
        sasl.login.retry.backoff.max.ms = 10000
        sasl.login.retry.backoff.ms = 100
        sasl.mechanism = GSSAPI
        sasl.oauthbearer.clock.skew.seconds = 30
        sasl.oauthbearer.expected.audience = null
        sasl.oauthbearer.expected.issuer = null
        sasl.oauthbearer.jwks.endpoint.refresh.ms = 3600000
        sasl.oauthbearer.jwks.endpoint.retry.backoff.max.ms = 10000
        sasl.oauthbearer.jwks.endpoint.retry.backoff.ms = 100
        sasl.oauthbearer.jwks.endpoint.url = null
        sasl.oauthbearer.scope.claim.name = scope
        sasl.oauthbearer.sub.claim.name = sub
        sasl.oauthbearer.token.endpoint.url = null
        security.protocol = PLAINTEXT
        security.providers = null
        send.buffer.bytes = 131072
        session.timeout.ms = 45000
        socket.connection.setup.timeout.max.ms = 30000
        socket.connection.setup.timeout.ms = 10000
        ssl.cipher.suites = null
        ssl.enabled.protocols = [TLSv1.2, TLSv1.3]
        ssl.endpoint.identification.algorithm = https
        ssl.engine.factory.class = null
        ssl.key.password = null
        ssl.keymanager.algorithm = SunX509
        ssl.keystore.certificate.chain = null
        ssl.keystore.key = null
        ssl.keystore.location = null
        ssl.keystore.password = null
        ssl.keystore.type = JKS
        ssl.protocol = TLSv1.3
        ssl.provider = null
        ssl.secure.random.implementation = null
        ssl.trustmanager.algorithm = PKIX
        ssl.truststore.certificates = null
        ssl.truststore.location = null
        ssl.truststore.password = null
        ssl.truststore.type = JKS
        value.deserializer = class org.springframework.kafka.support.serializer.JsonDeserializer

{"@timestamp":"2026-06-26T11:17:55.87717472+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.clients.consumer.ConsumerConfig","message":"ConsumerConfig values: \n\tallow.auto.create.topics = true\n\tauto.commit.interval.ms = 5000\n\tauto.include.jmx.reporter = true\n\tauto.offset.reset = earliest\n\tbootstrap.servers = [kafka-0.kafka.uat-cbops1.svc.cluster.local:9092]\n\tcheck.crcs = true\n\tclient.dns.lookup = use_all_dns_ips\n\tclient.id = consumer-notification-dispatch-workers-3\n\tclient.rack = \n\tconnections.max.idle.ms = 540000\n\tdefault.api.timeout.ms = 60000\n\tenable.auto.commit = false\n\tenable.metrics.push = true\n\texclude.internal.topics = true\n\tfetch.max.bytes = 52428800\n\tfetch.max.wait.ms = 500\n\tfetch.min.bytes = 1\n\tgroup.id = notification-dispatch-workers\n\tgroup.instance.id = null\n\tgroup.protocol = classic\n\tgroup.remote.assignor = null\n\theartbeat.interval.ms = 3000\n\tinterceptor.classes = []\n\tinternal.leave.group.on.close = true\n\tinternal.throw.on.fetch.stable.offset.unsupported = false\n\tisolation.level = read_uncommitted\n\tkey.deserializer = class org.apache.kafka.common.serialization.StringDeserializer\n\tmax.partition.fetch.bytes = 1048576\n\tmax.poll.interval.ms = 300000\n\tmax.poll.records = 500\n\tmetadata.max.age.ms = 300000\n\tmetric.reporters = []\n\tmetrics.num.samples = 2\n\tmetrics.recording.level = INFO\n\tmetrics.sample.window.ms = 30000\n\tpartition.assignment.strategy = [class org.apache.kafka.clients.consumer.RangeAssignor, class org.apache.kafka.clients.consumer.CooperativeStickyAssignor]\n\treceive.buffer.bytes = 65536\n\treconnect.backoff.max.ms = 1000\n\treconnect.backoff.ms = 50\n\trequest.timeout.ms = 30000\n\tretry.backoff.max.ms = 1000\n\tretry.backoff.ms = 100\n\tsasl.client.callback.handler.class = null\n\tsasl.jaas.config = null\n\tsasl.kerberos.kinit.cmd = /usr/bin/kinit\n\tsasl.kerberos.min.time.before.relogin = 60000\n\tsasl.kerberos.service.name = null\n\tsasl.kerberos.ticket.renew.jitter = 0.05\n\tsasl.kerberos.ticket.renew.window.factor = 0.8\n\tsasl.login.callback.handler.class = null\n\tsasl.login.class = null\n\tsasl.login.connect.timeout.ms = null\n\tsasl.login.read.timeout.ms = null\n\tsasl.login.refresh.buffer.seconds = 300\n\tsasl.login.refresh.min.period.seconds = 60\n\tsasl.login.refresh.window.factor = 0.8\n\tsasl.login.refresh.window.jitter = 0.05\n\tsasl.login.retry.backoff.max.ms = 10000\n\tsasl.login.retry.backoff.ms = 100\n\tsasl.mechanism = GSSAPI\n\tsasl.oauthbearer.clock.skew.seconds = 30\n\tsasl.oauthbearer.expected.audience = null\n\tsasl.oauthbearer.expected.issuer = null\n\tsasl.oauthbearer.jwks.endpoint.refresh.ms = 3600000\n\tsasl.oauthbearer.jwks.endpoint.retry.backoff.max.ms = 10000\n\tsasl.oauthbearer.jwks.endpoint.retry.backoff.ms = 100\n\tsasl.oauthbearer.jwks.endpoint.url = null\n\tsasl.oauthbearer.scope.claim.name = scope\n\tsasl.oauthbearer.sub.claim.name = sub\n\tsasl.oauthbearer.token.endpoint.url = null\n\tsecurity.protocol = PLAINTEXT\n\tsecurity.providers = null\n\tsend.buffer.bytes = 131072\n\tsession.timeout.ms = 45000\n\tsocket.connection.setup.timeout.max.ms = 30000\n\tsocket.connection.setup.timeout.ms = 10000\n\tssl.cipher.suites = null\n\tssl.enabled.protocols = [TLSv1.2, TLSv1.3]\n\tssl.endpoint.identification.algorithm = https\n\tssl.engine.factory.class = null\n\tssl.key.password = null\n\tssl.keymanager.algorithm = SunX509\n\tssl.keystore.certificate.chain = null\n\tssl.keystore.key = null\n\tssl.keystore.location = null\n\tssl.keystore.password = null\n\tssl.keystore.type = JKS\n\tssl.protocol = TLSv1.3\n\tssl.provider = null\n\tssl.secure.random.implementation = null\n\tssl.trustmanager.algorithm = PKIX\n\tssl.truststore.certificates = null\n\tssl.truststore.location = null\n\tssl.truststore.password = null\n\tssl.truststore.type = JKS\n\tvalue.deserializer = class org.springframework.kafka.support.serializer.JsonDeserializer\n","stack_trace":""}
2026-06-26 05:47:55.877 INFO  [main] o.a.k.c.t.i.KafkaMetricsCollector$StateLedger: initializing Kafka metrics collector
{"@timestamp":"2026-06-26T11:17:55.877948777+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.c.t.i.KafkaMetricsCollector","message":"initializing Kafka metrics collector","stack_trace":""}
2026-06-26 05:47:55.882 INFO  [main] o.a.k.c.c.AbstractConfig: These configurations '[spring.json.trusted.packages, spring.json.value.default.type, spring.json.use.type.headers]' were supplied but are not used yet.
{"@timestamp":"2026-06-26T11:17:55.882052582+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.clients.consumer.ConsumerConfig","message":"These configurations '[spring.json.trusted.packages, spring.json.value.default.type, spring.json.use.type.headers]' were supplied but are not used yet.","stack_trace":""}
2026-06-26 05:47:55.882 INFO  [main] o.a.k.c.u.AppInfoParser$AppInfo: Kafka version: 3.7.0
{"@timestamp":"2026-06-26T11:17:55.882402088+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.kafka.common.utils.AppInfoParser","message":"Kafka version: 3.7.0","stack_trace":""}
2026-06-26 05:47:55.882 INFO  [main] o.a.k.c.u.AppInfoParser$AppInfo: Kafka commitId: 2ae524ed625438c5
{"@timestamp":"2026-06-26T11:17:55.882571915+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.kafka.common.utils.AppInfoParser","message":"Kafka commitId: 2ae524ed625438c5","stack_trace":""}
2026-06-26 05:47:55.882 INFO  [main] o.a.k.c.u.AppInfoParser$AppInfo: Kafka startTimeMs: 1782452875882
{"@timestamp":"2026-06-26T11:17:55.882646123+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.kafka.common.utils.AppInfoParser","message":"Kafka startTimeMs: 1782452875882","stack_trace":""}
2026-06-26 05:47:55.883 INFO  [main] o.a.k.c.c.i.LegacyKafkaConsumer: [Consumer clientId=consumer-notification-dispatch-workers-3, groupId=notification-dispatch-workers] Subscribed to topic(s): notification.dispatch
{"@timestamp":"2026-06-26T11:17:55.883536272+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.c.c.internals.LegacyKafkaConsumer","message":"[Consumer clientId=consumer-notification-dispatch-workers-3, groupId=notification-dispatch-workers] Subscribed to topic(s): notification.dispatch","stack_trace":""}
2026-06-26 05:47:55.885 INFO  [main] o.a.k.c.c.AbstractConfig: ConsumerConfig values:
        allow.auto.create.topics = true
        auto.commit.interval.ms = 5000
        auto.include.jmx.reporter = true
        auto.offset.reset = earliest
        bootstrap.servers = [kafka-0.kafka.uat-cbops1.svc.cluster.local:9092]
        check.crcs = true
        client.dns.lookup = use_all_dns_ips
        client.id = consumer-notification-service-group-4
        client.rack =
        connections.max.idle.ms = 540000
        default.api.timeout.ms = 60000
        enable.auto.commit = false
        enable.metrics.push = true
        exclude.internal.topics = true
        fetch.max.bytes = 52428800
        fetch.max.wait.ms = 500
        fetch.min.bytes = 1
        group.id = notification-service-group
        group.instance.id = null
        group.protocol = classic
        group.remote.assignor = null
        heartbeat.interval.ms = 3000
        interceptor.classes = []
        internal.leave.group.on.close = true
        internal.throw.on.fetch.stable.offset.unsupported = false
        isolation.level = read_uncommitted
        key.deserializer = class org.apache.kafka.common.serialization.StringDeserializer
        max.partition.fetch.bytes = 1048576
        max.poll.interval.ms = 300000
        max.poll.records = 500
        metadata.max.age.ms = 300000
        metric.reporters = []
        metrics.num.samples = 2
        metrics.recording.level = INFO
        metrics.sample.window.ms = 30000
        partition.assignment.strategy = [class org.apache.kafka.clients.consumer.RangeAssignor, class org.apache.kafka.clients.consumer.CooperativeStickyAssignor]
        receive.buffer.bytes = 65536
        reconnect.backoff.max.ms = 1000
        reconnect.backoff.ms = 50
        request.timeout.ms = 30000
        retry.backoff.max.ms = 1000
        retry.backoff.ms = 100
        sasl.client.callback.handler.class = null
        sasl.jaas.config = null
        sasl.kerberos.kinit.cmd = /usr/bin/kinit
        sasl.kerberos.min.time.before.relogin = 60000
        sasl.kerberos.service.name = null
        sasl.kerberos.ticket.renew.jitter = 0.05
        sasl.kerberos.ticket.renew.window.factor = 0.8
        sasl.login.callback.handler.class = null
        sasl.login.class = null
        sasl.login.connect.timeout.ms = null
        sasl.login.read.timeout.ms = null
        sasl.login.refresh.buffer.seconds = 300
        sasl.login.refresh.min.period.seconds = 60
        sasl.login.refresh.window.factor = 0.8
        sasl.login.refresh.window.jitter = 0.05
        sasl.login.retry.backoff.max.ms = 10000
        sasl.login.retry.backoff.ms = 100
        sasl.mechanism = GSSAPI
        sasl.oauthbearer.clock.skew.seconds = 30
        sasl.oauthbearer.expected.audience = null
        sasl.oauthbearer.expected.issuer = null
        sasl.oauthbearer.jwks.endpoint.refresh.ms = 3600000
        sasl.oauthbearer.jwks.endpoint.retry.backoff.max.ms = 10000
        sasl.oauthbearer.jwks.endpoint.retry.backoff.ms = 100
        sasl.oauthbearer.jwks.endpoint.url = null
        sasl.oauthbearer.scope.claim.name = scope
        sasl.oauthbearer.sub.claim.name = sub
        sasl.oauthbearer.token.endpoint.url = null
        security.protocol = PLAINTEXT
        security.providers = null
        send.buffer.bytes = 131072
        session.timeout.ms = 45000
        socket.connection.setup.timeout.max.ms = 30000
        socket.connection.setup.timeout.ms = 10000
        ssl.cipher.suites = null
        ssl.enabled.protocols = [TLSv1.2, TLSv1.3]
        ssl.endpoint.identification.algorithm = https
        ssl.engine.factory.class = null
        ssl.key.password = null
        ssl.keymanager.algorithm = SunX509
        ssl.keystore.certificate.chain = null
        ssl.keystore.key = null
        ssl.keystore.location = null
        ssl.keystore.password = null
        ssl.keystore.type = JKS
        ssl.protocol = TLSv1.3
        ssl.provider = null
        ssl.secure.random.implementation = null
        ssl.trustmanager.algorithm = PKIX
        ssl.truststore.certificates = null
        ssl.truststore.location = null
        ssl.truststore.password = null
        ssl.truststore.type = JKS
        value.deserializer = class org.springframework.kafka.support.serializer.JsonDeserializer

{"@timestamp":"2026-06-26T11:17:55.885838471+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.clients.consumer.ConsumerConfig","message":"ConsumerConfig values: \n\tallow.auto.create.topics = true\n\tauto.commit.interval.ms = 5000\n\tauto.include.jmx.reporter = true\n\tauto.offset.reset = earliest\n\tbootstrap.servers = [kafka-0.kafka.uat-cbops1.svc.cluster.local:9092]\n\tcheck.crcs = true\n\tclient.dns.lookup = use_all_dns_ips\n\tclient.id = consumer-notification-service-group-4\n\tclient.rack = \n\tconnections.max.idle.ms = 540000\n\tdefault.api.timeout.ms = 60000\n\tenable.auto.commit = false\n\tenable.metrics.push = true\n\texclude.internal.topics = true\n\tfetch.max.bytes = 52428800\n\tfetch.max.wait.ms = 500\n\tfetch.min.bytes = 1\n\tgroup.id = notification-service-group\n\tgroup.instance.id = null\n\tgroup.protocol = classic\n\tgroup.remote.assignor = null\n\theartbeat.interval.ms = 3000\n\tinterceptor.classes = []\n\tinternal.leave.group.on.close = true\n\tinternal.throw.on.fetch.stable.offset.unsupported = false\n\tisolation.level = read_uncommitted\n\tkey.deserializer = class org.apache.kafka.common.serialization.StringDeserializer\n\tmax.partition.fetch.bytes = 1048576\n\tmax.poll.interval.ms = 300000\n\tmax.poll.records = 500\n\tmetadata.max.age.ms = 300000\n\tmetric.reporters = []\n\tmetrics.num.samples = 2\n\tmetrics.recording.level = INFO\n\tmetrics.sample.window.ms = 30000\n\tpartition.assignment.strategy = [class org.apache.kafka.clients.consumer.RangeAssignor, class org.apache.kafka.clients.consumer.CooperativeStickyAssignor]\n\treceive.buffer.bytes = 65536\n\treconnect.backoff.max.ms = 1000\n\treconnect.backoff.ms = 50\n\trequest.timeout.ms = 30000\n\tretry.backoff.max.ms = 1000\n\tretry.backoff.ms = 100\n\tsasl.client.callback.handler.class = null\n\tsasl.jaas.config = null\n\tsasl.kerberos.kinit.cmd = /usr/bin/kinit\n\tsasl.kerberos.min.time.before.relogin = 60000\n\tsasl.kerberos.service.name = null\n\tsasl.kerberos.ticket.renew.jitter = 0.05\n\tsasl.kerberos.ticket.renew.window.factor = 0.8\n\tsasl.login.callback.handler.class = null\n\tsasl.login.class = null\n\tsasl.login.connect.timeout.ms = null\n\tsasl.login.read.timeout.ms = null\n\tsasl.login.refresh.buffer.seconds = 300\n\tsasl.login.refresh.min.period.seconds = 60\n\tsasl.login.refresh.window.factor = 0.8\n\tsasl.login.refresh.window.jitter = 0.05\n\tsasl.login.retry.backoff.max.ms = 10000\n\tsasl.login.retry.backoff.ms = 100\n\tsasl.mechanism = GSSAPI\n\tsasl.oauthbearer.clock.skew.seconds = 30\n\tsasl.oauthbearer.expected.audience = null\n\tsasl.oauthbearer.expected.issuer = null\n\tsasl.oauthbearer.jwks.endpoint.refresh.ms = 3600000\n\tsasl.oauthbearer.jwks.endpoint.retry.backoff.max.ms = 10000\n\tsasl.oauthbearer.jwks.endpoint.retry.backoff.ms = 100\n\tsasl.oauthbearer.jwks.endpoint.url = null\n\tsasl.oauthbearer.scope.claim.name = scope\n\tsasl.oauthbearer.sub.claim.name = sub\n\tsasl.oauthbearer.token.endpoint.url = null\n\tsecurity.protocol = PLAINTEXT\n\tsecurity.providers = null\n\tsend.buffer.bytes = 131072\n\tsession.timeout.ms = 45000\n\tsocket.connection.setup.timeout.max.ms = 30000\n\tsocket.connection.setup.timeout.ms = 10000\n\tssl.cipher.suites = null\n\tssl.enabled.protocols = [TLSv1.2, TLSv1.3]\n\tssl.endpoint.identification.algorithm = https\n\tssl.engine.factory.class = null\n\tssl.key.password = null\n\tssl.keymanager.algorithm = SunX509\n\tssl.keystore.certificate.chain = null\n\tssl.keystore.key = null\n\tssl.keystore.location = null\n\tssl.keystore.password = null\n\tssl.keystore.type = JKS\n\tssl.protocol = TLSv1.3\n\tssl.provider = null\n\tssl.secure.random.implementation = null\n\tssl.trustmanager.algorithm = PKIX\n\tssl.truststore.certificates = null\n\tssl.truststore.location = null\n\tssl.truststore.password = null\n\tssl.truststore.type = JKS\n\tvalue.deserializer = class org.springframework.kafka.support.serializer.JsonDeserializer\n","stack_trace":""}
2026-06-26 05:47:55.886 INFO  [main] o.a.k.c.t.i.KafkaMetricsCollector$StateLedger: initializing Kafka metrics collector
{"@timestamp":"2026-06-26T11:17:55.886539598+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.c.t.i.KafkaMetricsCollector","message":"initializing Kafka metrics collector","stack_trace":""}
2026-06-26 05:47:55.890 INFO  [main] o.a.k.c.c.AbstractConfig: These configurations '[spring.json.trusted.packages, spring.json.value.default.type, spring.json.use.type.headers]' were supplied but are not used yet.
{"@timestamp":"2026-06-26T11:17:55.890609277+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.clients.consumer.ConsumerConfig","message":"These configurations '[spring.json.trusted.packages, spring.json.value.default.type, spring.json.use.type.headers]' were supplied but are not used yet.","stack_trace":""}
2026-06-26 05:47:55.891 INFO  [main] o.a.k.c.u.AppInfoParser$AppInfo: Kafka version: 3.7.0
{"@timestamp":"2026-06-26T11:17:55.891016971+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.kafka.common.utils.AppInfoParser","message":"Kafka version: 3.7.0","stack_trace":""}
2026-06-26 05:47:55.891 INFO  [main] o.a.k.c.u.AppInfoParser$AppInfo: Kafka commitId: 2ae524ed625438c5
{"@timestamp":"2026-06-26T11:17:55.891138186+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.kafka.common.utils.AppInfoParser","message":"Kafka commitId: 2ae524ed625438c5","stack_trace":""}
2026-06-26 05:47:55.891 INFO  [main] o.a.k.c.u.AppInfoParser$AppInfo: Kafka startTimeMs: 1782452875890
{"@timestamp":"2026-06-26T11:17:55.891223821+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.kafka.common.utils.AppInfoParser","message":"Kafka startTimeMs: 1782452875890","stack_trace":""}
2026-06-26 05:47:55.891 INFO  [main] o.a.k.c.c.i.LegacyKafkaConsumer: [Consumer clientId=consumer-notification-service-group-4, groupId=notification-service-group] Subscribed to topic(s): fincore.FINCORE.USER_ROLES
{"@timestamp":"2026-06-26T11:17:55.891594413+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"o.a.k.c.c.internals.LegacyKafkaConsumer","message":"[Consumer clientId=consumer-notification-service-group-4, groupId=notification-service-group] Subscribed to topic(s): fincore.FINCORE.USER_ROLES","stack_trace":""}
2026-06-26 05:47:56.454 INFO  [main] o.s.b.StartupInfoLogger: Started NotificationServiceApplication in 50.183 seconds (process running for 50.662)
{"@timestamp":"2026-06-26T11:17:56.454125708+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"c.f.N.NotificationServiceApplication","message":"Started NotificationServiceApplication in 50.183 seconds (process running for 50.662)","stack_trace":""}
2026-06-26 05:48:05.065 INFO  [org.springframework.kafka.KafkaListenerEndpointContainer#1-0-C-1] o.a.k.c.NetworkClient: [Consumer clientId=consumer-notification-service-group-4, groupId=notification-service-group] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 9125 ms.
{"@timestamp":"2026-06-26T11:18:05.065927781+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"org.apache.kafka.clients.NetworkClient","message":"[Consumer clientId=consumer-notification-service-group-4, groupId=notification-service-group] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 9125 ms.","stack_trace":""}
2026-06-26 05:48:05.066 WARN  [org.springframework.kafka.KafkaListenerEndpointContainer#1-0-C-1] o.a.k.c.NetworkClient$DefaultMetadataUpdater: [Consumer clientId=consumer-notification-service-group-4, groupId=notification-service-group] Bootstrap broker kafka-0.kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
{"@timestamp":"2026-06-26T11:18:05.06656221+05:30","level":"WARN","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"org.apache.kafka.clients.NetworkClient","message":"[Consumer clientId=consumer-notification-service-group-4, groupId=notification-service-group] Bootstrap broker kafka-0.kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected","stack_trace":""}
2026-06-26 05:48:05.456 INFO  [org.springframework.kafka.KafkaListenerEndpointContainer#0-0-C-1] o.a.k.c.NetworkClient: [Consumer clientId=consumer-notification-dispatch-workers-3, groupId=notification-dispatch-workers] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 9524 ms.
{"@timestamp":"2026-06-26T11:18:05.456799279+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"org.apache.kafka.clients.NetworkClient","message":"[Consumer clientId=consumer-notification-dispatch-workers-3, groupId=notification-dispatch-workers] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 9524 ms.","stack_trace":""}
2026-06-26 05:48:05.457 WARN  [org.springframework.kafka.KafkaListenerEndpointContainer#0-0-C-1] o.a.k.c.NetworkClient$DefaultMetadataUpdater: [Consumer clientId=consumer-notification-dispatch-workers-3, groupId=notification-dispatch-workers] Bootstrap broker kafka-0.kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
{"@timestamp":"2026-06-26T11:18:05.457331784+05:30","level":"WARN","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"org.apache.kafka.clients.NetworkClient","message":"[Consumer clientId=consumer-notification-dispatch-workers-3, groupId=notification-dispatch-workers] Bootstrap broker kafka-0.kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected","stack_trace":""}
2026-06-26 05:48:06.028 INFO  [org.springframework.kafka.KafkaListenerEndpointContainer#3-0-C-1] o.a.k.c.NetworkClient: [Consumer clientId=consumer-notification-service-group-2, groupId=notification-service-group] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 10108 ms.
{"@timestamp":"2026-06-26T11:18:06.028855545+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"org.apache.kafka.clients.NetworkClient","message":"[Consumer clientId=consumer-notification-service-group-2, groupId=notification-service-group] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 10108 ms.","stack_trace":""}
2026-06-26 05:48:06.029 WARN  [org.springframework.kafka.KafkaListenerEndpointContainer#3-0-C-1] o.a.k.c.NetworkClient$DefaultMetadataUpdater: [Consumer clientId=consumer-notification-service-group-2, groupId=notification-service-group] Bootstrap broker kafka-0.kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
{"@timestamp":"2026-06-26T11:18:06.029426317+05:30","level":"WARN","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"org.apache.kafka.clients.NetworkClient","message":"[Consumer clientId=consumer-notification-service-group-2, groupId=notification-service-group] Bootstrap broker kafka-0.kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected","stack_trace":""}
2026-06-26 05:48:07.031 INFO  [org.springframework.kafka.KafkaListenerEndpointContainer#2-0-C-1] o.a.k.c.NetworkClient: [Consumer clientId=consumer-debug-group-1-1, groupId=debug-group-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 11130 ms.
{"@timestamp":"2026-06-26T11:18:07.031116951+05:30","level":"INFO","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"org.apache.kafka.clients.NetworkClient","message":"[Consumer clientId=consumer-debug-group-1-1, groupId=debug-group-1] Disconnecting from node -1 due to socket connection setup timeout. The timeout value is 11130 ms.","stack_trace":""}
2026-06-26 05:48:07.031 WARN  [org.springframework.kafka.KafkaListenerEndpointContainer#2-0-C-1] o.a.k.c.NetworkClient$DefaultMetadataUpdater: [Consumer clientId=consumer-debug-group-1-1, groupId=debug-group-1] Bootstrap broker kafka-0.kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected
{"@timestamp":"2026-06-26T11:18:07.031840952+05:30","level":"WARN","service":"NotificationService","traceId":"","userId":"","clientIp":"","apiPath":"","requestUrl":"","httpMethod":"","httpStatus":"","class":"org.apache.kafka.clients.NetworkClient","message":"[Consumer clientId=consumer-debug-group-1-1, groupId=debug-group-1] Bootstrap broker kafka-0.kafka.uat-cbops1.svc.cluster.local:9092 (id: -1 rack: null) disconnected","stack_trace":""
