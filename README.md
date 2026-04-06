D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl get pods -n logging --kubeconfig h06vksuatcbopscls.conf
NAME                    READY   STATUS              RESTARTS      AGE
loki-7974ccfdd5-2n2m9   1/1     Running             0             4m46s
loki-7974ccfdd5-2nt9m   0/1     CrashLoopBackOff    4 (27s ago)   2m25s
loki-7974ccfdd5-pff7r   0/1     ContainerCreating   0             2m25s

D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl logs loki-7974ccfdd5-2nt9m -n logging --kubeconfig h06vksuatcbopscls.conf
level=warn ts=2026-04-06T06:35:03.724062533Z caller=store.go:56 msg="running with DEPRECATED flag -store.max-look-back-period, use -querier.max-query-lookback instead."
level=warn ts=2026-04-06T06:35:03.724119681Z caller=loki.go:288 msg="global timeout not configured, using default engine timeout (\"5m0s\"). This behavior will change in the next major to always use the default global timeout (\"5m\")."
level=info ts=2026-04-06T06:35:03.725114628Z caller=main.go:108 msg="Starting Loki" version="(version=2.9.4, branch=HEAD, revision=f599ebc535)"
level=info ts=2026-04-06T06:35:03.725887115Z caller=server.go:322 http=[::]:3100 grpc=[::]:9095 msg="server listening on addresses"
level=info ts=2026-04-06T06:35:03.726206708Z caller=modules.go:932 msg="Ruler storage is not configured; ruler will not be started."
level=warn ts=2026-04-06T06:35:03.726950718Z caller=cache.go:127 msg="fifocache config is deprecated. use embedded-cache instead"
level=warn ts=2026-04-06T06:35:03.72696571Z caller=experimental.go:20 msg="experimental feature in use" feature="In-memory (FIFO) cache - chunksembedded-cache"
level=info ts=2026-04-06T06:35:03.727251229Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20519"
ts=2026-04-06T06:35:03.727314842Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727322412Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=3.879µs
level=info ts=2026-04-06T06:35:03.727300933Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
ts=2026-04-06T06:35:03.727329611Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727336003Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.398µs
ts=2026-04-06T06:35:03.727359843Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727363669Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.36µs
level=info ts=2026-04-06T06:35:03.727371741Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20520"
ts=2026-04-06T06:35:03.727401747Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727405403Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.202µs
ts=2026-04-06T06:35:03.727424693Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727428354Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.401µs
level=info ts=2026-04-06T06:35:03.727435959Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20521"
ts=2026-04-06T06:35:03.727464111Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727467376Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.368µs
ts=2026-04-06T06:35:03.72748316Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727486652Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.219µs
level=info ts=2026-04-06T06:35:03.727494624Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20522"
ts=2026-04-06T06:35:03.727524015Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727527209Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.154µs
ts=2026-04-06T06:35:03.72754437Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727547815Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.269µs
level=info ts=2026-04-06T06:35:03.727554742Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20523"
ts=2026-04-06T06:35:03.727582407Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.72758581Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.34µs
ts=2026-04-06T06:35:03.727605262Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727608677Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.387µs
level=info ts=2026-04-06T06:35:03.727616572Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20524"
ts=2026-04-06T06:35:03.727643787Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727647014Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.288µs
ts=2026-04-06T06:35:03.727664384Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727667631Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.159µs
level=info ts=2026-04-06T06:35:03.727674343Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20525"
ts=2026-04-06T06:35:03.727699951Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727703156Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.323µs
ts=2026-04-06T06:35:03.727718454Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727722267Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.247µs
level=info ts=2026-04-06T06:35:03.727728755Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20526"
ts=2026-04-06T06:35:03.727755738Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727758736Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.141µs
ts=2026-04-06T06:35:03.727774109Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727777471Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.118µs
level=info ts=2026-04-06T06:35:03.727783767Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20527"
ts=2026-04-06T06:35:03.727810887Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727816365Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.334µs
ts=2026-04-06T06:35:03.727832116Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.72783542Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.373µs
level=info ts=2026-04-06T06:35:03.727843197Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20528"
ts=2026-04-06T06:35:03.727868449Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.72787222Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.182µs
ts=2026-04-06T06:35:03.727889319Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727892486Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.298µs
level=info ts=2026-04-06T06:35:03.727899489Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20529"
ts=2026-04-06T06:35:03.727927412Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727930765Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.319µs
ts=2026-04-06T06:35:03.727948264Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727951248Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.157µs
level=info ts=2026-04-06T06:35:03.727957741Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20530"
ts=2026-04-06T06:35:03.727983961Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.727986961Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.142µs
ts=2026-04-06T06:35:03.728004804Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.72800837Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.238µs
level=info ts=2026-04-06T06:35:03.72801579Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20531"
ts=2026-04-06T06:35:03.728041197Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728044326Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.157µs
ts=2026-04-06T06:35:03.728062273Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728065485Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.302µs
level=info ts=2026-04-06T06:35:03.728072274Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20532"
ts=2026-04-06T06:35:03.728098819Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728106383Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=5.673µs
ts=2026-04-06T06:35:03.728146886Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728155818Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=3.872µs
level=info ts=2026-04-06T06:35:03.728166943Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20533"
ts=2026-04-06T06:35:03.728200103Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728203531Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.273µs
ts=2026-04-06T06:35:03.728221783Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728224903Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.235µs
level=info ts=2026-04-06T06:35:03.728233128Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20534"
ts=2026-04-06T06:35:03.728261412Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.72826446Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.201µs
ts=2026-04-06T06:35:03.72827995Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728284648Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.155µs
level=info ts=2026-04-06T06:35:03.72829301Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20535"
ts=2026-04-06T06:35:03.72831919Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728323879Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.262µs
ts=2026-04-06T06:35:03.728340524Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728344834Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.228µs
level=info ts=2026-04-06T06:35:03.728351329Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20536"
ts=2026-04-06T06:35:03.728378054Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728381599Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.668µs
ts=2026-04-06T06:35:03.728401197Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728404362Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.226µs
level=info ts=2026-04-06T06:35:03.728412691Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20537"
ts=2026-04-06T06:35:03.728440018Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728452436Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.195µs
ts=2026-04-06T06:35:03.728472515Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728475794Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.362µs
level=info ts=2026-04-06T06:35:03.72848398Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20538"
ts=2026-04-06T06:35:03.728509327Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728512487Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.334µs
ts=2026-04-06T06:35:03.728533197Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728537961Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=2.068µs
level=info ts=2026-04-06T06:35:03.728547351Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20539"
ts=2026-04-06T06:35:03.72858315Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728586481Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.265µs
ts=2026-04-06T06:35:03.728603305Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728606398Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.189µs
level=info ts=2026-04-06T06:35:03.728613999Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20540"
ts=2026-04-06T06:35:03.728642873Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728646068Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.36µs
ts=2026-04-06T06:35:03.728661196Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728664163Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.142µs
level=info ts=2026-04-06T06:35:03.728670669Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20541"
ts=2026-04-06T06:35:03.728696773Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728699764Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.124µs
ts=2026-04-06T06:35:03.728721257Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.72872607Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.435µs
level=info ts=2026-04-06T06:35:03.728736058Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20542"
ts=2026-04-06T06:35:03.728763958Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728767067Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.26µs
ts=2026-04-06T06:35:03.728786554Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728789675Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.219µs
level=info ts=2026-04-06T06:35:03.72879573Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20543"
ts=2026-04-06T06:35:03.728818047Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.72882116Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.107µs
ts=2026-04-06T06:35:03.728835788Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728840156Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.108µs
level=info ts=2026-04-06T06:35:03.72884705Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20544"
ts=2026-04-06T06:35:03.728872059Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728876414Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.116µs
ts=2026-04-06T06:35:03.728895253Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728898451Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.22µs
level=info ts=2026-04-06T06:35:03.72890806Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20545"
ts=2026-04-06T06:35:03.7289336Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728936723Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.11µs
ts=2026-04-06T06:35:03.72895191Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728954919Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.081µs
level=info ts=2026-04-06T06:35:03.728961946Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20546"
ts=2026-04-06T06:35:03.728988144Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.728992773Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.383µs
ts=2026-04-06T06:35:03.729009286Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.729012655Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.24µs
level=info ts=2026-04-06T06:35:03.729019265Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20547"
ts=2026-04-06T06:35:03.729043575Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.72904675Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.127µs
ts=2026-04-06T06:35:03.729066589Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.729069805Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.201µs
level=info ts=2026-04-06T06:35:03.729076165Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20548"
ts=2026-04-06T06:35:03.729100326Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.729103369Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.174µs
ts=2026-04-06T06:35:03.729117874Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.729120829Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.135µs
level=info ts=2026-04-06T06:35:03.729130121Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20549"
ts=2026-04-06T06:35:03.729152772Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.729155801Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.147µs
ts=2026-04-06T06:35:03.729181479Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-06T06:35:03.729184933Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=1.22µs
level=info ts=2026-04-06T06:35:03.729194248Z caller=table_manager.go:271 index-store=boltdb-shipper-2024-01-01 msg="query readiness setup completed" duration=1.156µs distinct_users_len=0 distinct_users=
level=info ts=2026-04-06T06:35:03.729223817Z caller=shipper.go:165 index-store=boltdb-shipper-2024-01-01 msg="starting index shipper in RW mode"
level=info ts=2026-04-06T06:35:03.729334097Z caller=table_manager.go:240 index-store=boltdb-shipper-2024-01-01 msg="loading table index_20549"
level=error ts=2026-04-06T06:35:08.710223702Z caller=table.go:375 msg="failed to open file /var/loki/index/index_20549/1775457175. Please fix or remove this file." err=timeout
level=error ts=2026-04-06T06:35:08.710293636Z caller=table_manager.go:250 index-store=boltdb-shipper-2024-01-01 msg="failed to remove empty table folder" table=index_20549 err="remove /var/loki/index/index_20549: directory not empty"
level=info ts=2026-04-06T06:35:08.710340876Z caller=shipper_index_client.go:76 index-store=boltdb-shipper-2024-01-01 msg="starting boltdb shipper in RW mode"
level=info ts=2026-04-06T06:35:08.710413072Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=warn ts=2026-04-06T06:35:08.710850341Z caller=modules.go:951 msg="RulerStorage is nil. Not starting the ruler."
failed to init delete store: timeout
error initialising module: compactor
github.com/grafana/dskit/modules.(*Manager).initModule
        /src/loki/vendor/github.com/grafana/dskit/modules/modules.go:138
