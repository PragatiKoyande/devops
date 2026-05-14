goroutine 13 [running]:
syscall.(*LazyProc).mustFind(...)
        syscall/dll_windows.go:270
syscall.(*LazyProc).Addr(...)
        syscall/dll_windows.go:277
internal/syscall/windows.GetAdaptersAddresses(0x0, 0x90, 0xc0008080a0?, 0xc0002e1b80?, 0x7ff7241e8da5?)
        internal/syscall/windows/zsyscall_windows.go:259 +0xa6
net.adapterAddresses()
        net/interface_windows.go:24 +0x59
net.dnsReadConfig({0x1?, 0x7ff72418a5bb?})
        net/dnsconfig_windows.go:24 +0xa5
net.(*resolverConfig).init(0x7ff728038b80)
        net/dnsclient_unix.go:377 +0x28
sync.(*Once).doSlow(0xa?, 0x8?)
        sync/once.go:78 +0xac
sync.(*Once).Do(...)
        sync/once.go:69
net.(*resolverConfig).tryUpdate(0x7ff728038b80, {0x7ff726510003, 0x10})
        net/dnsclient_unix.go:389 +0x59
net.getSystemDNSConfig(...)
        net/dnsclient_unix.go:369
net.(*Resolver).lookupIP.func1()
        net/lookup_windows.go:124 +0x11c
net.(*Resolver).lookupIP.func2()
        net/lookup_windows.go:165 +0x22
created by net.(*Resolver).lookupIP in goroutine 12
        net/lookup_windows.go:164 +0x209



getting this issue and not working
