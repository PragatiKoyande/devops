D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl logs loki-58595d499c-d888v -n logging --kubeconfig h06vksuatcbopscls.conf
mkdir /var/loki/index_cache: no space left on device
error creating index client
github.com/grafana/loki/pkg/storage.(*store).storeForPeriod
        /src/loki/pkg/storage/store.go:295
github.com/grafana/loki/pkg/storage.(*store).init
        /src/loki/pkg/storage/store.go:177
github.com/grafana/loki/pkg/storage.NewStore
        /src/loki/pkg/storage/store.go:155
github.com/grafana/loki/pkg/loki.(*Loki).initStore
        /src/loki/pkg/loki/modules.go:689
github.com/grafana/dskit/modules.(*Manager).initModule
        /src/loki/vendor/github.com/grafana/dskit/modules/modules.go:136
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
error initialising module: store
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
level=warn ts=2026-03-13T06:18:52.197458836Z caller=store.go:56 msg="running with DEPRECATED flag -store.max-look-back-period, use -querier.max-query-lookback instead."
level=warn ts=2026-03-13T06:18:52.197533281Z caller=loki.go:288 msg="global timeout not configured, using default engine timeout (\"5m0s\"). This behavior will change in the next major to always use the default global timeout (\"5m\")."
level=info ts=2026-03-13T06:18:52.199014307Z caller=main.go:108 msg="Starting Loki" version="(version=2.9.4, branch=HEAD, revision=f599ebc535)"
level=info ts=2026-03-13T06:18:52.200125937Z caller=server.go:322 http=[::]:3100 grpc=[::]:9095 msg="server listening on addresses"
level=warn ts=2026-03-13T06:18:52.202792987Z caller=cache.go:127 msg="fifocache config is deprecated. use embedded-cache instead"
level=warn ts=2026-03-13T06:18:52.202825974Z caller=experimental.go:20 msg="experimental feature in use" feature="In-memory (FIFO) cache - chunksembedded-cache"
level=info ts=2026-03-13T06:18:52.203252022Z caller=table_manager.go:136 index-store=boltdb-shipper-2024-01-01 msg="uploading tables"
level=error ts=2026-03-13T06:18:52.203251909Z caller=log.go:230 msg="error running loki" err="mkdir /var/loki/index_cache: no space left on device\nerror creating index client\ngithub.com/grafana/loki/pkg/storage.(*store).storeForPeriod\n\t/src/loki/pkg/storage/store.go:295\ngithub.com/grafana/loki/pkg/storage.(*store).init\n\t/src/loki/pkg/storage/store.go:177\ngithub.com/grafana/loki/pkg/storage.NewStore\n\t/src/loki/pkg/storage/store.go:155\ngithub.com/grafana/loki/pkg/loki.(*Loki).initStore\n\t/src/loki/pkg/loki/modules.go:689\ngithub.com/grafana/dskit/modules.(*Manager).initModule\n\t/src/loki/vendor/github.com/grafana/dskit/modules/modules.go:136\ngithub.com/grafana/dskit/modules.(*Manager).InitModuleServices\n\t/src/loki/vendor/github.com/grafana/dskit/modules/modules.go:108\ngithub.com/grafana/loki/pkg/loki.(*Loki).Run\n\t/src/loki/pkg/loki/loki.go:461\nmain.main\n\t/src/loki/cmd/loki/main.go:110\nruntime.main\n\t/usr/local/go/src/runtime/proc.go:267\nruntime.goexit\n\t/usr/local/go/src/runtime/asm_amd64.s:1650\nerror initialising module: store\ngithub.com/grafana/dskit/modules.(*Manager).initModule\n\t/src/loki/vendor/github.com/grafana/dskit/modules/modules.go:138\ngithub.com/grafana/dskit/modules.(*Manager).InitModuleServices\n\t/src/loki/vendor/github.com/grafana/dskit/modules/modules.go:108\ngithub.com/grafana/loki/pkg/loki.(*Loki).Run\n\t/src/loki/pkg/loki/loki.go:461\nmain.main\n\t/src/loki/cmd/loki/main.go:110\nruntime.main\n\t/usr/local/go/src/runtime/proc.go:267\nruntime.goexit\n\t/usr/local/go/src/runtime/asm_amd64.s:1650"
