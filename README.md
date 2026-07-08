
[root@fcppjump PRE-PROD-Microservices]# k get networkpolicy -n backend
NAME                     POD-SELECTOR          AGE
allow-egress-to-oracle   app=debezium-server   20d
[root@fcppjump PRE-PROD-Microservices]# k describe pod debezium-server-86c8fbbbcb-g2bch -n backend
Name:             debezium-server-86c8fbbbcb-g2bch
Namespace:        backend
Priority:         0
Service Account:  default
Node:             h06vkspreprodcbopscls-node-pool-1-28vw8-qnbb2-l8ft4/10.244.7.218
Start Time:       Wed, 08 Jul 2026 09:29:00 +0530
Labels:           app=debezium-server
                  pod-template-hash=86c8fbbbcb
Annotations:      <none>
Status:           Running
IP:               192.168.5.2
IPs:
  IP:           192.168.5.2
Controlled By:  ReplicaSet/debezium-server-86c8fbbbcb
Containers:
  debezium-server:
    Container ID:   containerd://005a024c4e2457c7450f7a0e23c2b21ffa7b344ded2630fa8b5cd9ff897cc0f4
    Image:          h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1
    Image ID:       h06vksharbor.corp.ad.sbi/cbops/debezium-server@sha256:db96544a508ee71ff174bcf13ce5a02e0b5b57411d8067bafcd916cc0f0025b6
    Port:           8080/TCP
    Host Port:      0/TCP
    State:          Waiting
      Reason:       CrashLoopBackOff
    Last State:     Terminated
      Reason:       Error
      Exit Code:    1
      Started:      Wed, 08 Jul 2026 11:43:41 +0530
      Finished:     Wed, 08 Jul 2026 11:44:04 +0530
    Ready:          False
    Restart Count:  29
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
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-qw58j (ro)
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
  kube-api-access-qw58j:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    Optional:                false
    DownwardAPI:             true
QoS Class:                   Burstable
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason   Age                    From     Message
  ----     ------   ----                   ----     -------
  Normal   Created  52m (x21 over 137m)    kubelet  spec.containers{debezium-server}: Created container: debezium-server
  Normal   Pulled   3m17s (x29 over 137m)  kubelet  spec.containers{debezium-server}: Container image "h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1" already present on machine
  Warning  BackOff  106s (x575 over 136m)  kubelet  spec.containers{debezium-server}: Back-off restarting failed container debezium-server in pod debezium-server-86c8fbbbcb-g2bch_backend(6d60d71c-f4d0-47be-8ca4-f48e1637ea49)
