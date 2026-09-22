2026-09-22 05:44:06.277 WARN  [batch-report-gen-5] o.a.h.h.DFSOutputStream: Error while syncing
org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /reports/2026-03-30/nwsa_report/08027/nwsa_report_30032026_08027.xlsx could only be written to 0 of the 1 minReplication nodes. There are 2 datanode(s) running and 2 node(s) are excluded in this operation.
        at org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:2473)
        at org.apache.hadoop.hdfs.server.namenode.FSDirWriteFileOp.chooseTargetForNewBlock(FSDirWriteFileOp.java:293)
        at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3075)
        at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:932)
        at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:603)
        at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
        at org.apache.hadoop.ipc.ProtobufRpcEngine2$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine2.java:621)
        at org.apache.hadoop.ipc.ProtobufRpcEngine2$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine2.java:589)
        at org.apache.hadoop.ipc.ProtobufRpcEngine2$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine2.java:573)
        at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1228)
        at org.apache.hadoop.ipc.Server$RpcCall.run(Server.java:1246)
        at org.apache.hadoop.ipc.Server$RpcCall.run(Server.java:1169)
        at java.base/java.security.AccessController.doPrivileged(AccessController.java:712)
        at java.base/javax.security.auth.Subject.doAs(Subject.java:439)
        at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1953)
        at org.apache.hadoop.ipc.Server$Handler.run(Server.java:3198)

        at org.apache.hadoop.ipc.Client.warpIOException(Client.java:1614)
        at org.apache.hadoop.ipc.Client.getRpcResponse(Client.java:1605)
        at org.apache.hadoop.ipc.Client.call(Client.java:1558)
        at org.apache.hadoop.ipc.Client.call(Client.java:1474)
        at org.apache.hadoop.ipc.ProtobufRpcEngine2$Invoker.invoke(ProtobufRpcEngine2.java:259)
        at org.apache.hadoop.ipc.ProtobufRpcEngine2$Invoker.invoke(ProtobufRpcEngine2.java:140)
        at jdk.proxy2/jdk.proxy2.$Proxy112.addBlock(Unknown Source)
        at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.lambda$addBlock$11(ClientNamenodeProtocolTranslatorPB.java:500)
        at org.apache.hadoop.ipc.internal.ShadedProtobufHelper.ipc(ShadedProtobufHelper.java:160)
        at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:500)
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
        at java.base/java.lang.reflect.Method.invoke(Method.java:580)
        at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:437)
        at org.apache.hadoop.io.retry.RetryInvocationHandler$Call.invokeMethod(RetryInvocationHandler.java:170)
        at org.apache.hadoop.io.retry.RetryInvocationHandler$Call.invoke(RetryInvocationHandler.java:162)
        at org.apache.hadoop.io.retry.RetryInvocationHandler$Call.invokeOnce(RetryInvocationHandler.java:100)
        at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:366)
        at jdk.proxy2/jdk.proxy2.$Proxy113.addBlock(Unknown Source)
        at org.apache.hadoop.hdfs.DFSOutputStream.addBlock(DFSOutputStream.java:1148)
        at org.apache.hadoop.hdfs.DataStreamer.locateFollowingBlock(DataStreamer.java:2035)
        at org.apache.hadoop.hdfs.DataStreamer.setupPipelineForCreate(DataStreamer.java:1830)
        at org.apache.hadoop.hdfs.DataStreamer.work(DataStreamer.java:752)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:70)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:66)
        at java.base/javax.security.auth.Subject.lambda$callAs$0(Subject.java:379)
        at java.base/java.security.AccessController.doPrivileged(AccessController.java:714)
        at java.base/javax.security.auth.Subject.doAs(Subject.java:525)
        at java.base/javax.security.auth.Subject.callAs(Subject.java:381)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.callAs(SubjectUtil.java:242)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.doAs(SubjectUtil.java:275)
        at org.apache.hadoop.util.Daemon.run(Daemon.java:66)
{"@timestamp":"2026-09-22T11:14:06.277276055+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DFSClient","message":"Error while syncing","stack_trace":"org.apache.hadoop.ipc.RemoteException(java.io.IOException): File /reports/2026-03-30/nwsa_report/08027/nwsa_report_30032026_08027.xlsx could only be written to 0 of the 1 minReplication nodes. There are 2 datanode(s) running and 2 node(s) are excluded in this operation.\n\tat org.apache.hadoop.hdfs.server.blockmanagement.BlockManager.chooseTarget4NewBlock(BlockManager.java:2473)\n\tat org.apache.hadoop.hdfs.server.namenode.FSDirWriteFileOp.chooseTargetForNewBlock(FSDirWriteFileOp.java:293)\n\tat org.apache.hadoop.hdfs.server.namenode.FSNamesystem.getAdditionalBlock(FSNamesystem.java:3075)\n\tat org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.addBlock(NameNodeRpcServer.java:932)\n\tat org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.addBlock(ClientNamenodeProtocolServerSideTranslatorPB.java:603)\n\tat org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)\n\tat org.apache.hadoop.ipc.ProtobufRpcEngine2$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine2.java:621)\n\tat org.apache.hadoop.ipc.ProtobufRpcEngine2$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine2.java:589)\n\tat org.apache.hadoop.ipc.ProtobufRpcEngine2$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine2.java:573)\n\tat org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1228)\n\tat org.apache.hadoop.ipc.Server$RpcCall.run(Server.java:1246)\n\tat org.apache.hadoop.ipc.Server$RpcCall.run(Server.java:1169)\n\tat java.base/java.security.AccessController.doPrivileged(AccessController.java:712)\n\tat java.base/javax.security.auth.Subject.doAs(Subject.java:439)\n\tat org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1953)\n\tat org.apache.hadoop.ipc.Server$Handler.run(Server.java:3198)\n\n\tat org.apache.hadoop.ipc.Client.warpIOException(Client.java:1614)\n\tat org.apache.hadoop.ipc.Client.getRpcResponse(Client.java:1605)\n\tat org.apache.hadoop.ipc.Client.call(Client.java:1558)\n\tat org.apache.hadoop.ipc.Client.call(Client.java:1474)\n\tat org.apache.hadoop.ipc.ProtobufRpcEngine2$Invoker.invoke(ProtobufRpcEngine2.java:259)\n\tat org.apache.hadoop.ipc.ProtobufRpcEngine2$Invoker.invoke(ProtobufRpcEngine2.java:140)\n\tat jdk.proxy2/jdk.proxy2.$Proxy112.addBlock(Unknown Source)\n\tat org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.lambda$addBlock$11(ClientNamenodeProtocolTranslatorPB.java:500)\n\tat org.apache.hadoop.ipc.internal.ShadedProtobufHelper.ipc(ShadedProtobufHelper.java:160)\n\tat org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.addBlock(ClientNamenodeProtocolTranslatorPB.java:500)\n"}
2026-09-22 05:44:06.277 ERROR [batch-report-gen-5] c.t.f.R.b.a.s.BatchReportStorageService: Failed to save xlsx report for 08027: IllegalArgumentException
{"@timestamp":"2026-09-22T11:14:06.277438031+05:30","level":"ERROR","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.t.f.R.b.a.s.BatchReportStorageService","message":"Failed to save xlsx report for 08027: IllegalArgumentException","stack_trace":""}
2026-09-22 05:44:11.707 WARN  [Thread-56965] o.a.h.h.DataStreamer: Exception in createBlockOutputStream blk_1076381838_2641107
org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/10.177.103.197:50012]
        at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:616)
        at org.apache.hadoop.hdfs.DataStreamer.createSocketForPipeline(DataStreamer.java:256)
        at org.apache.hadoop.hdfs.DataStreamer.createBlockOutputStream(DataStreamer.java:1894)
        at org.apache.hadoop.hdfs.DataStreamer.setupPipelineForCreate(DataStreamer.java:1842)
        at org.apache.hadoop.hdfs.DataStreamer.work(DataStreamer.java:752)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:70)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:66)
        at java.base/javax.security.auth.Subject.lambda$callAs$0(Subject.java:379)
        at java.base/java.security.AccessController.doPrivileged(AccessController.java:714)
        at java.base/javax.security.auth.Subject.doAs(Subject.java:525)
        at java.base/javax.security.auth.Subject.callAs(Subject.java:381)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.callAs(SubjectUtil.java:242)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.doAs(SubjectUtil.java:275)
        at org.apache.hadoop.util.Daemon.run(Daemon.java:66)
{"@timestamp":"2026-09-22T11:14:11.707266347+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Exception in createBlockOutputStream blk_1076381838_2641107","stack_trace":"org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/10.177.103.197:50012]\n\tat org.apache.hadoop.net.NetUtils.connect(NetUtils.java:616)\n\tat org.apache.hadoop.hdfs.DataStreamer.createSocketForPipeline(DataStreamer.java:256)\n\tat org.apache.hadoop.hdfs.DataStreamer.createBlockOutputStream(DataStreamer.java:1894)\n\tat org.apache.hadoop.hdfs.DataStreamer.setupPipelineForCreate(DataStreamer.java:1842)\n\tat org.apache.hadoop.hdfs.DataStreamer.work(DataStreamer.java:752)\n\tat org.apache.hadoop.util.Daemon$1.run(Daemon.java:70)\n\tat org.apache.hadoop.util.Daemon$1.run(Daemon.java:66)\n\tat java.base/javax.security.auth.Subject.lambda$callAs$0(Subject.java:379)\n\tat java.base/java.security.AccessController.doPrivileged(AccessController.java:714)\n\tat java.base/javax.security.auth.Subject.doAs(Subject.java:525)\n"}
2026-09-22 05:44:11.707 WARN  [Thread-56965] o.a.h.h.DataStreamer: Error Recovery for BP-1063351587-10.177.103.199-1770116578607:blk_1076381838_2641107 in pipeline [DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK], DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]]: datanode 0(DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]) is bad.
{"@timestamp":"2026-09-22T11:14:11.707582615+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Error Recovery for BP-1063351587-10.177.103.199-1770116578607:blk_1076381838_2641107 in pipeline [DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK], DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]]: datanode 0(DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]) is bad.","stack_trace":""}
2026-09-22 05:44:11.707 WARN  [Thread-56965] o.a.h.h.DataStreamer: Abandoning BP-1063351587-10.177.103.199-1770116578607:blk_1076381838_2641107
{"@timestamp":"2026-09-22T11:14:11.707621235+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Abandoning BP-1063351587-10.177.103.199-1770116578607:blk_1076381838_2641107","stack_trace":""}
2026-09-22 05:44:11.712 WARN  [Thread-56965] o.a.h.h.DataStreamer: Excluding datanode DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]
{"@timestamp":"2026-09-22T11:14:11.712169187+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Excluding datanode DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]","stack_trace":""}
2026-09-22 05:44:15.474 WARN  [Thread-56967] o.a.h.h.DataStreamer: Exception in createBlockOutputStream blk_1076381840_2641109
org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/10.177.103.198:50012]
        at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:616)
        at org.apache.hadoop.hdfs.DataStreamer.createSocketForPipeline(DataStreamer.java:256)
        at org.apache.hadoop.hdfs.DataStreamer.createBlockOutputStream(DataStreamer.java:1894)
        at org.apache.hadoop.hdfs.DataStreamer.setupPipelineForCreate(DataStreamer.java:1842)
        at org.apache.hadoop.hdfs.DataStreamer.work(DataStreamer.java:752)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:70)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:66)
        at java.base/javax.security.auth.Subject.lambda$callAs$0(Subject.java:379)
        at java.base/java.security.AccessController.doPrivileged(AccessController.java:714)
        at java.base/javax.security.auth.Subject.doAs(Subject.java:525)
        at java.base/javax.security.auth.Subject.callAs(Subject.java:381)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.callAs(SubjectUtil.java:242)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.doAs(SubjectUtil.java:275)
        at org.apache.hadoop.util.Daemon.run(Daemon.java:66)
{"@timestamp":"2026-09-22T11:14:15.474504884+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Exception in createBlockOutputStream blk_1076381840_2641109","stack_trace":"org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/10.177.103.198:50012]\n\tat org.apache.hadoop.net.NetUtils.connect(NetUtils.java:616)\n\tat org.apache.hadoop.hdfs.DataStreamer.createSocketForPipeline(DataStreamer.java:256)\n\tat org.apache.hadoop.hdfs.DataStreamer.createBlockOutputStream(DataStreamer.java:1894)\n\tat org.apache.hadoop.hdfs.DataStreamer.setupPipelineForCreate(DataStreamer.java:1842)\n\tat org.apache.hadoop.hdfs.DataStreamer.work(DataStreamer.java:752)\n\tat org.apache.hadoop.util.Daemon$1.run(Daemon.java:70)\n\tat org.apache.hadoop.util.Daemon$1.run(Daemon.java:66)\n\tat java.base/javax.security.auth.Subject.lambda$callAs$0(Subject.java:379)\n\tat java.base/java.security.AccessController.doPrivileged(AccessController.java:714)\n\tat java.base/javax.security.auth.Subject.doAs(Subject.java:525)\n"}
2026-09-22 05:44:15.474 WARN  [Thread-56967] o.a.h.h.DataStreamer: Error Recovery for BP-1063351587-10.177.103.199-1770116578607:blk_1076381840_2641109 in pipeline [DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK], DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]]: datanode 0(DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]) is bad.
{"@timestamp":"2026-09-22T11:14:15.474663807+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Error Recovery for BP-1063351587-10.177.103.199-1770116578607:blk_1076381840_2641109 in pipeline [DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK], DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]]: datanode 0(DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]) is bad.","stack_trace":""}
2026-09-22 05:44:15.474 WARN  [Thread-56967] o.a.h.h.DataStreamer: Abandoning BP-1063351587-10.177.103.199-1770116578607:blk_1076381840_2641109
{"@timestamp":"2026-09-22T11:14:15.474689813+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Abandoning BP-1063351587-10.177.103.199-1770116578607:blk_1076381840_2641109","stack_trace":""}
2026-09-22 05:44:15.478 WARN  [Thread-56967] o.a.h.h.DataStreamer: Excluding datanode DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]
{"@timestamp":"2026-09-22T11:14:15.478716542+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Excluding datanode DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]","stack_trace":""}
2026-09-22 05:44:15.493 WARN  [batch-report-gen-1] o.a.h.h.DataStreamer: Slow waitForAckedSeqno took 60057ms (threshold=30000ms). File being written: /reports/2026-03-30/nwsa_report/08013/nwsa_report_30032026_08013.psv, block: BP-1063351587-10.177.103.199-1770116578607:blk_1076381866_2641135, Write pipeline datanodes: [DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]].
{"@timestamp":"2026-09-22T11:14:15.493699459+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Slow waitForAckedSeqno took 60057ms (threshold=30000ms). File being written: /reports/2026-03-30/nwsa_report/08013/nwsa_report_30032026_08013.psv, block: BP-1063351587-10.177.103.199-1770116578607:blk_1076381866_2641135, Write pipeline datanodes: [DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]].","stack_trace":""}
2026-09-22 05:44:16.863 WARN  [Thread-56969] o.a.h.h.DataStreamer: Exception in createBlockOutputStream blk_1076381842_2641111
org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/10.177.103.197:50012]
        at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:616)
        at org.apache.hadoop.hdfs.DataStreamer.createSocketForPipeline(DataStreamer.java:256)
        at org.apache.hadoop.hdfs.DataStreamer.createBlockOutputStream(DataStreamer.java:1894)
        at org.apache.hadoop.hdfs.DataStreamer.setupPipelineForCreate(DataStreamer.java:1842)
        at org.apache.hadoop.hdfs.DataStreamer.work(DataStreamer.java:752)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:70)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:66)
        at java.base/javax.security.auth.Subject.lambda$callAs$0(Subject.java:379)
        at java.base/java.security.AccessController.doPrivileged(AccessController.java:714)
        at java.base/javax.security.auth.Subject.doAs(Subject.java:525)
        at java.base/javax.security.auth.Subject.callAs(Subject.java:381)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.callAs(SubjectUtil.java:242)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.doAs(SubjectUtil.java:275)
        at org.apache.hadoop.util.Daemon.run(Daemon.java:66)
{"@timestamp":"2026-09-22T11:14:16.863968647+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Exception in createBlockOutputStream blk_1076381842_2641111","stack_trace":"org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/10.177.103.197:50012]\n\tat org.apache.hadoop.net.NetUtils.connect(NetUtils.java:616)\n\tat org.apache.hadoop.hdfs.DataStreamer.createSocketForPipeline(DataStreamer.java:256)\n\tat org.apache.hadoop.hdfs.DataStreamer.createBlockOutputStream(DataStreamer.java:1894)\n\tat org.apache.hadoop.hdfs.DataStreamer.setupPipelineForCreate(DataStreamer.java:1842)\n\tat org.apache.hadoop.hdfs.DataStreamer.work(DataStreamer.java:752)\n\tat org.apache.hadoop.util.Daemon$1.run(Daemon.java:70)\n\tat org.apache.hadoop.util.Daemon$1.run(Daemon.java:66)\n\tat java.base/javax.security.auth.Subject.lambda$callAs$0(Subject.java:379)\n\tat java.base/java.security.AccessController.doPrivileged(AccessController.java:714)\n\tat java.base/javax.security.auth.Subject.doAs(Subject.java:525)\n"}
2026-09-22 05:44:16.864 WARN  [Thread-56969] o.a.h.h.DataStreamer: Error Recovery for BP-1063351587-10.177.103.199-1770116578607:blk_1076381842_2641111 in pipeline [DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK], DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]]: datanode 0(DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]) is bad.
{"@timestamp":"2026-09-22T11:14:16.864307198+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Error Recovery for BP-1063351587-10.177.103.199-1770116578607:blk_1076381842_2641111 in pipeline [DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK], DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]]: datanode 0(DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]) is bad.","stack_trace":""}
2026-09-22 05:44:16.864 WARN  [Thread-56969] o.a.h.h.DataStreamer: Abandoning BP-1063351587-10.177.103.199-1770116578607:blk_1076381842_2641111
{"@timestamp":"2026-09-22T11:14:16.864398821+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Abandoning BP-1063351587-10.177.103.199-1770116578607:blk_1076381842_2641111","stack_trace":""}
2026-09-22 05:44:16.869 WARN  [Thread-56969] o.a.h.h.DataStreamer: Excluding datanode DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]
{"@timestamp":"2026-09-22T11:14:16.86916843+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Excluding datanode DatanodeInfoWithStorage[10.177.103.197:50012,DS-39fbcd73-ee12-46ca-9dd8-c92787f237b0,DISK]","stack_trace":""}
2026-09-22 05:44:16.882 WARN  [batch-report-gen-3] o.a.h.h.DataStreamer: Slow waitForAckedSeqno took 60154ms (threshold=30000ms). File being written: /reports/2026-03-30/nwsa_report/08030/nwsa_report_30032026_08030.psv, block: BP-1063351587-10.177.103.199-1770116578607:blk_1076381867_2641136, Write pipeline datanodes: [DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]].
{"@timestamp":"2026-09-22T11:14:16.882048295+05:30","level":"WARN","service":"ReportBuilderService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"org.apache.hadoop.hdfs.DataStreamer","message":"Slow waitForAckedSeqno took 60154ms (threshold=30000ms). File being written: /reports/2026-03-30/nwsa_report/08030/nwsa_report_30032026_08030.psv, block: BP-1063351587-10.177.103.199-1770116578607:blk_1076381867_2641136, Write pipeline datanodes: [DatanodeInfoWithStorage[10.177.103.198:50012,DS-db07fb70-036d-41ec-bed9-dbd9030bc92c,DISK]].","stack_trace":""}
2026-09-22 05:44:26.411 WARN  [Thread-56971] o.a.h.h.DataStreamer: Exception in createBlockOutputStream blk_1076381844_2641113
org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/10.177.103.198:50012]
        at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:616)
        at org.apache.hadoop.hdfs.DataStreamer.createSocketForPipeline(DataStreamer.java:256)
        at org.apache.hadoop.hdfs.DataStreamer.createBlockOutputStream(DataStreamer.java:1894)
        at org.apache.hadoop.hdfs.DataStreamer.setupPipelineForCreate(DataStreamer.java:1842)
        at org.apache.hadoop.hdfs.DataStreamer.work(DataStreamer.java:752)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:70)
        at org.apache.hadoop.util.Daemon$1.run(Daemon.java:66)
        at java.base/javax.security.auth.Subject.lambda$callAs$0(Subject.java:379)
        at java.base/java.security.AccessController.doPrivileged(AccessController.java:714)
        at java.base/javax.security.auth.Subject.doAs(Subject.java:525)
        at java.base/javax.security.auth.Subject.callAs(Subject.java:381)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.callAs(SubjectUtil.java:242)
        at org.apache.hadoop.security.authentication.util.SubjectUtil.doAs(SubjectUtil.java:275)
        at org.apache.hadoop.util.Daemon.run(Daemon.java:66)
