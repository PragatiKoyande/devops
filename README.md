
[root@fcsitgateway SIT-Grafana]# kubectl describe volumeattachment csi-60aec5123627d0864f2fbc7c3db250e7b1e58b5bcee1f99895814968110a6a3d
Name:         csi-60aec5123627d0864f2fbc7c3db250e7b1e58b5bcee1f99895814968110a6a3d
Namespace:
Labels:       <none>
Annotations:  csi.alpha.kubernetes.io/node-id: h06vkssitcbopscls-node-pool-1-2nb6d-qhtlx-t6s7f
API Version:  storage.k8s.io/v1
Kind:         VolumeAttachment
Metadata:
  Creation Timestamp:  2026-09-08T16:48:01Z
  Finalizers:
    external-attacher/csi-vsphere-vmware-com
  Resource Version:  113439746
  UID:               92894e6c-efd9-40a0-8d7f-61b30bb209bb
Spec:
  Attacher:   csi.vsphere.vmware.com
  Node Name:  h06vkssitcbopscls-node-pool-1-2nb6d-qhtlx-t6s7f
  Source:
    Persistent Volume Name:  pvc-b5d60fbd-9a4f-4d1a-8875-bba9e53f2a71
Status:
  Attached:  true
  Attachment Metadata:
    Disk UUID:  6000c2952dadaf965fec660abcd398fd
    Type:       vSphere CNS Block Volume
Events:         <none>
[root@fcsitgateway SIT-Grafana]# kubectl get pv pvc-b5d60fbd-9a4f-4d1a-8875-bba9e53f2a71 -o yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  annotations:
    pv.kubernetes.io/provisioned-by: csi.vsphere.vmware.com
    volume.kubernetes.io/provisioner-deletion-secret-name: ""
    volume.kubernetes.io/provisioner-deletion-secret-namespace: ""
  creationTimestamp: "2026-08-14T12:07:42Z"
  finalizers:
  - kubernetes.io/pv-protection
  - external-attacher/csi-vsphere-vmware-com
  name: pvc-b5d60fbd-9a4f-4d1a-8875-bba9e53f2a71
  resourceVersion: "103874150"
  uid: af67e010-e023-4447-8b61-1b1e67a4d0fb
spec:
  accessModes:
  - ReadWriteOnce
  capacity:
    storage: 5Gi
  claimRef:
    apiVersion: v1
    kind: PersistentVolumeClaim
    name: debezium-pvc
    namespace: backend
    resourceVersion: "103874108"
    uid: b5d60fbd-9a4f-4d1a-8875-bba9e53f2a71
  csi:
    driver: csi.vsphere.vmware.com
    fsType: ext4
    volumeAttributes:
      storage.kubernetes.io/csiProvisionerIdentity: 1785886244445-1429-csi.vsphere.vmware.com
      type: vSphere CNS Block Volume
    volumeHandle: 0b8f4e85-183c-402b-934a-ac8d2d662d9f-b5d60fbd-9a4f-4d1a-8875-bba9e53f2a71
  persistentVolumeReclaimPolicy: Delete
  storageClassName: h06-vks-sp-6
  volumeMode: Filesystem
status:
  lastPhaseTransitionTime: "2026-08-14T12:07:42Z"
  phase: Bound
