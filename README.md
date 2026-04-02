D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pod loki-56f4c8c9d9-mj55t -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-56f4c8c9d9-mj55t
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b/10.244.5.99
Start Time:       Thu, 02 Apr 2026 18:28:41 +0530
Labels:           app=loki
                  pod-template-hash=56f4c8c9d9
Annotations:      <none>
Status:           Running
IP:               192.168.2.181
IPs:
  IP:           192.168.2.181
Controlled By:  ReplicaSet/loki-56f4c8c9d9
Containers:
  loki:
    Container ID:  containerd://e756df663cc6422b28f1ccc60e47b6df060d75356ff562337fd28aba9c082f57
    Image:         h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
    Image ID:      h06vksharbor.corp.ad.sbi/cbops/grafana/loki@sha256:4a825ed37cf574f9cfeda62bd50c00fa1020b0aca8202aaa42cd0c0e5bfe0f63
    Port:          3100/TCP
    Host Port:     0/TCP
    Args:
      -config.file=/etc/loki/loki.yaml
    State:          Running
      Started:      Thu, 02 Apr 2026 18:30:57 +0530
    Last State:     Terminated
      Reason:       OOMKilled
      Exit Code:    137
      Started:      Thu, 02 Apr 2026 18:28:45 +0530
      Finished:     Thu, 02 Apr 2026 18:30:57 +0530
    Ready:          False
    Restart Count:  1
    Limits:
      cpu:     1
      memory:  2Gi
    Requests:
      cpu:        250m
      memory:     1Gi
    Liveness:     http-get http://:3100/ready delay=90s timeout=1s period=15s #success=1 #failure=3
    Readiness:    http-get http://:3100/ready delay=30s timeout=1s period=10s #success=1 #failure=3
    Startup:      http-get http://:3100/ready delay=0s timeout=1s period=10s #success=1 #failure=60
    Environment:  <none>
    Mounts:
      /etc/loki from config (ro)
      /tmp from tmp (rw)
      /var/loki from storage (rw)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
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
  Type     Reason                  Age                  From                     Message
  ----     ------                  ----                 ----                     -------
  Normal   Scheduled               2m50s                default-scheduler        Successfully assigned logging/loki-56f4c8c9d9-mj55t to h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b
  Normal   SuccessfulAttachVolume  2m50s                attachdetach-controller  AttachVolume.Attach succeeded for volume "pvc-6f477084-8be0-4bc5-9659-739ccc11cd33"
  Normal   Pulled                  35s (x2 over 2m47s)  kubelet                  Container image "h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4" already present on machine
  Normal   Created                 35s (x2 over 2m47s)  kubelet                  Created container: loki
  Normal   Started                 35s (x2 over 2m47s)  kubelet                  Started container loki
  Warning  Unhealthy               18s (x4 over 2m38s)  kubelet                  Startup probe failed: HTTP probe failed with statuscode: 503
