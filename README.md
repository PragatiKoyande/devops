
D:\pragati\HELM_LATEST_26082026>k get pvc debezium-pvc
NAME           STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
debezium-pvc   Bound    pvc-b6a2575d-a8d7-4f5f-8f93-a294e56117ec   50Gi       RWO            h06-vks-sp-6   <unset>                 67d

D:\pragati\HELM_LATEST_26082026>k decsribe pvc debezium-pvc
Error: flags cannot be placed before plugin name: --kubeconfig

D:\pragati\HELM_LATEST_26082026>k describe pvc debezium-pvc
Name:          debezium-pvc
Namespace:     backend
StorageClass:  h06-vks-sp-6
Status:        Bound
Volume:        pvc-b6a2575d-a8d7-4f5f-8f93-a294e56117ec
Labels:        <none>
Annotations:   pv.kubernetes.io/bind-completed: yes
               pv.kubernetes.io/bound-by-controller: yes
               volume.beta.kubernetes.io/storage-provisioner: csi.vsphere.vmware.com
               volume.kubernetes.io/storage-provisioner: csi.vsphere.vmware.com
               volumehealth.storage.kubernetes.io/health: accessible
               volumehealth.storage.kubernetes.io/health-timestamp: Thu Sep 17 08:23:25 UTC 2026
Finalizers:    [kubernetes.io/pvc-protection]
Capacity:      50Gi
Access Modes:  RWO
VolumeMode:    Filesystem
Used By:       debezium-server-f5c5498d-9xhdt
Events:        <none>

D:\pragati\HELM_LATEST_26082026>k get pods -n backend -l app=debezium-server -o wide
NAME                             READY   STATUS             RESTARTS          AGE    IP             NODE                                              NOMINATED NODE   READINESS GATES
debezium-server-f5c5498d-9xhdt   0/1     CrashLoopBackOff   620 (3m31s ago)   2d5h   192.168.0.21   h06vksuatcbopscls-node-pool-1-xg7gx-77xrn-z7n7m   <none>           <none>

D:\pragati\HELM_LATEST_26082026>k describe pod -n backend -l app=debezium-server
Name:             debezium-server-f5c5498d-9xhdt
Namespace:        backend
Priority:         0
Service Account:  default
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-77xrn-z7n7m/10.244.5.100
Start Time:       Sun, 22 Nov 2026 05:52:58 +0530
Labels:           app=debezium-server
                  pod-template-hash=f5c5498d
Annotations:      kubectl.kubernetes.io/restartedAt: 2026-09-17T15:46:30+05:30
Status:           Running
IP:               192.168.0.21
IPs:
  IP:           192.168.0.21
Controlled By:  ReplicaSet/debezium-server-f5c5498d
Containers:
  debezium-server:
    Container ID:   containerd://4c08f12bee32c13fc44e537770a8d48636614c58ec0618a8633713aa64dab5bc
    Image:          h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1
    Image ID:       h06vksharbor.corp.ad.sbi/cbops/debezium-server@sha256:db96544a508ee71ff174bcf13ce5a02e0b5b57411d8067bafcd916cc0f0025b6
    Port:           8080/TCP
    Host Port:      0/TCP
    State:          Waiting
      Reason:       CrashLoopBackOff
    Last State:     Terminated
      Reason:       Error
      Exit Code:    1
      Started:      Tue, 24 Nov 2026 11:44:46 +0530
      Finished:     Tue, 24 Nov 2026 11:44:55 +0530
    Ready:          False
    Restart Count:  620
    Limits:
      cpu:     2
      memory:  3Gi
    Requests:
      cpu:     500m
      memory:  1Gi
    Environment:
      JAVA_OPTS:  -Xms512m -Xmx2g
    Mounts:
      /debezium/conf from config-volume (rw)
      /debezium/data from data-volume (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-j4p55 (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       False
  ContainersReady             False
  PodScheduled                True
Volumes:
  config-volume:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      debezium-server-config
    Optional:  false
  data-volume:
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName:  debezium-pvc
    ReadOnly:   false
  kube-api-access-j4p55:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   Burstable
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason   Age                       From     Message
  ----     ------   ----                      ----     -------
  Normal   Created  25m (x617 over 2d5h)      kubelet  Created container: debezium-server
  Warning  BackOff  4m26s (x14454 over 2d5h)  kubelet  Back-off restarting failed container debezium-server in pod debezium-server-f5c5498d-9xhdt_backend(db568b89-3e7e-43dc-a702-94b671f79a6f)
  Normal   Pulled   4m13s (x620 over 2d5h)    kubelet  Container image "h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1" already present on machine
