D:\Pragati\PROD-Deployment-Test\Infra\Kafka>kubectl describe pvc kafka-data-kafka-0 -n backend --kubeconfig h06vksuatcbopscls.conf
Name:          kafka-data-kafka-0
Namespace:     backend
StorageClass:  h06-vks-sp-6
Status:        Terminating (lasts 31m)
Volume:        pvc-bd7c63a8-0ee2-496e-a439-c3462b883d53
Labels:        app=kafka
Annotations:   pv.kubernetes.io/bind-completed: yes
               pv.kubernetes.io/bound-by-controller: yes
               volume.beta.kubernetes.io/storage-provisioner: csi.vsphere.vmware.com
               volume.kubernetes.io/storage-provisioner: csi.vsphere.vmware.com
               volumehealth.storage.kubernetes.io/health: accessible
               volumehealth.storage.kubernetes.io/health-timestamp: Thu Mar  5 08:22:08 UTC 2026
Finalizers:    [kubernetes.io/pvc-protection]
Capacity:      5Gi
Access Modes:  RWO
VolumeMode:    Filesystem
Used By:       kafka-0
Events:        <none>

D:\Pragati\PROD-Deployment-Test\Infra\Kafka>kubectl get pvc -n backend --kubeconfig h06vksuatcbopscls.conf
NAME                 STATUS        VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
kafka-data-kafka-0   Terminating   pvc-bd7c63a8-0ee2-496e-a439-c3462b883d53   5Gi        RWO            h06-vks-sp-6   <unset>                 22h

THIS IS TAKING TIME. GIVE ME SOLUTION FOR THIS.
