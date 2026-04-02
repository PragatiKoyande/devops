D:\Pragati\DEV-Deployment\Grafana-Deployment>kubectl describe pod loki-58595d499c-t7k8b -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-58595d499c-t7k8b
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b/10.244.5.99
Start Time:       Thu, 02 Apr 2026 12:12:28 +0530
Labels:           app=loki
                  pod-template-hash=58595d499c
Annotations:      <none>
Status:           Pending
IP:
IPs:              <none>
Controlled By:    ReplicaSet/loki-58595d499c
Containers:
  loki:
    Container ID:
    Image:         h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
    Image ID:
    Port:          3100/TCP
    Host Port:     0/TCP
    Args:
      -config.file=/etc/loki/loki.yaml
    State:          Waiting
      Reason:       ContainerCreating
    Ready:          False
    Restart Count:  0
    Limits:
      cpu:     1
      memory:  1Gi
    Requests:
      cpu:        250m
      memory:     512Mi
    Liveness:     http-get http://:3100/ready delay=30s timeout=1s period=20s #success=1 #failure=5
    Readiness:    http-get http://:3100/ready delay=10s timeout=1s period=10s #success=1 #failure=5
    Startup:      http-get http://:3100/ready delay=0s timeout=1s period=10s #success=1 #failure=30
    Environment:  <none>
    Mounts:
      /etc/loki from config (ro)
      /var/loki from storage (rw)
Conditions:
  Type                        Status
  PodReadyToStartContainers   False
  Initialized                 True
  Ready                       False
  ContainersReady             False
  PodScheduled                True
Volumes:
  config:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      loki-config
    Optional:  false
  storage:
    Type:                     PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName:                loki-pvc
    ReadOnly:                 false
QoS Class:                    Burstable
Node-Selectors:               <none>
Tolerations:                  node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                              node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Topology Spread Constraints:  kubernetes.io/hostname:ScheduleAnyway when max skew 1 is exceeded for selector app=loki
Events:
  Type     Reason              Age   From                     Message
  ----     ------              ----  ----                     -------
  Normal   Scheduled           3m    default-scheduler        Successfully assigned logging/loki-58595d499c-t7k8b to h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b
  Warning  FailedAttachVolume  3m    attachdetach-controller  Multi-Attach error for volume "pvc-2ce37aeb-8eb4-46a1-99e1-c5768c16a39b" Volume is already used by pod(s) loki-58595d499c-hqtzg


  this is decribe command
