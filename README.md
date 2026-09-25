D:\pragati\HELM_LATEST_26082026\Grafana-Deployment>kubectl get pvc -n logging --kubeconfig h06vksuatcbopscls.conf
NAME       STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
loki-pvc   Bound    pvc-b8e3cd58-c4f6-4c54-b6b4-6457a5eefcd3   100Gi      RWO            h06-vks-sp-6   <unset>                 171d

D:\pragati\HELM_LATEST_26082026\Grafana-Deployment>kubectl describe pvc loki-pvc -n logging --kubeconfig h06vksuatcbopscls.conf
Name:          loki-pvc
Namespace:     logging
StorageClass:  h06-vks-sp-6
Status:        Bound
Volume:        pvc-b8e3cd58-c4f6-4c54-b6b4-6457a5eefcd3
Labels:        <none>
Annotations:   pv.kubernetes.io/bind-completed: yes
               pv.kubernetes.io/bound-by-controller: yes
               volume.beta.kubernetes.io/storage-provisioner: csi.vsphere.vmware.com
               volume.kubernetes.io/storage-provisioner: csi.vsphere.vmware.com
               volumehealth.storage.kubernetes.io/health: accessible
               volumehealth.storage.kubernetes.io/health-timestamp: Wed Jul  8 18:52:09 UTC 2026
Finalizers:    [kubernetes.io/pvc-protection]
Capacity:      100Gi
Access Modes:  RWO
VolumeMode:    Filesystem
Used By:       loki-58886b45cd-v7blr
               loki-644c85b56-htpdd
Events:        <none>
