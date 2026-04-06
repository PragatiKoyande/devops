
D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl logs loki-7974ccfdd5-q9b45  -n logging --kubeconfig h06vksuatcbopscls.conf
level=warn ts=2026-04-06T08:05:13.759820826Z caller=loki.go:288 msg="global timeout not configured, using default engine timeout (\"5m0s\"). This behavior will change in the next major to always use the default global timeout (\"5m\")."
level=info ts=2026-04-06T08:05:13.760591963Z caller=main.go:108 msg="Starting Loki" version="(version=2.9.4, branch=HEAD, revision=f599ebc535)"
level=info ts=2026-04-06T08:05:13.761511119Z caller=server.go:322 http=[::]:3100 grpc=[::]:9095 msg="server listening on addresses"
level=info ts=2026-04-06T08:05:13.762318335Z caller=modules.go:932 msg="Ruler storage is not configured; ruler will not be started."
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
level=error ts=2026-04-06T08:05:18.745979124Z caller=log.go:230 msg="error running loki" err="failed to init delete store: timeout\nerror initialising module: compactor\ngithub.com/grafana/dskit/modules.(*Manager).initModule\n\t/src/loki/vendor/github.com/grafana/dskit/modules/modules.go:138\ngithub.com/grafana/dskit/modules.(*Manager).InitModuleServices\n\t/src/loki/vendor/github.com/grafana/dskit/modules/modules.go:108\ngithub.com/grafana/loki/pkg/loki.(*Loki).Run\n\t/src/loki/pkg/loki/loki.go:461\nmain.main\n\t/src/loki/cmd/loki/main.go:110\nruntime.main\n\t/usr/local/go/src/runtime/proc.go:267\nruntime.goexit\n\t/usr/local/go/src/runtime/asm_amd64.s:1650"
