D:\pragati\HELM_LATEST_26082026>k get pod debezium-reset -n backend
NAME             READY   STATUS                 RESTARTS   AGE
debezium-reset   0/1     CreateContainerError   0          19s

D:\pragati\HELM_LATEST_26082026>k logs debezium-reset -f
Error from server (BadRequest): container "reset" in pod "debezium-reset" is waiting to start: CreateContainerError

D:\pragati\HELM_LATEST_26082026>k describe pod debezium-reset
Name:             debezium-reset
Namespace:        backend
Priority:         0
Service Account:  default
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-77xrn-z7n7m/10.244.5.100
Start Time:       Tue, 24 Nov 2026 12:03:13 +0530
Labels:           <none>
Annotations:      <none>
Status:           Pending
IP:               192.168.0.27
IPs:
  IP:  192.168.0.27
Containers:
  reset:
    Container ID:
    Image:         h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1
    Image ID:
    Port:          <none>
    Host Port:     <none>
    Command:
      /bin/sh
      -c
      sleep 3600
    State:          Waiting
      Reason:       CreateContainerError
    Ready:          False
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /debezium/data from data-volume (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-cpq94 (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       False
  ContainersReady             False
  PodScheduled                True
Volumes:
  data-volume:
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName:  debezium-pvc
    ReadOnly:   false
  kube-api-access-cpq94:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason                  Age               From                     Message
  ----     ------                  ----              ----                     -------
  Normal   Scheduled               46s               default-scheduler        Successfully assigned backend/debezium-reset to h06vksuatcbopscls-node-pool-1-xg7gx-77xrn-z7n7m
  Normal   SuccessfulAttachVolume  45s               attachdetach-controller  AttachVolume.Attach succeeded for volume "pvc-b6a2575d-a8d7-4f5f-8f93-a294e56117ec"
  Warning  Failed                  40s               kubelet                  Error: failed to create containerd container: mount callback failed on /var/lib/containerd/tmpmounts/containerd-mount1816511856: no users found
  Warning  Failed                  40s               kubelet                  Error: failed to create containerd container: mount callback failed on /var/lib/containerd/tmpmounts/containerd-mount2590800210: no users found
  Warning  Failed                  27s               kubelet                  Error: failed to create containerd container: mount callback failed on /var/lib/containerd/tmpmounts/containerd-mount626508092: no users found
  Warning  Failed                  15s               kubelet                  Error: failed to create containerd container: mount callback failed on /var/lib/containerd/tmpmounts/containerd-mount1663808242: no users found
  Normal   Pulled                  3s (x5 over 40s)  kubelet                  Container image "h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1" already present on machine
  Warning  Failed                  3s                kubelet                  Error: failed to create containerd container: mount callback failed on /var/lib/containerd/tmpmounts/containerd-mount385899035: no users found
