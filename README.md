
2026-06-19 03:51:48 WARN  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Error connecting to node kafka.cbops.svc.cluster.local:9092 (id: 1 rack: null): java.net.UnknownHostException: kafka.cbops.svc.cluster.local: Name or service not known
        at java.base/java.net.Inet6AddressImpl.lookupAllHostAddr(Native Method)
        at java.base/java.net.InetAddress$PlatformNameService.lookupAllHostAddr(InetAddress.java:930)
        at java.base/java.net.InetAddress.getAddressesFromNameService(InetAddress.java:1543)
        at java.base/java.net.InetAddress$NameServiceAddresses.get(InetAddress.java:848)
        at java.base/java.net.InetAddress.getAllByName0(InetAddress.java:1533)
        at java.base/java.net.InetAddress.getAllByName(InetAddress.java:1386)
        at java.base/java.net.InetAddress.getAllByName(InetAddress.java:1307)
        at org.apache.kafka.clients.DefaultHostResolver.resolve(DefaultHostResolver.java:27)
        at org.apache.kafka.clients.ClientUtils.resolve(ClientUtils.java:122)
        at org.apache.kafka.clients.ClusterConnectionStates$NodeConnectionState.currentAddress(ClusterConnectionStates.java:510)
        at org.apache.kafka.clients.ClusterConnectionStates$NodeConnectionState.access$200(ClusterConnectionStates.java:467)
        at org.apache.kafka.clients.ClusterConnectionStates.currentAddress(ClusterConnectionStates.java:173)
        at org.apache.kafka.clients.NetworkClient.initiateConnect(NetworkClient.java:1030)
        at org.apache.kafka.clients.NetworkClient.access$600(NetworkClient.java:73)
        at org.apache.kafka.clients.NetworkClient$DefaultMetadataUpdater.maybeUpdate(NetworkClient.java:1203)
        at org.apache.kafka.clients.NetworkClient$DefaultMetadataUpdater.maybeUpdate(NetworkClient.java:1091)
        at org.apache.kafka.clients.NetworkClient.poll(NetworkClient.java:569)
        at org.apache.kafka.clients.producer.internals.Sender.runOnce(Sender.java:343)
        at org.apache.kafka.clients.producer.internals.Sender.run(Sender.java:246)
        at java.base/java.lang.Thread.run(Thread.java:829)

2026-06-19 03:51:49 WARN  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Error connecting to node kafka.cbops.svc.cluster.local:9092 (id: 1 rack: null): java.net.UnknownHostException: kafka.cbops.svc.cluster.local: Name or service not known
        at java.base/java.net.Inet6AddressImpl.lookupAllHostAddr(Native Method)
        at java.base/java.net.InetAddress$PlatformNameService.lookupAllHostAddr(InetAddress.java:930)
        at java.base/java.net.InetAddress.getAddressesFromNameService(InetAddress.java:1543)
        at java.base/java.net.InetAddress$NameServiceAddresses.get(InetAddress.java:848)
        at java.base/java.net.InetAddress.getAllByName0(InetAddress.java:1533)
        at java.base/java.net.InetAddress.getAllByName(InetAddress.java:1386)
        at java.base/java.net.InetAddress.getAllByName(InetAddress.java:1307)
        at org.apache.kafka.clients.DefaultHostResolver.resolve(DefaultHostResolver.java:27)
        at org.apache.kafka.clients.ClientUtils.resolve(ClientUtils.java:122)
        at org.apache.kafka.clients.ClusterConnectionStates$NodeConnectionState.currentAddress(ClusterConnectionStates.java:510)
        at org.apache.kafka.clients.ClusterConnectionStates$NodeConnectionState.access$200(ClusterConnectionStates.java:467)
        at org.apache.kafka.clients.ClusterConnectionStates.currentAddress(ClusterConnectionStates.java:173)
        at org.apache.kafka.clients.NetworkClient.initiateConnect(NetworkClient.java:1030)
        at org.apache.kafka.clients.NetworkClient.access$600(NetworkClient.java:73)
        at org.apache.kafka.clients.NetworkClient$DefaultMetadataUpdater.maybeUpdate(NetworkClient.java:1203)
        at org.apache.kafka.clients.NetworkClient$DefaultMetadataUpdater.maybeUpdate(NetworkClient.java:1091)
        at org.apache.kafka.clients.NetworkClient.poll(NetworkClient.java:569)
        at org.apache.kafka.clients.producer.internals.Sender.runOnce(Sender.java:343)
        at org.apache.kafka.clients.producer.internals.Sender.run(Sender.java:246)
        at java.base/java.lang.Thread.run(Thread.java:829)

