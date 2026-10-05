[root@fcsitgateway SIT-Grafana]# kubectl describe pod debezium-server-86c8fbbbcb-g7xmp
Name:             debezium-server-86c8fbbbcb-g7xmp
Namespace:        backend
Priority:         0
Service Account:  default
Node:             h06vkssitcbopscls-node-pool-1-2nb6d-qhtlx-t6s7f/10.244.7.89
Start Time:       Tue, 08 Sep 2026 15:17:45 +0530
Labels:           app=debezium-server
                  pod-template-hash=86c8fbbbcb
Annotations:      <none>
Status:           Pending
IP:
IPs:              <none>
Controlled By:    ReplicaSet/debezium-server-86c8fbbbcb
Containers:
  debezium-server:
    Container ID:
    Image:          h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1
    Image ID:
    Port:           8080/TCP
    Host Port:      0/TCP
    State:          Waiting
      Reason:       ContainerCreating
    Ready:          False
    Restart Count:  0
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
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-g4f8j (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   False
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
  kube-api-access-g4f8j:
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
  Type     Reason       Age                      From     Message
  ----     ------       ----                     ----     -------
  Warning  FailedMount  3m59s (x18880 over 26d)  kubelet  MountVolume.SetUp failed for volume "pvc-b5d60fbd-9a4f-4d1a-8875-bba9e53f2a71" : rpc error: code = FailedPrecondition desc = volume ID: "0b8f4e85-183c-402b-934a-ac8d2d662d9f-b5d60fbd-9a4f-4d1a-8875-bba9e53f2a71" does not appear staged to "/var/lib/kubelet/plugins/kubernetes.io/csi/csi.vsphere.vmware.com/8923abe49ff697861a3dc614c3bdba1daacbcd6170b9bfc4bdd312998dbc5df4/globalmount"
