D:\pragati\HELM_LATEST_26082026\Grafana-Deployment>kubectl get events -n logging --sort-by=.lastTimestamp --kubeconfig h06vksuatcbopscls.conf
LAST SEEN   TYPE      REASON               OBJECT                       MESSAGE
60m         Normal    Scheduled            pod/loki-58886b45cd-v7blr    Successfully assigned logging/loki-58886b45cd-v7blr to h06vksuatcbopscls-node-pool-1-xg7gx-smcqf-5zppt
60m         Normal    SuccessfulCreate     replicaset/loki-58886b45cd   Created pod: loki-58886b45cd-v7blr
60m         Normal    ScalingReplicaSet    deployment/loki              Scaled up replica set loki-58886b45cd from 0 to 1
7m13s       Warning   FailedAttachVolume   pod/loki-58886b45cd-v7blr    AttachVolume.Attach failed for volume "pvc-b8e3cd58-c4f6-4c54-b6b4-6457a5eefcd3" : PersistentVolume "pvc-b8e3cd58-c4f6-4c54-b6b4-6457a5eefcd3" is marked for deletion
5m11s       Warning   FailedAttachVolume   pod/loki-644c85b56-htpdd     AttachVolume.Attach failed for volume "pvc-b8e3cd58-c4f6-4c54-b6b4-6457a5eefcd3" : PersistentVolume "pvc-b8e3cd58-c4f6-4c54-b6b4-6457a5eefcd3" is marked for deletion

D:\pragati\HELM_LATEST_26082026\Grafana-Deployment>kubectl get pods -n logging -| app=loki -o wide --kubeconfig h06vksuatcbopscls.conf
'app' is not recognized as an internal or external command,
operable program or batch file.

D:\pragati\HELM_LATEST_26082026\Grafana-Deployment>kubectl describe pod loki-58886b45cd-v7blr -n logging --kubectl h06vksuatcbopscls.conf
error: unknown flag: --kubectl
See 'kubectl describe --help' for usage.

D:\pragati\HELM_LATEST_26082026\Grafana-Deployment>kubectl describe pod loki-58886b45cd-v7blr -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-58886b45cd-v7blr
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-smcqf-5zppt/10.244.5.108
Start Time:       Fri, 25 Sep 2026 11:07:33 +0530
Labels:           app=loki
                  pod-template-hash=58886b45cd
Annotations:      <none>
Status:           Pending
IP:
IPs:              <none>
Controlled By:    ReplicaSet/loki-58886b45cd
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
  Warning  FailedAttachVolume  9m4s  attachdetach-controller  AttachVolume.Attach failed for volume "pvc-b8e3cd58-c4f6-4c54-b6b4-6457a5eefcd3" : PersistentVolume "pvc-b8e3cd58-c4f6-4c54-b6b4-6457a5eefcd3" is marked for deletion