2026-06-19 03:51:50 WARN  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Error connecting to node kafka.cbops.svc.cluster.local:9092 (id: 1 rack: null): java.net.UnknownHostException: kafka.cbops.svc.cluster.local: Name or service not known
        at java.base/java.net.Inet6AddressImpl.lookupAllHostAddr(Native Method)
        at java.base/java.net.InetAddress$PlatformNameService.lookupAllHostAddr(InetAddress.java:930)
        at java.base/java.net.InetAddress.getAddressesFromNameService(InetAddress.java:1543)
        at java.base/java.net.InetAddress$NameServiceAddresses.get(InetAddress.java:848)
        at java.base/java.net.InetAddress.getAllByName0(InetAddress.java:1533)
        at java.base/java.net.InetAddress.getAllByName(InetAddress.java:1386)
        at java.base/java.net.InetAddress.getAllByName(InetAddress.java:1307)
        at org.apache.kafka.clients.DefaultHostResolver.resolve(DefaultHostResolver.java:27)
        at org.apache.kafka.clients.ClientUtils.resolve(ClientUtils.java:122)
        at org.apache.kafka.clients.ClusterConnectionStates$NodeConnectionState.currentAddress(ClusterConnectionStates.java:510)
        at org.apache.kafka.clients.ClusterConnectionStates$NodeConnectionState.access$200(ClusterConnectionStates.java:467)
        at org.apache.kafka.clients.ClusterConnectionStates.currentAddress(ClusterConnectionStates.java:173)
        at org.apache.kafka.clients.NetworkClient.initiateConnect(NetworkClient.java:1030)
        at org.apache.kafka.clients.NetworkClient.access$600(NetworkClient.java:73)
        at org.apache.kafka.clients.NetworkClient$DefaultMetadataUpdater.maybeUpdate(NetworkClient.java:1203)
        at org.apache.kafka.clients.NetworkClient$DefaultMetadataUpdater.maybeUpdate(NetworkClient.java:1091)
        at org.apache.kafka.clients.NetworkClient.poll(NetworkClient.java:569)
        at org.apache.kafka.clients.producer.internals.Sender.runOnce(Sender.java:343)
        at org.apache.kafka.clients.producer.internals.Sender.run(Sender.java:246)
        at java.base/java.lang.Thread.run(Thread.java:829)

2026-06-19 03:51:51 INFO  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Node 1 disconnected.
2026-06-19 03:51:51 WARN  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Connection to node 1 (kafka.cbops.svc.cluster.local/192.168.7.12:9092) could not be established. Broker may not be available.
2026-06-19 03:51:53 INFO  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Node 1 disconnected.
2026-06-19 03:51:53 WARN  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Connection to node 1 (kafka.cbops.svc.cluster.local/192.168.7.12:9092) could not be established. Broker may not be available.
2026-06-19 03:51:54 INFO  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Node 1 disconnected.
2026-06-19 03:51:54 WARN  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Connection to node 1 (kafka.cbops.svc.cluster.local/192.168.7.12:9092) could not be established. Broker may not be available.
2026-06-19 03:51:55 INFO  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Node 1 disconnected.
2026-06-19 03:51:55 WARN  [org.apache.kafka.clients.NetworkClient] (kafka-producer-network-thread | producer-1) [Producer clientId=producer-1] Connection to node 1 (kafka.cbops.svc.cluster.local/192.168.7.12:9092) could not be established. Broker may not be available.



i am having debezium server pod running these logs are present can you suggest me





