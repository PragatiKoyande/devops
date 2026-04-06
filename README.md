D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pod loki-7974ccfdd5-j8c7p  -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-7974ccfdd5-j8c7p
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-bcssn/10.244.5.101
Start Time:       Mon, 06 Apr 2026 15:58:11 +0530
Labels:           app=loki
                  pod-template-hash=7974ccfdd5
Annotations:      <none>
Status:           Pending
IP:
IPs:              <none>
Controlled By:    ReplicaSet/loki-7974ccfdd5
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
      memory:  4Gi
    Requests:
      cpu:        250m
      memory:     2Gi
    Liveness:     http-get http://:3100/ready delay=180s timeout=2s period=10s #success=1 #failure=3
    Readiness:    http-get http://:3100/ready delay=60s timeout=2s period=10s #success=1 #failure=3
    Startup:      http-get http://:3100/ready delay=0s timeout=2s period=10s #success=1 #failure=120
    Environment:  <none>
    Mounts:
      /etc/loki from config (ro)
      /tmp from tmp (rw)
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
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName:  loki-pvc
    ReadOnly:   false
  tmp:
    Type:        EmptyDir (a temporary directory that shares a pod's lifetime)
    Medium:
    SizeLimit:   <unset>
QoS Class:       Burstable
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                 node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason              Age   From                     Message
  ----     ------              ----  ----                     -------
  Normal   Scheduled           96s   default-scheduler        Successfully assigned logging/loki-7974ccfdd5-j8c7p to h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-bcssn
  Warning  FailedAttachVolume  96s   attachdetach-controller  Multi-Attach error for volume "pvc-e6c7bb00-68f9-49db-8e10-a4b8663e6bea" Volume is already used by pod(s) loki-7974ccfdd5-h7wnq



  
D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl get pods -n logging --kubeconfig h06vksuatcbopscls.conf
NAME                    READY   STATUS              RESTARTS   AGE
loki-7974ccfdd5-dlzw5   0/1     ContainerCreating   0          2m5s
loki-7974ccfdd5-h7wnq   1/1     Running             0          4m44s
loki-7974ccfdd5-j8c7p   0/1     ContainerCreating   0          2m5s


container are going in cretaing state and starting again and above is the describation
