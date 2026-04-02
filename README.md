
D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pod loki-55dcb8bbff-tcc9s -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-55dcb8bbff-tcc9s
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b/10.244.5.99
Start Time:       Thu, 02 Apr 2026 16:51:26 +0530
Labels:           app=loki
                  pod-template-hash=55dcb8bbff
Annotations:      <none>
Status:           Running
IP:               192.168.2.180
IPs:
  IP:           192.168.2.180
Controlled By:  ReplicaSet/loki-55dcb8bbff
Containers:
  loki:
    Container ID:  containerd://93dbd8fa6d79ce61774f4a4892e460826f35ca4d0a3c2975aef270c001441f41
    Image:         h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
    Image ID:      h06vksharbor.corp.ad.sbi/cbops/grafana/loki@sha256:4a825ed37cf574f9cfeda62bd50c00fa1020b0aca8202aaa42cd0c0e5bfe0f63
    Port:          3100/TCP
    Host Port:     0/TCP
    Args:
      -config.file=/etc/loki/loki.yaml
    State:          Running
      Started:      Thu, 02 Apr 2026 18:18:56 +0530
    Last State:     Terminated
      Reason:       OOMKilled
      Exit Code:    137
      Started:      Thu, 02 Apr 2026 16:51:30 +0530
      Finished:     Thu, 02 Apr 2026 18:18:55 +0530
    Ready:          True
    Restart Count:  1
    Limits:
      cpu:     1
      memory:  1Gi
    Requests:
      cpu:        250m
      memory:     512Mi
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
  Ready                       True
  ContainersReady             True
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
  Type     Reason     Age                  From     Message
  ----     ------     ----                 ----     -------
  Normal   Pulled     2m31s (x2 over 89m)  kubelet  Container image "h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4" already present on machine
  Normal   Created    2m31s (x2 over 89m)  kubelet  Created container: loki
  Normal   Started    2m31s (x2 over 89m)  kubelet  Started container loki
  Warning  Unhealthy  2m17s (x4 over 89m)  kubelet  Startup probe failed: HTTP probe failed with statuscode: 503
