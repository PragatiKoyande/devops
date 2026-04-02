NAME                    READY   STATUS             RESTARTS      AGE
loki-6dd797b766-jhxtj   0/1     CrashLoopBackOff   9 (74s ago)   42m

D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl logs loki-6dd797b766-jhxtj -n logging --kubeconfig h06vksuatcbopscls.conf
level=warn ts=2026-04-02T10:48:25.767175581Z caller=store.go:56 msg="running with DEPRECATED flag -store.max-look-back-period, use -querier.max-query-lookback instead."
level=warn ts=2026-04-02T10:48:25.767220045Z caller=loki.go:288 msg="global timeout not configured, using default engine timeout (\"5m0s\"). This behavior will change in the next major to always use the default global timeout (\"5m\")."
level=info ts=2026-04-02T10:48:25.768302333Z caller=main.go:108 msg="Starting Loki" version="(version=2.9.4, branch=HEAD, revision=f599ebc535)"
level=info ts=2026-04-02T10:48:25.76867967Z caller=modules.go:932 msg="Ruler storage is not configured; ruler will not be started."
level=info ts=2026-04-02T10:48:25.769103659Z caller=server.go:322 http=[::]:3100 grpc=[::]:9095 msg="server listening on addresses"
level=warn ts=2026-04-02T10:48:25.770296808Z caller=cache.go:127 msg="fifocache config is deprecated. use embedded-cache instead"
level=warn ts=2026-04-02T10:48:25.770311421Z caller=experimental.go:20 msg="experimental feature in use" feature="In-memory (FIFO) cache - chunksembedded-cache"
level=info ts=2026-04-02T10:48:25.770525621Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20515"
level=info ts=2026-04-02T10:48:25.770564753Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
ts=2026-04-02T10:48:25.770600535Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.770668695Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=63.42µs
ts=2026-04-02T10:48:25.770675387Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.770721496Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=42.97µs
ts=2026-04-02T10:48:25.770744126Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.770783511Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.137µs
level=info ts=2026-04-02T10:48:25.770793856Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20516"
ts=2026-04-02T10:48:25.770820659Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.770859398Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.632µs
ts=2026-04-02T10:48:25.77087709Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.770932375Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=51.85µs
level=info ts=2026-04-02T10:48:25.770944177Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20517"
ts=2026-04-02T10:48:25.770983565Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771034274Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=47.688µs
ts=2026-04-02T10:48:25.771055092Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771096229Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=38.828µs
level=info ts=2026-04-02T10:48:25.771103892Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20518"
ts=2026-04-02T10:48:25.771129841Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771169284Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.429µs
ts=2026-04-02T10:48:25.771186735Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771226847Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.883µs
level=info ts=2026-04-02T10:48:25.771234088Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20519"
ts=2026-04-02T10:48:25.771264838Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771320233Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=52.264µs
ts=2026-04-02T10:48:25.771342503Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771383245Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=38.331µs
level=info ts=2026-04-02T10:48:25.771391365Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20520"
ts=2026-04-02T10:48:25.77141682Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771457253Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.834µs
ts=2026-04-02T10:48:25.771474299Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.77151355Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.315µs
level=info ts=2026-04-02T10:48:25.771520628Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20521"
ts=2026-04-02T10:48:25.771546858Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771585877Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.829µs
ts=2026-04-02T10:48:25.771603013Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771642204Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.123µs
level=info ts=2026-04-02T10:48:25.771648618Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20522"
ts=2026-04-02T10:48:25.771674777Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771712924Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.93µs
ts=2026-04-02T10:48:25.771729042Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771767348Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.371µs
level=info ts=2026-04-02T10:48:25.771775083Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20523"
ts=2026-04-02T10:48:25.771798619Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771836487Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.962µs
ts=2026-04-02T10:48:25.771852413Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771890453Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.134µs
level=info ts=2026-04-02T10:48:25.771897886Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20524"
ts=2026-04-02T10:48:25.771921101Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.771959161Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.038µs
ts=2026-04-02T10:48:25.771976171Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772015245Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.155µs
level=info ts=2026-04-02T10:48:25.772024108Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20525"
ts=2026-04-02T10:48:25.772055914Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772096426Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=38.001µs
ts=2026-04-02T10:48:25.772113983Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772154299Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=38.31µs
level=info ts=2026-04-02T10:48:25.77216138Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20526"
ts=2026-04-02T10:48:25.772186547Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772224266Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.79µs
ts=2026-04-02T10:48:25.772242366Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772281729Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.381µs
level=info ts=2026-04-02T10:48:25.772289216Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20527"
ts=2026-04-02T10:48:25.77231429Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772351969Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.719µs
ts=2026-04-02T10:48:25.772367825Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772405127Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.27µs
level=info ts=2026-04-02T10:48:25.772412376Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20528"
ts=2026-04-02T10:48:25.772436288Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772474303Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.12µs
ts=2026-04-02T10:48:25.772490391Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772529007Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.197µs
level=info ts=2026-04-02T10:48:25.772535598Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20529"
ts=2026-04-02T10:48:25.772559046Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.77259697Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.961µs
ts=2026-04-02T10:48:25.772612688Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772651167Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.605µs
level=info ts=2026-04-02T10:48:25.772657688Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20530"
ts=2026-04-02T10:48:25.77268104Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772719008Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.066µs
ts=2026-04-02T10:48:25.772734762Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772772347Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.672µs
level=info ts=2026-04-02T10:48:25.772783249Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20531"
ts=2026-04-02T10:48:25.772806649Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.772844881Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.602µs
ts=2026-04-02T10:48:25.772861555Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.77290016Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.681µs
level=info ts=2026-04-02T10:48:25.772906933Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20532"
ts=2026-04-02T10:48:25.77295118Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773001488Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=47.56µs
ts=2026-04-02T10:48:25.773019709Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773059602Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.602µs
level=info ts=2026-04-02T10:48:25.773068318Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20533"
ts=2026-04-02T10:48:25.773091324Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773140858Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=45.507µs
ts=2026-04-02T10:48:25.773179015Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.7732199Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=38.186µs
level=info ts=2026-04-02T10:48:25.77322985Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20534"
ts=2026-04-02T10:48:25.773253423Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773292481Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.005µs
ts=2026-04-02T10:48:25.773307856Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773347286Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.519µs
level=info ts=2026-04-02T10:48:25.773355223Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20535"
ts=2026-04-02T10:48:25.773381582Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.7734212Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.686µs
ts=2026-04-02T10:48:25.773439109Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773481734Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=39.435µs
level=info ts=2026-04-02T10:48:25.773489013Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20536"
ts=2026-04-02T10:48:25.773511954Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773549659Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.767µs
ts=2026-04-02T10:48:25.773567225Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773604917Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.577µs
level=info ts=2026-04-02T10:48:25.773613136Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20537"
ts=2026-04-02T10:48:25.773637613Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773679012Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=39.319µs
ts=2026-04-02T10:48:25.773698615Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773737601Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.777µs
level=info ts=2026-04-02T10:48:25.773743959Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20538"
ts=2026-04-02T10:48:25.773770051Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773809859Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.84µs
ts=2026-04-02T10:48:25.773827464Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773875674Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=46.263µs
level=info ts=2026-04-02T10:48:25.773885582Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20539"
ts=2026-04-02T10:48:25.773917752Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.773959285Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=39.246µs
ts=2026-04-02T10:48:25.773975095Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774014988Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.977µs
level=info ts=2026-04-02T10:48:25.774022812Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20540"
ts=2026-04-02T10:48:25.774047292Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774087149Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.729µs
ts=2026-04-02T10:48:25.77410551Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.77414756Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=39.017µs
level=info ts=2026-04-02T10:48:25.77415562Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20541"
ts=2026-04-02T10:48:25.774177335Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774216367Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.068µs
ts=2026-04-02T10:48:25.774239656Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774277849Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.076µs
level=info ts=2026-04-02T10:48:25.77428465Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20542"
ts=2026-04-02T10:48:25.774310393Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774349691Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=37.224µs
ts=2026-04-02T10:48:25.774366176Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774406592Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=38.502µs
level=info ts=2026-04-02T10:48:25.774418214Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20543"
ts=2026-04-02T10:48:25.774441416Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774481462Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=38.199µs
ts=2026-04-02T10:48:25.774497265Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774539009Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=39.878µs
level=info ts=2026-04-02T10:48:25.77454545Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20544"
ts=2026-04-02T10:48:25.774573571Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774614831Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=38.816µs
ts=2026-04-02T10:48:25.774630117Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-04-02T10:48:25.774667356Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.401µs
level=info ts=2026-04-02T10:48:25.774675338Z caller=table_manager.go:427 index-store=boltdb-shipper-2024-01-01 msg="loading local table index_20545"
ts=2026-04-02T10:48:25.774743925Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-04-02T10:48:25.77480152Z caller=spanlogger.go:86 level=info msg="table cache built" duration=53.779µs
level=info ts=2026-04-02T10:48:25.779479847Z caller=table_manager.go:271 index-store=boltdb-shipper-2024-01-01 msg="query readiness setup completed" duration=1.332µs distinct_users_len=0 distinct_users=
level=info ts=2026-04-02T10:48:25.779508535Z caller=shipper.go:165 index-store=boltdb-shipper-2024-01-01 msg="starting index shipper in RW mode"
level=info ts=2026-04-02T10:48:25.779751629Z caller=table_manager.go:240 index-store=boltdb-shipper-2024-01-01 msg="loading table index_20545"
level=info ts=2026-04-02T10:48:25.785691029Z caller=table.go:318 msg="handing over indexes to shipper index_20545"
level=info ts=2026-04-02T10:48:25.785719819Z caller=table.go:334 msg="finished handing over table index_20545"
level=info ts=2026-04-02T10:48:25.785745856Z caller=shipper_index_client.go:76 index-store=boltdb-shipper-2024-01-01 msg="starting boltdb shipper in RW mode"
level=info ts=2026-04-02T10:48:25.785814507Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-04-02T10:48:25.785879776Z caller=table.go:318 msg="handing over indexes to shipper index_20545"
level=info ts=2026-04-02T10:48:25.785886487Z caller=table.go:334 msg="finished handing over table index_20545"
level=info ts=2026-04-02T10:48:25.788289016Z caller=worker.go:112 msg="Starting querier worker using query-scheduler and scheduler ring for addresses"
level=warn ts=2026-04-02T10:48:25.789903324Z caller=modules.go:951 msg="RulerStorage is nil. Not starting the ruler."
level=info ts=2026-04-02T10:48:25.791220035Z caller=module_service.go:82 msg=initialising module=cache-generation-loader
level=info ts=2026-04-02T10:48:25.791233199Z caller=module_service.go:82 msg=initialising module=server
level=info ts=2026-04-02T10:48:25.791259268Z caller=module_service.go:82 msg=initialising module=memberlist-kv
level=info ts=2026-04-02T10:48:25.79129651Z caller=module_service.go:82 msg=initialising module=query-frontend-tripperware
level=info ts=2026-04-02T10:48:25.791314326Z caller=module_service.go:82 msg=initialising module=ring
level=info ts=2026-04-02T10:48:25.791314146Z caller=module_service.go:82 msg=initialising module=query-scheduler-ring
level=info ts=2026-04-02T10:48:25.79134539Z caller=module_service.go:82 msg=initialising module=store
level=info ts=2026-04-02T10:48:25.791378041Z caller=ring.go:273 msg="ring doesn't exist in KV store yet"
level=info ts=2026-04-02T10:48:25.79138486Z caller=ring.go:273 msg="ring doesn't exist in KV store yet"
level=info ts=2026-04-02T10:48:25.791422878Z caller=module_service.go:82 msg=initialising module=ingester-querier
level=info ts=2026-04-02T10:48:25.791432551Z caller=module_service.go:82 msg=initialising module=analytics
level=info ts=2026-04-02T10:48:25.791421849Z caller=basic_lifecycler.go:297 msg="instance not found in the ring" instance=loki-6dd797b766-jhxtj ring=scheduler
level=info ts=2026-04-02T10:48:25.791443954Z caller=basic_lifecycler_delegates.go:63 msg="not loading tokens from file, tokens file path is empty"
level=info ts=2026-04-02T10:48:25.791529566Z caller=ringmanager.go:201 msg="waiting until scheduler is JOINING in the ring"
level=info ts=2026-04-02T10:48:25.791595835Z caller=module_service.go:82 msg=initialising module=ingester
level=info ts=2026-04-02T10:48:25.791599728Z caller=module_service.go:82 msg=initialising module=compactor
level=info ts=2026-04-02T10:48:25.791606218Z caller=module_service.go:82 msg=initialising module=distributor
level=info ts=2026-04-02T10:48:25.791612127Z caller=ingester.go:431 msg="recovering from checkpoint"
level=info ts=2026-04-02T10:48:25.791632766Z caller=ring.go:273 msg="ring doesn't exist in KV store yet"
level=info ts=2026-04-02T10:48:25.791662108Z caller=ring.go:273 msg="ring doesn't exist in KV store yet"
level=info ts=2026-04-02T10:48:25.791670362Z caller=basic_lifecycler.go:297 msg="instance not found in the ring" instance=loki-6dd797b766-jhxtj ring=compactor
level=info ts=2026-04-02T10:48:25.791676511Z caller=basic_lifecycler.go:297 msg="instance not found in the ring" instance=loki-6dd797b766-jhxtj ring=distributor
level=info ts=2026-04-02T10:48:25.791684013Z caller=basic_lifecycler_delegates.go:63 msg="not loading tokens from file, tokens file path is empty"
level=info ts=2026-04-02T10:48:25.791788114Z caller=compactor.go:395 msg="waiting until compactor is JOINING in the ring"
level=info ts=2026-04-02T10:48:25.791795334Z caller=compactor.go:399 msg="compactor is JOINING in the ring"
level=info ts=2026-04-02T10:48:25.791829157Z caller=compactor.go:409 msg="waiting until compactor is ACTIVE in the ring"
level=info ts=2026-04-02T10:48:25.801341645Z caller=ingester.go:447 msg="recovered WAL checkpoint recovery finished" elapsed=9.737981ms errors=false
level=info ts=2026-04-02T10:48:25.801365523Z caller=ingester.go:453 msg="recovering from WAL"
level=info ts=2026-04-02T10:48:25.896973637Z caller=ringmanager.go:205 msg="scheduler is JOINING in the ring"
level=info ts=2026-04-02T10:48:25.897110387Z caller=ringmanager.go:214 msg="waiting until scheduler is ACTIVE in the ring"
level=info ts=2026-04-02T10:48:25.923175744Z caller=compactor.go:413 msg="compactor is ACTIVE in the ring"
level=info ts=2026-04-02T10:48:26.093645032Z caller=ringmanager.go:218 msg="scheduler is ACTIVE in the ring"
level=info ts=2026-04-02T10:48:26.093716451Z caller=module_service.go:82 msg=initialising module=query-scheduler
level=info ts=2026-04-02T10:48:26.093799631Z caller=module_service.go:82 msg=initialising module=query-frontend
level=info ts=2026-04-02T10:48:26.093873658Z caller=module_service.go:82 msg=initialising module=querier
level=info ts=2026-04-02T10:48:28.302558115Z caller=ingester.go:469 msg="WAL segment recovery finished" elapsed=2.510954285s errors=false
level=info ts=2026-04-02T10:48:28.302589001Z caller=ingester.go:417 msg="closing recoverer"
level=info ts=2026-04-02T10:48:28.302599142Z caller=ingester.go:425 msg="WAL recovery finished" time=2.51099615s
level=info ts=2026-04-02T10:48:28.30262085Z caller=wal.go:156 msg=started component=wal
level=info ts=2026-04-02T10:48:28.302649333Z caller=lifecycler.go:614 msg="not loading tokens from file, tokens file path is empty"
level=info ts=2026-04-02T10:48:28.302697745Z caller=lifecycler.go:643 msg="instance not found in ring, adding with no tokens" ring=ingester
level=info ts=2026-04-02T10:48:28.302761853Z caller=lifecycler.go:483 msg="auto-joining cluster after timeout" ring=ingester
level=info ts=2026-04-02T10:48:28.302773988Z caller=loki.go:505 msg="Loki started"
level=info ts=2026-04-02T10:48:29.094636487Z caller=worker.go:209 msg="adding connection" addr=192.168.2.175:9095
level=info ts=2026-04-02T10:48:29.094647766Z caller=scheduler.go:615 msg="this scheduler is in the ReplicationSet, will now accept requests."
level=info ts=2026-04-02T10:48:30.923990166Z caller=compactor.go:474 msg="this instance has been chosen to run the compactor, starting compactor"
level=info ts=2026-04-02T10:48:30.924066424Z caller=compactor.go:503 msg="waiting 10m0s for ring to stay stable and previous compactions to finish before starting compactor"
level=info ts=2026-04-02T10:48:36.094100644Z caller=frontend_scheduler_worker.go:107 msg="adding connection to scheduler" addr=192.168.2.175:9095
