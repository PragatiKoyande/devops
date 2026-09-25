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
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  39m   default-scheduler  Successfully assigned logging/loki-58886b45cd-v7blr to h06vksuatcbopscls-node-pool-1-xg7gx-smcqf-5zppt

D:\pragati\HELM_LATEST_26082026\Grafana-Deployment>kubectl get pods -n logging --kubeconfig h06vksuatcbopscls.conf
NAME                    READY   STATUS              RESTARTS   AGE
fluent-bit-b7kfl        1/1     Running             0          61m
fluent-bit-m5xtx        1/1     Running             0          61m
fluent-bit-spwmd        1/1     Running             0          61m
loki-58886b45cd-v7blr   0/1     ContainerCreating   0          57m
loki-644c85b56-htpdd    0/1     ContainerCreating   0          16d
