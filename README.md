[root@fcuatgateway UAT-Grafana]# kubectl get pvc -n logging  --kubeconfig h06vksuat1cbopscls.conf
NAME       STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
loki-pvc   Bound    pvc-6aa64fbe-2b91-4449-b42b-24c678536551   5Gi        RWO            h06-vks-sp-5   <unset>                 11d
[root@fcuatgateway UAT-Grafana]# kubectl describe pod loki-58595d499c-f4bx5  -n logging  --kubeconfig h06vksuat1cbopscls.conf
Name:             loki-58595d499c-f4bx5
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuat1cbopscls-node-pool-1-8qvhf-tvgr4-djgd9/10.244.7.180
Start Time:       Wed, 11 Mar 2026 12:06:18 +0530
Labels:           app=loki
                  pod-template-hash=58595d499c
Annotations:      <none>
Status:           Running
IP:               192.168.1.82
IPs:
  IP:           192.168.1.82
Controlled By:  ReplicaSet/loki-58595d499c
Containers:
  loki:
    Container ID:  containerd://e72e1f2d6bdf866eda817e09dc836fd5529cc88e610eb339304ff07429bf46ce
    Image:         h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
    Image ID:      h06vksharbor.corp.ad.sbi/cbops/grafana/loki@sha256:4a825ed37cf574f9cfeda62bd50c00fa1020b0aca8202aaa42cd0c0e5bfe0f63
    Port:          3100/TCP
    Host Port:     0/TCP
    Args:
      -config.file=/etc/loki/loki.yaml
    State:          Waiting
      Reason:       CrashLoopBackOff
    Last State:     Terminated
      Reason:       Error
      Exit Code:    2
      Started:      Wed, 11 Mar 2026 12:12:25 +0530
      Finished:     Wed, 11 Mar 2026 12:12:25 +0530
    Ready:          False
    Restart Count:  6
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
    Type:                     PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName:                loki-pvc
    ReadOnly:                 false
QoS Class:                    Burstable
Node-Selectors:               <none>
Tolerations:                  node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                              node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Topology Spread Constraints:  kubernetes.io/hostname:ScheduleAnyway when max skew 1 is exceeded for selector app=loki
Events:
  Type     Reason                  Age                   From                     Message
  ----     ------                  ----                  ----                     -------
  Normal   Scheduled               6m39s                 default-scheduler        Successfully assigned logging/loki-58595d499c-f4bx5 to h06vksuat1cbopscls-node-pool-1-8qvhf-tvgr4-djgd9
  Normal   SuccessfulAttachVolume  6m28s                 attachdetach-controller  AttachVolume.Attach succeeded for volume "pvc-6aa64fbe-2b91-4449-b42b-24c678536551"
  Warning  BackOff                 82s (x32 over 6m26s)  kubelet                  spec.containers{loki}: Back-off restarting failed container loki in pod loki-58595d499c-f4bx5_logging(d296058f-8ad0-4dc9-8323-bc8931514da3)
  Normal   Pulled                  32s (x7 over 6m28s)   kubelet                  spec.containers{loki}: Container image "h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4" already present on machine
  Normal   Created                 32s (x7 over 6m28s)   kubelet                  spec.containers{loki}: Created container: loki
  Normal   Started                 32s (x7 over 6m27s)   kubelet                  spec.containers{loki}: Started container loki
