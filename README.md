logger=settings t=2026-02-27T06:53:58.147242854Z level=info msg="Starting Grafana" version=10.2.3 commit=1e84fede543acc892d2a2515187e545eb047f237 branch=HEAD compiled=2023-12-18T15:46:07Z
logger=settings t=2026-02-27T06:53:58.147499455Z level=info msg="Config loaded from" file=/usr/share/grafana/conf/defaults.ini
logger=settings t=2026-02-27T06:53:58.147511711Z level=info msg="Config loaded from" file=/etc/grafana/grafana.ini
logger=settings t=2026-02-27T06:53:58.147516181Z level=info msg="Config overridden from command line" arg="default.paths.data=/var/lib/grafana"
logger=settings t=2026-02-27T06:53:58.147527054Z level=info msg="Config overridden from command line" arg="default.paths.logs=/var/log/grafana"
logger=settings t=2026-02-27T06:53:58.147530162Z level=info msg="Config overridden from command line" arg="default.paths.plugins=/var/lib/grafana/plugins"
logger=settings t=2026-02-27T06:53:58.147534486Z level=info msg="Config overridden from command line" arg="default.paths.provisioning=/etc/grafana/provisioning"
logger=settings t=2026-02-27T06:53:58.14753762Z level=info msg="Config overridden from command line" arg="default.log.mode=console"
logger=settings t=2026-02-27T06:53:58.147540914Z level=info msg="Config overridden from Environment variable" var="GF_PATHS_DATA=/var/lib/grafana"
logger=settings t=2026-02-27T06:53:58.147548301Z level=info msg="Config overridden from Environment variable" var="GF_PATHS_LOGS=/var/log/grafana"
logger=settings t=2026-02-27T06:53:58.14755161Z level=info msg="Config overridden from Environment variable" var="GF_PATHS_PLUGINS=/var/lib/grafana/plugins"
logger=settings t=2026-02-27T06:53:58.147561652Z level=info msg="Config overridden from Environment variable" var="GF_PATHS_PROVISIONING=/etc/grafana/provisioning"
logger=settings t=2026-02-27T06:53:58.147567721Z level=info msg="Config overridden from Environment variable" var="GF_SERVER_HTTP_ADDR=0.0.0.0"
logger=settings t=2026-02-27T06:53:58.14757051Z level=info msg="Config overridden from Environment variable" var="GF_SERVER_DOMAIN=fincoreuat.sbi"
logger=settings t=2026-02-27T06:53:58.147572689Z level=info msg="Config overridden from Environment variable" var="GF_SERVER_ROOT_URL=https://fincore-uat.sbi/grafana/"
logger=settings t=2026-02-27T06:53:58.147574943Z level=info msg="Config overridden from Environment variable" var="GF_SERVER_SERVE_FROM_SUB_PATH=true"
logger=settings t=2026-02-27T06:53:58.14757706Z level=info msg="Config overridden from Environment variable" var="GF_SECURITY_ADMIN_USER=admin"
logger=settings t=2026-02-27T06:53:58.147579696Z level=info msg=Target target=[all]
logger=settings t=2026-02-27T06:53:58.147587721Z level=info msg="Path Home" path=/usr/share/grafana
logger=settings t=2026-02-27T06:53:58.147595115Z level=info msg="Path Data" path=/var/lib/grafana
logger=settings t=2026-02-27T06:53:58.147600892Z level=info msg="Path Logs" path=/var/log/grafana
logger=settings t=2026-02-27T06:53:58.147603022Z level=info msg="Path Plugins" path=/var/lib/grafana/plugins
logger=settings t=2026-02-27T06:53:58.147610561Z level=info msg="Path Provisioning" path=/etc/grafana/provisioning
logger=settings t=2026-02-27T06:53:58.147616643Z level=info msg="App mode production"
logger=sqlstore t=2026-02-27T06:53:58.147945161Z level=info msg="Connecting to DB" dbtype=sqlite3
logger=migrator t=2026-02-27T06:53:58.148684325Z level=info msg="Starting DB migrations"
logger=migrator t=2026-02-27T06:53:58.172486297Z level=info msg="migrations completed" performed=0 skipped=523 duration=348.283µs
logger=secrets t=2026-02-27T06:53:58.173251719Z level=info msg="Envelope encryption state" enabled=true currentprovider=secretKey.v1
logger=plugin.store t=2026-02-27T06:53:58.181451294Z level=info msg="Loading plugins..."
logger=local.finder t=2026-02-27T06:53:58.21374172Z level=warn msg="Skipping finding plugins as directory does not exist" path=/usr/share/grafana/plugins-bundled
logger=plugin.store t=2026-02-27T06:53:58.214210726Z level=info msg="Plugins loaded" count=55 duration=32.760125ms
logger=query_data t=2026-02-27T06:53:58.226833349Z level=info msg="Query Service initialization"
logger=live.push_http t=2026-02-27T06:53:58.231559944Z level=info msg="Live Push Gateway initialization"
logger=ngalert.migration t=2026-02-27T06:53:58.235489012Z level=info msg=Starting
logger=ngalert.migration CurrentType=UnifiedAlerting DesiredType=UnifiedAlerting CleanOnDowngrade=false CleanOnUpgrade=false t=2026-02-27T06:53:58.23608779Z level=info msg="Migration already complete"
logger=infra.usagestats.collector t=2026-02-27T06:53:58.247298799Z level=info msg="registering usage stat providers" usageStatsProvidersLen=2
logger=provisioning.alerting t=2026-02-27T06:53:58.247472313Z level=info msg="starting to provision alerting"
logger=provisioning.alerting t=2026-02-27T06:53:58.24748279Z level=info msg="finished to provision alerting"
logger=grafanaStorageLogger t=2026-02-27T06:53:58.247704416Z level=info msg="Storage starting"
logger=ngalert.state.manager t=2026-02-27T06:53:58.247863112Z level=info msg="Warming state cache for startup"
logger=ngalert.multiorg.alertmanager t=2026-02-27T06:53:58.248036553Z level=info msg="Starting MultiOrg Alertmanager"
logger=http.server t=2026-02-27T06:53:58.249547059Z level=info msg="HTTP Server Listen" address=[::]:3000 protocol=http subUrl=/grafana socket=
logger=plugin.signature.key_retriever t=2026-02-27T06:53:58.273773788Z level=error msg="Error downloading plugin manifest keys" error="Get \"https://grafana.com/api/plugins/ci/keys\": dial tcp: lookup grafana.com on 10.96.0.10:53: no such host"
logger=grafana.update.checker t=2026-02-27T06:53:58.273816416Z level=error msg="Update check failed" error="failed to get latest.json repo from github.com: Get \"https://raw.githubusercontent.com/grafana/grafana/main/latest.json\": dial tcp: lookup raw.githubusercontent.com on 10.96.0.10:53: no such host" duration=26.056956ms
logger=ngalert.state.manager t=2026-02-27T06:53:58.334313043Z level=info msg="State cache has been initialized" states=0 duration=86.446876ms
logger=ngalert.scheduler t=2026-02-27T06:53:58.334347477Z level=info msg="Starting scheduler" tickInterval=10s
logger=ticker t=2026-02-27T06:53:58.334409168Z level=info msg=starting first_tick=2026-02-27T06:54:00Z
logger=infra.usagestats t=2026-02-27T06:54:45.254688248Z level=info msg="Usage stats are ready to report"
logger=plugin.signature.key_retriever t=2026-02-27T06:54:58.322238258Z level=error msg="Error downloading plugin manifest keys" error="Get \"https://grafana.com/api/plugins/ci/keys\": dial tcp: lookup grafana.com on 10.96.0.10:53: no such host
