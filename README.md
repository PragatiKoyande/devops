kubectl logs -n vmware-system-csi vsphere-csi-node-2kv82 --all-containers --since=30m


kubectl describe volumeattachment csi-60aec5123627d0864f2fbc7c3db250e7b1e58b5bcee1f99895814968110a6a3d


kubectl get pv pvc-b5d60fbd-9a4f-4d1a-8875-bba9e53f2a71 -o yaml