{"@timestamp":"2026-09-18T15:22:31.425507919+05:30","level":"WARN","service":"CommonMasterService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"com.zaxxer.hikari.pool.PoolBase","message":"HikariPool-1 - Pool is empty, failed to create/setup connection (e2b6433c-22d7-4ac6-9fb9-417f0ac5aaeb)","stack_trace":"java.sql.SQLTimeoutException: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=3x06FQ76RP6PFvYWu3W8fQ==)\nhttps://docs.oracle.com/error-help/db/ora-12170/\n\tat oracle.jdbc.driver.T4CConnection.handleLogonNetException(T4CConnection.java:2068)\n\tat oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:1305)\n\tat oracle.jdbc.driver.PhysicalConnection.connect(PhysicalConnection.java:1236)\n\tat oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:107)\n\tat oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:817)\n\tat oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:720)\n\tat com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:144)\n\tat com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:373)\n\tat com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:210)\n\tat com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:488)\nCaused by: oracle.net.ns.NetException: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=3x06FQ76RP6PFvYWu3W8fQ==)\nhttps://docs.oracle.com/error-help/db/ora-12170/\n\tat oracle.net.nt.TcpNTAdapter.handleEstablishSocketException(TcpNTAdapter.java:396)\n\tat oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:361)\n\tat oracle.net.nt.TcpNTAdapter.connect(TcpNTAdapter.java:239)\n\tat oracle.net.nt.ConnOption.connect(ConnOption.java:361)\n\tat oracle.net.nt.ConnStrategy.executeConnOption(ConnStrategy.java:1305)\n\tat oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:794)\n\tat oracle.net.resolver.AddrResolution.resolveAndExecute(AddrResolution.java:729)\n\tat oracle.net.ns.NSProtocol.establishConnection(NSProtocol.java:985)\n\tat oracle.net.ns.NSProtocol.connect(NSProtocol.java:344)\n\tat oracle.jdbc.driver.T4CConnection.connectNetworkSessionProtocol(T4CConnection.java:3978)\n"}
2026-09-18 09:53:35.333 WARN  [HikariPool-1:connection-adder] c.z.h.p.PoolBase: HikariPool-1 - Pool is empty, failed to create/setup connection (4727d2e3-8198-4b06-b0e4-971d761d8ff7)
java.sql.SQLTimeoutException: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=/vpCFGHnR6qhug0/7sEv9A==)
https://docs.oracle.com/error-help/db/ora-12170/
        at oracle.jdbc.driver.T4CConnection.handleLogonNetException(T4CConnection.java:2068)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:1305)
        at oracle.jdbc.driver.PhysicalConnection.connect(PhysicalConnection.java:1236)
        at oracle.jdbc.driver.T4CDriverExtension.getConnection(T4CDriverExtension.java:107)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:817)
        at oracle.jdbc.driver.OracleDriver.connect(OracleDriver.java:720)
        at com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:144)
        at com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:373)
        at com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:210)
        at com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:488)
        at com.zaxxer.hikari.pool.HikariPool$PoolEntryCreator.call(HikariPool.java:752)
        at com.zaxxer.hikari.pool.HikariPool$PoolEntryCreator.call(HikariPool.java:731)
        at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:317)
        at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1144)
        at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:642)
        at java.base/java.lang.Thread.run(Thread.java:1570)
Caused by: oracle.net.ns.NetException: ORA-12170: Cannot connect. TCP connect timeout of 30000ms for host 10.177.103.192 port 1523. (CONNECTION_ID=/vpCFGHnR6qhug0/7sEv9A==)
https://docs.oracle.com/error-help/db/ora-12170/
        at oracle.net.nt.TcpNTAdapter.handleEstablishSocketException(TcpNTAdapter.java:396)
        at oracle.net.nt.TcpNTAdapter.establishSocket(TcpNTAdapter.java:361)
        at oracle.net.nt.TcpNTAdapter.connect(TcpNTAdapter.java:239)
        at oracle.net.nt.ConnOption.connect(ConnOption.java:361)
        at oracle.net.nt.ConnStrategy.executeConnOption(ConnStrategy.java:1305)
        at oracle.net.nt.ConnStrategy.execute(ConnStrategy.java:794)
        at oracle.net.resolver.AddrResolution.resolveAndExecute(AddrResolution.java:729)
        at oracle.net.ns.NSProtocol.establishConnection(NSProtocol.java:985)
        at oracle.net.ns.NSProtocol.connect(NSProtocol.java:344)
        at oracle.jdbc.driver.T4CConnection.connectNetworkSessionProtocol(T4CConnection.java:3978)
        at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:1187)
        ... 14 common frames omitted


        
