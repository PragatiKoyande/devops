
D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pod loki-6d6c946fb5-8vvld  -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-6d6c946fb5-8vvld
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b/10.244.5.99
Start Time:       Thu, 02 Apr 2026 18:47:42 +0530
Labels:           app=loki
                  pod-template-hash=6d6c946fb5
Annotations:      <none>
Status:           Running
IP:               192.168.2.183
IPs:
  IP:           192.168.2.183
Controlled By:  ReplicaSet/loki-6d6c946fb5
Containers:
  loki:
    Container ID:  containerd://be4ed291157b69125ffafa987791116fc9c9133d07adedc163fc19be89c4062f
    Image:         h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
    Image ID:      h06vksharbor.corp.ad.sbi/cbops/grafana/loki@sha256:4a825ed37cf574f9cfeda62bd50c00fa1020b0aca8202aaa42cd0c0e5bfe0f63
    Port:          3100/TCP
    Host Port:     0/TCP
    Args:
      -config.file=/etc/loki/loki.yaml
    State:          Running
      Started:      Fri, 03 Apr 2026 10:44:37 +0530
    Last State:     Terminated
      Reason:       OOMKilled
      Exit Code:    137
      Started:      Thu, 02 Apr 2026 18:47:47 +0530
      Finished:     Fri, 03 Apr 2026 10:44:36 +0530
    Ready:          False
    Restart Count:  1
    Limits:
      cpu:     1
      memory:  3Gi
    Requests:
      cpu:        250m
      memory:     1Gi
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
  Type     Reason     Age                From     Message
  ----     ------     ----               ----     -------
  Normal   Pulled     56s (x2 over 15h)  kubelet  Container image "h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4" already present on machine
  Normal   Created    56s (x2 over 15h)  kubelet  Created container: loki
  Normal   Started    56s (x2 over 15h)  kubelet  Started container loki
  Warning  Unhealthy  56s                kubelet  Liveness probe failed: Get "http://192.168.2.183:3100/ready": dial tcp 192.168.2.183:3100: connect: connection refused
  Warning  Unhealthy  56s                kubelet  Readiness probe failed: Get "http://192.168.2.183:3100/ready": dial tcp 192.168.2.183:3100: connect: connection refused
  Warning  Unhealthy  36s (x4 over 15h)  kubelet  Startup probe failed: HTTP probe failed with statuscode: 503
