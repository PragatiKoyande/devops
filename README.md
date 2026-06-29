[root@fcprodkubjump media]# k exec -it notification-deployment-6fff9d966b-9257m -- env | grep -i KAFKA
E0629 12:42:17.881567  752702 runtime.go:142] "Observed a panic" panic="runtime error: invalid memory address or nil pointer dereference" panicGoValue="\"invalid memory address or nil pointer dereference\"" stacktrace=<
                                                                                                                                                                                                                                goroutine 106 [running]:
                k8s.io/apimachinery/pkg/util/runtime.logPanic({0x289ca38, 0x3c0f0a0}, {0x2008260, 0x3bb6560})
                                                                                                                        k8s.io/apimachinery/pkg/util/runtime/runtime.go:132 +0xbc
                                                                                                                                                                                        k8s.io/apimachinery/pkg/util/runtime.handleCrash({0x289ca38, 0x3c0f0a0}, {0x2008260, 0x3bb6560}, {0xc000114da8, 0x0, 0x0?})
                                                                                k8s.io/apimachinery/pkg/util/runtime/runtime.go:107 +0x116
                                                                                                                                                k8s.io/apimachinery/pkg/util/runtime.HandleCrash({0x0, 0x0, 0xc00074a540?})
                                                                                                                                                                                                                                        k8s.io/apimachinery/pkg/util/runtime/runtime.go:64 +0x17b
                                                        panic({0x2008260?, 0x3bb6560?})
                                                                                                runtime/panic.go:783 +0x132
                                                                                                                                k8s.io/kubectl/pkg/cmd/exec.(*terminalSizeQueueAdapter).Next(0x0?)
                                                                                                                                                                                                                k8s.io/kubectl/pkg/cmd/exec/exec.go:414 +0x15
                        k8s.io/client-go/tools/remotecommand.(*streamProtocolV3).handleResizes.func1()
                                                                                                                k8s.io/client-go/tools/remotecommand/v3.go:74 +0xac
                                                                                                                                                                        created by k8s.io/client-go/tools/remotecommand.(*streamProtocolV3).handleResizes in goroutine 103
                                        k8s.io/client-go/tools/remotecommand/v3.go:69 +0x65
                                                                                            >
                                                                                             panic: runtime error: invalid memory address or nil pointer dereference [recovered, repanicked]
                                                                                                                                                                                            [signal SIGSEGV: segmentation violation code=0x1 addr=0x18 pc=0x1bfd355]

                       goroutine 106 [running]:
                                               k8s.io/apimachinery/pkg/util/runtime.handleCrash({0x289ca38, 0x3c0f0a0}, {0x2008260, 0x3bb6560}, {0xc000483da8, 0x0, 0x0?})
                                                                                                                                                                                k8s.io/apimachinery/pkg/util/runtime/runtime.go:114 +0x1a9
                                                                                                                                                                                                                                          k8s.io/apimachinery/pkg/util/runtime.HandleCrash({0x0, 0x0, 0xc00074a540?})
                                                                                k8s.io/apimachinery/pkg/util/runtime/runtime.go:64 +0x17b
                                                                                                                                         panic({0x2008260?, 0x3bb6560?})
                                                                                                                                                                                runtime/panic.go:783 +0x132
                                                                                                                                                                                                           k8s.io/kubectl/pkg/cmd/exec.(*terminalSizeQueueAdapter).Next(0x0?)
                                        k8s.io/kubectl/pkg/cmd/exec/exec.go:414 +0x15
                                                                                     k8s.io/client-go/tools/remotecommand.(*streamProtocolV3).handleResizes.func1()
                                                                                                                                                                        k8s.io/client-go/tools/remotecommand/v3.go:74 +0xac
                                                                                                                                                                                                                           created by k8s.io/client-go/tools/remotecommand.(*streamProtocolV3).handleResizes in goroutine 103
                                                                                        k8s.io/client-go/tools/remotecommand/v3.go:69 +0x65
