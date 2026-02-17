Name:             fluent-bit-bhx4f
Namespace:        logging
Priority:         0
Service Account:  fluent-bit
Node:             h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-sb28w/10.244.7.83
Start Time:       Tue, 17 Feb 2026 11:27:13 +0530
Labels:           app=fluent-bit
                  controller-revision-hash=5b8f9cb74f
                  pod-template-generation=20
Annotations:      kubectl.kubernetes.io/restartedAt: 2026-02-17T11:27:12+05:30
Status:           Running
IP:               192.168.2.181
IPs:
  IP:           192.168.2.181
Controlled By:  DaemonSet/fluent-bit
Containers:
  fluent-bit:
    Container ID:   containerd://072fbc0be36dc379d2b13d979e3d5ff61131253e4779b7d4288365e0161cd7ed
    Image:          h06vksharbor.corp.ad.sbi/cbops/fluent-bit-2.2.2
    Image ID:       h06vksharbor.corp.ad.sbi/cbops/fluent-bit-2.2.2@sha256:b2d953d412cf1fb0b615f0fc3a7c6a019e61459c790c26de7911826c42243316
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Tue, 17 Feb 2026 11:27:14 +0530
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /fluent-bit/etc from config (rw)
      /var/log from varlog (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-2ng87 (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       True
  ContainersReady             True
  PodScheduled                True
Volumes:
  varlog:
    Type:          HostPath (bare host directory volume)
    Path:          /var/log
    HostPathType:
  config:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      fluent-bit-config
    Optional:  false
  kube-api-access-2ng87:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/disk-pressure:NoSchedule op=Exists
                             node.kubernetes.io/memory-pressure:NoSchedule op=Exists
                             node.kubernetes.io/not-ready:NoExecute op=Exists
                             node.kubernetes.io/pid-pressure:NoSchedule op=Exists
                             node.kubernetes.io/unreachable:NoExecute op=Exists
                             node.kubernetes.io/unschedulable:NoSchedule op=Exists
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  47m   default-scheduler  Successfully assigned logging/fluent-bit-bhx4f to h06vkssitcbopscls-node-pool-1-2nb6d-ff9ds-sb28w
  Normal  Pulling    47m   kubelet            Pulling image "h06vksharbor.corp.ad.sbi/cbops/fluent-bit-2.2.2"
  Normal  Pulled     47m   kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/fluent-bit-2.2.2" in 224ms (224ms including waiting). Image size: 32412251 bytes.
  Normal  Created    47m   kubelet            Created container: fluent-bit
  Normal  Started    47m   kubelet            Started container fluent-bit
