evel=info ts=2026-02-18T06:02:33.969063914Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:02:33.969067575Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
level=info ts=2026-02-18T06:02:33.969089834Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:02:33.969132206Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:02:33.969138543Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:02:33.96915562Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:02:33.969160557Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:02:40.164036577Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:02:40.164101214Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:03:03.977717434Z caller=checkpoint.go:498 msg="atomic checkpoint finished" old=/var/loki/wal/checkpoint.000238.tmp new=/var/loki/wal/checkpoint.000238
level=info ts=2026-02-18T06:03:03.978055314Z caller=checkpoint.go:569 msg="checkpoint done" time=4m30.003789552s
level=info ts=2026-02-18T06:03:14.006510115Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:03:15.92208774Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:03:18.708128131Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:03:23.444875818Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:03:33.968965987Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:03:33.968969905Z caller=table_manager.go:228 index-store=boltdb-shipper-2024-01-01 msg="syncing tables"
level=info ts=2026-02-18T06:03:33.968996149Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:03:33.969001428Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:03:33.969006345Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:03:33.969011503Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:03:33.969014108Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:03:33.96901931Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
ts=2026-02-18T06:03:33.969032422Z caller=spanlogger.go:86 level=info msg="building table cache"
level=info ts=2026-02-18T06:03:33.969084187Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
ts=2026-02-18T06:03:33.96909362Z caller=spanlogger.go:86 level=info msg="table cache built" duration=53.974µs
level=info ts=2026-02-18T06:03:33.969116386Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:03:33.9691218Z caller=table.go:334 msg="finished handing over table index_20502"
ts=2026-02-18T06:03:33.969132696Z caller=spanlogger.go:86 level=info msg="building table names cache"
level=info ts=2026-02-18T06:03:33.96913909Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:03:33.969142526Z caller=table.go:334 msg="finished handing over table index_20501"
ts=2026-02-18T06:03:33.969182547Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=45.887µs
ts=2026-02-18T06:03:33.969192646Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.96922847Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=32.814µs
ts=2026-02-18T06:03:33.969241099Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969275965Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=32.115µs
ts=2026-02-18T06:03:33.969285134Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969324584Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=36.865µs
ts=2026-02-18T06:03:33.969337679Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969374894Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=34.722µs
ts=2026-02-18T06:03:33.96938433Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969420185Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=33.054µs
ts=2026-02-18T06:03:33.969436147Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969477728Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=39.054µs
ts=2026-02-18T06:03:33.969489695Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969527484Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=34.796µs
ts=2026-02-18T06:03:33.969539138Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969584828Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=42.041µs
ts=2026-02-18T06:03:33.969599815Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969643666Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=40.73µs
ts=2026-02-18T06:03:33.969657813Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.96969611Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=34.442µs
ts=2026-02-18T06:03:33.969707246Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969744903Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=34.587µs
ts=2026-02-18T06:03:33.969760913Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969797302Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=33.837µs
ts=2026-02-18T06:03:33.969806696Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:33.969848667Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=38.611µs
ts=2026-02-18T06:03:33.969862261Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-02-18T06:03:33.969876881Z caller=spanlogger.go:86 level=info msg="table cache built" duration=10.792µs
level=info ts=2026-02-18T06:03:33.96989767Z caller=table_manager.go:271 index-store=boltdb-shipper-2024-01-01 msg="query readiness setup completed" duration=1.875µs distinct_users_len=0 distinct_users=
level=info ts=2026-02-18T06:03:33.969906737Z caller=table_manager.go:244 index-store=boltdb-shipper-2024-01-01 msg="cleaning tables cache"
level=info ts=2026-02-18T06:03:33.969912315Z caller=table_manager.go:247 index-store=boltdb-shipper-2024-01-01 msg="cleaning up expired table index_20495"
level=info ts=2026-02-18T06:03:33.969919144Z caller=table_manager.go:247 index-store=boltdb-shipper-2024-01-01 msg="cleaning up expired table index_20497"
level=info ts=2026-02-18T06:03:33.969923605Z caller=table_manager.go:247 index-store=boltdb-shipper-2024-01-01 msg="cleaning up expired table index_20498"
level=info ts=2026-02-18T06:03:33.969927995Z caller=table_manager.go:247 index-store=boltdb-shipper-2024-01-01 msg="cleaning up expired table index_20499"
level=info ts=2026-02-18T06:03:33.969932386Z caller=table_manager.go:247 index-store=boltdb-shipper-2024-01-01 msg="cleaning up expired table index_20502"
level=info ts=2026-02-18T06:03:33.969937372Z caller=table_manager.go:247 index-store=boltdb-shipper-2024-01-01 msg="cleaning up expired table index_20501"
level=info ts=2026-02-18T06:03:33.969942535Z caller=table_manager.go:247 index-store=boltdb-shipper-2024-01-01 msg="cleaning up expired table index_20500"
level=info ts=2026-02-18T06:03:33.969945781Z caller=table_manager.go:247 index-store=boltdb-shipper-2024-01-01 msg="cleaning up expired table index_20496"
level=info ts=2026-02-18T06:03:33.96994927Z caller=table_manager.go:247 index-store=boltdb-shipper-2024-01-01 msg="cleaning up expired table index_20494"
level=info ts=2026-02-18T06:03:33.973739881Z caller=checkpoint.go:611 msg="starting checkpoint"
level=info ts=2026-02-18T06:03:33.97386115Z caller=checkpoint.go:336 msg="attempting checkpoint for" dir=/var/loki/wal/checkpoint.000239
level=info ts=2026-02-18T06:03:36.736979988Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:03:36.737033915Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
ts=2026-02-18T06:03:39.113959721Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:03:39.114119656Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=91.994µs
level=info ts=2026-02-18T06:03:39.114150804Z caller=compactor.go:683 msg="compacting table" table-name=index_20502
ts=2026-02-18T06:03:39.114252767Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-02-18T06:03:39.114270197Z caller=spanlogger.go:86 level=info msg="table cache built" duration=13.366µs
level=info ts=2026-02-18T06:03:39.114275158Z caller=table.go:132 table-name=index_20502 msg="listed files" count=1
level=info ts=2026-02-18T06:03:39.11431209Z caller=compactor.go:688 msg="finished compacting table" table-name=index_20502
level=info ts=2026-02-18T06:03:39.114320533Z caller=compactor.go:683 msg="compacting table" table-name=index_20501
ts=2026-02-18T06:03:39.114339686Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-02-18T06:03:39.114357598Z caller=spanlogger.go:86 level=info msg="table cache built" duration=14.783µs
level=info ts=2026-02-18T06:03:39.114361554Z caller=table.go:132 table-name=index_20501 msg="listed files" count=1
level=info ts=2026-02-18T06:03:39.114376525Z caller=compactor.go:688 msg="finished compacting table" table-name=index_20501
level=info ts=2026-02-18T06:04:14.007039564Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:04:15.082069213Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:04:17.914530361Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:04:24.14369883Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:04:33.953103093Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:04:33.953149246Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:04:33.968950212Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:04:33.968980542Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:04:33.968986404Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:04:33.968990997Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:04:33.968998107Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:04:33.969000947Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:04:33.969007717Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
level=info ts=2026-02-18T06:04:33.970037878Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:04:33.970068168Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:04:33.97007341Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:04:33.970090491Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:04:33.970093489Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:05:13.986433672Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:05:15.033977946Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:05:18.305020119Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:05:23.204501932Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:05:32.584126882Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:05:32.584176962Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:05:33.968982679Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:05:33.969014985Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:05:33.969021611Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:05:33.969027391Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:05:33.969032521Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:05:33.969035887Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:05:33.969039193Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
level=info ts=2026-02-18T06:05:33.970114802Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:05:33.970155725Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:05:33.97016015Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:05:33.970178596Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:05:33.970181855Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:06:14.006423582Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:06:15.59922898Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:06:17.644656729Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:06:22.416538881Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:06:32.521812536Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:06:32.521852376Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:06:33.969644154Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:06:33.969661047Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:06:33.969680779Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:06:33.969687136Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:06:33.969691965Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:06:33.969697474Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:06:33.96970038Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:06:33.969703346Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
level=info ts=2026-02-18T06:06:33.96970837Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:06:33.969714579Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:06:33.969732593Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:06:33.969735951Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:07:14.005046537Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:07:15.891726374Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:07:18.633609964Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:07:24.038326794Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:07:33.969989671Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:07:33.970008958Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:07:33.970035305Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:07:33.970040634Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:07:33.970046124Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
level=info ts=2026-02-18T06:07:33.970048183Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:07:33.970054079Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:07:33.970056783Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:07:33.970060219Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:07:33.970063788Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:07:33.970073412Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:07:33.970076963Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:07:37.84219489Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:07:37.842236908Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:07:56.79700393Z caller=flush.go:167 msg="flushing stream" user=fake fp=d94d5e7ea9d986e8 immediate=false num_chunks=1 labels="{job=\"fluentbit\", kubernetes_container_name=\"loki\", kubernetes_namespace_name=\"logging\", kubernetes_pod_name=\"loki-6f676bfbc7-986kw\"}"
level=info ts=2026-02-18T06:08:03.976483177Z caller=checkpoint.go:498 msg="atomic checkpoint finished" old=/var/loki/wal/checkpoint.000239.tmp new=/var/loki/wal/checkpoint.000239
level=info ts=2026-02-18T06:08:03.976801645Z caller=checkpoint.go:569 msg="checkpoint done" time=4m30.002828327s
level=info ts=2026-02-18T06:08:13.987590346Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:08:15.016834413Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:08:17.038205571Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:08:21.298987561Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:08:26.940580199Z caller=flush.go:167 msg="flushing stream" user=fake fp=0fbd77df24f90b44 immediate=false num_chunks=1 labels="{job=\"fluentbit\", kubernetes_container_name=\"connect\", kubernetes_namespace_name=\"cbops\", kubernetes_pod_name=\"connect-c87c7c494-wc2ml\"}"
level=info ts=2026-02-18T06:08:31.005250341Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:08:31.005299605Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:08:33.968934896Z caller=table_manager.go:228 index-store=boltdb-shipper-2024-01-01 msg="syncing tables"
ts=2026-02-18T06:08:33.968993687Z caller=spanlogger.go:86 level=info msg="building table names cache"
level=info ts=2026-02-18T06:08:33.968985199Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:08:33.969012344Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:08:33.969017613Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:08:33.969029994Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:08:33.969035993Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:08:33.969039014Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:08:33.969044588Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
ts=2026-02-18T06:08:33.969100075Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=99.882µs
ts=2026-02-18T06:08:33.969118455Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969156504Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35µs
ts=2026-02-18T06:08:33.969170186Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969205046Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=32.029µs
ts=2026-02-18T06:08:33.969214993Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969248617Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.074µs
ts=2026-02-18T06:08:33.969260215Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.96929417Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.815µs
ts=2026-02-18T06:08:33.969301492Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969335889Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=32.223µs
ts=2026-02-18T06:08:33.969349145Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-02-18T06:08:33.969362263Z caller=spanlogger.go:86 level=info msg="table cache built" duration=10.775µs
ts=2026-02-18T06:08:33.969381077Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969415467Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.883µs
ts=2026-02-18T06:08:33.969425226Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969461302Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=33.214µs
ts=2026-02-18T06:08:33.969473096Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969507025Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.36µs
ts=2026-02-18T06:08:33.969517424Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969552766Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.985µs
ts=2026-02-18T06:08:33.969564717Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969598402Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.241µs
ts=2026-02-18T06:08:33.969606966Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969641933Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=32.569µs
ts=2026-02-18T06:08:33.969652162Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.9696857Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.122µs
ts=2026-02-18T06:08:33.969692911Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:08:33.969727014Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.255µs
ts=2026-02-18T06:08:33.969739229Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-02-18T06:08:33.969751311Z caller=spanlogger.go:86 level=info msg="table cache built" duration=9.853µs
level=info ts=2026-02-18T06:08:33.969765176Z caller=table_manager.go:271 index-store=boltdb-shipper-2024-01-01 msg="query readiness setup completed" duration=1.617µs distinct_users_len=0 distinct_users=
level=info ts=2026-02-18T06:08:33.969850054Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:08:33.969892691Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:08:33.969898527Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:08:33.969916059Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:08:33.969921782Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:08:33.973788418Z caller=checkpoint.go:611 msg="starting checkpoint"
level=info ts=2026-02-18T06:08:33.973876568Z caller=checkpoint.go:336 msg="attempting checkpoint for" dir=/var/loki/wal/checkpoint.000240
level=info ts=2026-02-18T06:09:14.006551338Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:09:15.995175049Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:09:19.443967782Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:09:23.792578382Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:09:33.968955787Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:09:33.968992323Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:09:33.968998422Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:09:33.969003655Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:09:33.969009162Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:09:33.9690122Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:09:33.969015779Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
level=info ts=2026-02-18T06:09:33.97016869Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:09:33.970219788Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:09:33.970225411Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:09:33.970243588Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:09:33.970249499Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:09:34.860622775Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:09:34.860673339Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:10:14.005958027Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:10:15.206874317Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:10:17.811850041Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:10:24.082708752Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:10:33.05450308Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:10:33.054544378Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:10:33.968971382Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:10:33.968997876Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:10:33.969005546Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:10:33.96901071Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:10:33.9690162Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:10:33.969019259Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:10:33.969024564Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
level=info ts=2026-02-18T06:10:33.970090182Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:10:33.970123926Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:10:33.970128631Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:10:33.970146252Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:10:33.970152532Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:11:14.006047161Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:11:15.54351141Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:11:18.874397816Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:11:26.796896202Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:11:31.48109047Z caller=roundtrip.go:295 org_id=fake traceID=64735264fecd1098 msg="executing query" type=labels label= length=48h0m0s query=
ts=2026-02-18T06:11:31.481841095Z caller=spanlogger.go:86 user=fake level=info org_id=fake traceID=64735264fecd1098 latency=fast query_type=labels length=18h27m55.883s duration=154.394µs status=200 label= query= splits=0 throughput=0B total_bytes=0B total_entries=0
ts=2026-02-18T06:11:31.481953467Z caller=spanlogger.go:86 user=fake level=info org_id=fake traceID=64735264fecd1098 latency=fast query_type=labels length=23h59m59.999s duration=294.193µs status=200 label= query= splits=0 throughput=0B total_bytes=0B total_entries=4
ts=2026-02-18T06:11:31.482234569Z caller=spanlogger.go:86 user=fake level=info org_id=fake traceID=64735264fecd1098 latency=fast query_type=labels length=5h32m4.116s duration=574.847µs status=200 label= query= splits=0 throughput=0B total_bytes=0B total_entries=4
level=info ts=2026-02-18T06:11:31.482455216Z caller=metrics.go:207 component=frontend org_id=fake traceID=64735264fecd1098 latency=fast query_type=labels length=48h0m0s duration=1.266878ms status=200 label= query= splits=3 throughput=0B total_bytes=0B total_entries=4
level=info ts=2026-02-18T06:11:33.968944849Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:11:33.968971322Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:11:33.968976877Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:11:33.968981589Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:11:33.968987452Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:11:33.968990608Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:11:33.968993921Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
level=info ts=2026-02-18T06:11:33.970071528Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:11:33.970109521Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:11:33.970113843Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:11:33.97013284Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:11:33.970138288Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:11:37.651493152Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:11:37.651534284Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:12:14.009463462Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:12:15.929362975Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:12:18.507309371Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:12:22.575810578Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:12:32.454001147Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:12:32.454041872Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:12:33.969625631Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:12:33.969657405Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:12:33.969662765Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:12:33.969668479Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
level=info ts=2026-02-18T06:12:33.969657428Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
level=info ts=2026-02-18T06:12:33.969674294Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:12:33.969685512Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:12:33.969689642Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:12:33.969696899Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:12:33.969702688Z caller=table.go:334 msg="finished handing over table index_20501"
level=info ts=2026-02-18T06:12:33.969722681Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
level=info ts=2026-02-18T06:12:33.969728008Z caller=table.go:334 msg="finished handing over table index_20502"
level=info ts=2026-02-18T06:13:03.98510014Z caller=checkpoint.go:498 msg="atomic checkpoint finished" old=/var/loki/wal/checkpoint.000240.tmp new=/var/loki/wal/checkpoint.000240
level=info ts=2026-02-18T06:13:03.985402415Z caller=checkpoint.go:569 msg="checkpoint done" time=4m30.011399566s
level=info ts=2026-02-18T06:13:14.00600544Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:13:15.051326065Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:13:17.124733358Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:13:23.707926621Z caller=reporter.go:305 msg="failed to send usage report" retries=3 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:13:26.306493202Z caller=flush.go:167 msg="flushing stream" user=fake fp=9a130b7866c026de immediate=false num_chunks=1 labels="{job=\"fluentbit\", kubernetes_container_name=\"kafka\", kubernetes_namespace_name=\"cbops\", kubernetes_pod_name=\"kafka-0\"}"
level=info ts=2026-02-18T06:13:33.968925043Z caller=table_manager.go:228 index-store=boltdb-shipper-2024-01-01 msg="syncing tables"
level=info ts=2026-02-18T06:13:33.968946565Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=info ts=2026-02-18T06:13:33.968966877Z caller=index_set.go:86 msg="uploading table index_20501"
level=info ts=2026-02-18T06:13:33.968973683Z caller=index_set.go:107 msg="finished uploading table index_20501"
level=info ts=2026-02-18T06:13:33.968978466Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20501"
level=info ts=2026-02-18T06:13:33.968984774Z caller=index_set.go:86 msg="uploading table index_20502"
level=info ts=2026-02-18T06:13:33.968989094Z caller=index_set.go:107 msg="finished uploading table index_20502"
level=info ts=2026-02-18T06:13:33.968992556Z caller=index_set.go:185 msg="cleaning up unwanted indexes from table index_20502"
ts=2026-02-18T06:13:33.969002705Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-02-18T06:13:33.969071315Z caller=spanlogger.go:86 level=info msg="table cache built" duration=54.744µs
level=info ts=2026-02-18T06:13:33.969087811Z caller=table_manager.go:171 index-store=boltdb-shipper-2024-01-01 msg="handing over indexes to shipper"
ts=2026-02-18T06:13:33.969102916Z caller=spanlogger.go:86 level=info msg="building table names cache"
level=info ts=2026-02-18T06:13:33.969142886Z caller=table.go:318 msg="handing over indexes to shipper index_20501"
level=info ts=2026-02-18T06:13:33.969148879Z caller=table.go:334 msg="finished handing over table index_20501"
ts=2026-02-18T06:13:33.969159915Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=52.794µs
level=info ts=2026-02-18T06:13:33.96916681Z caller=table.go:318 msg="handing over indexes to shipper index_20502"
ts=2026-02-18T06:13:33.969172461Z caller=spanlogger.go:86 level=info msg="building table names cache"
level=info ts=2026-02-18T06:13:33.969172565Z caller=table.go:334 msg="finished handing over table index_20502"
ts=2026-02-18T06:13:33.969208895Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=33.535µs
ts=2026-02-18T06:13:33.96922649Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969264952Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=35.474µs
ts=2026-02-18T06:13:33.969275088Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969312577Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=34.767µs
ts=2026-02-18T06:13:33.969324596Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969359681Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=32.204µs
ts=2026-02-18T06:13:33.969368481Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969403877Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=32.303µs
ts=2026-02-18T06:13:33.96941487Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969448172Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.031µs
ts=2026-02-18T06:13:33.969456533Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969490374Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=31.222µs
ts=2026-02-18T06:13:33.969503267Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969536139Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=30.819µs
ts=2026-02-18T06:13:33.969544798Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969577882Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=30.734µs
ts=2026-02-18T06:13:33.969596734Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969633823Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=34.172µs
ts=2026-02-18T06:13:33.969642718Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969675169Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=30.098µs
ts=2026-02-18T06:13:33.969687237Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969722976Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=32.733µs
ts=2026-02-18T06:13:33.969732547Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:33.969768435Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=32.842µs
ts=2026-02-18T06:13:33.969785995Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-02-18T06:13:33.969799531Z caller=spanlogger.go:86 level=info msg="table cache built" duration=10.663µs
level=info ts=2026-02-18T06:13:33.969815231Z caller=table_manager.go:271 index-store=boltdb-shipper-2024-01-01 msg="query readiness setup completed" duration=1.748µs distinct_users_len=0 distinct_users=
level=info ts=2026-02-18T06:13:33.973727105Z caller=checkpoint.go:611 msg="starting checkpoint"
level=info ts=2026-02-18T06:13:33.973820141Z caller=checkpoint.go:336 msg="attempting checkpoint for" dir=/var/loki/wal/checkpoint.000241
level=info ts=2026-02-18T06:13:36.42754616Z caller=reporter.go:305 msg="failed to send usage report" retries=4 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:13:36.427590642Z caller=reporter.go:281 msg="failed to report usage" err="5 errors: Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host; Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
ts=2026-02-18T06:13:39.114076604Z caller=spanlogger.go:86 level=info msg="building table names cache"
ts=2026-02-18T06:13:39.114237564Z caller=spanlogger.go:86 level=info msg="table names cache built" duration=105.283µs
level=info ts=2026-02-18T06:13:39.114262731Z caller=compactor.go:683 msg="compacting table" table-name=index_20502
ts=2026-02-18T06:13:39.11434267Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-02-18T06:13:39.114359765Z caller=spanlogger.go:86 level=info msg="table cache built" duration=13.191µs
level=info ts=2026-02-18T06:13:39.114365706Z caller=table.go:132 table-name=index_20502 msg="listed files" count=1
level=info ts=2026-02-18T06:13:39.11440143Z caller=compactor.go:688 msg="finished compacting table" table-name=index_20502
level=info ts=2026-02-18T06:13:39.114410162Z caller=compactor.go:683 msg="compacting table" table-name=index_20501
ts=2026-02-18T06:13:39.114429598Z caller=spanlogger.go:86 level=info msg="building table cache"
ts=2026-02-18T06:13:39.114444309Z caller=spanlogger.go:86 level=info msg="table cache built" duration=11.633µs
level=info ts=2026-02-18T06:13:39.114447864Z caller=table.go:132 table-name=index_20501 msg="listed files" count=1
level=info ts=2026-02-18T06:13:39.1144627Z caller=compactor.go:688 msg="finished compacting table" table-name=index_20501
level=info ts=2026-02-18T06:14:13.986549937Z caller=reporter.go:305 msg="failed to send usage report" retries=0 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:14:15.636912Z caller=reporter.go:305 msg="failed to send usage report" retries=1 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
level=info ts=2026-02-18T06:14:18.542896619Z caller=reporter.go:305 msg="failed to send usage report" retries=2 err="Post \"https://stats.grafana.org/loki-usage-report\": dial tcp: lookup stats.grafana.org on 10.96.0.10:53: no such host"