github.com/grafana/dskit/modules.(*Manager).InitModuleServices
        /src/loki/vendor/github.com/grafana/dskit/modules/modules.go:108
github.com/grafana/loki/pkg/loki.(*Loki).Run
        /src/loki/pkg/loki/loki.go:461
main.main
        /src/loki/cmd/loki/main.go:110
runtime.main
        /usr/local/go/src/runtime/proc.go:267
runtime.goexit
        /usr/local/go/src/runtime/asm_amd64.s:1650
level=error ts=2026-04-06T06:35:13.692587128Z caller=log.go:230 msg="error running loki" err="failed to init delete store: timeout\nerror initialising module: compactor\ngithub.com/grafana/dskit/modules.(*Manager).initModule\n\t/src/loki/vendor/github.com/grafana/dskit/modules/modules.go:138\ngithub.com/grafana/dskit/modules.(*Manager).InitModuleServices\n\t/src/loki/vendor/github.com/grafana/dskit/modules/modules.go:108\ngithub.com/grafana/loki/pkg/loki.(*Loki).Run\n\t/src/loki/pkg/loki/loki.go:461\nmain.main\n\t/src/loki/cmd/loki/main.go:110\nruntime.main\n\t/usr/local/go/src/runtime/proc.go:267\nruntime.goexit\n\t/usr/local/go/src/runtime/asm_amd64.s:1650"
