D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pod loki-7974ccfdd5-c5mxr  -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-7974ccfdd5-c5mxr
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             <none>
Labels:           app=loki
                  pod-template-hash=7974ccfdd5
Annotations:      <none>
Status:           Pending
IP:
IPs:              <none>
Controlled By:    ReplicaSet/loki-7974ccfdd5
Containers:
  loki:
    Image:      h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
    Port:       3100/TCP
    Host Port:  0/TCP
    Args:
      -config.file=/etc/loki/loki.yaml
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
  Type           Status
  PodScheduled   False
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
  Type     Reason            Age                From               Message
  ----     ------            ----               ----               -------
  Warning  FailedScheduling  64s                default-scheduler  0/6 nodes are available: pod has unbound immediate PersistentVolumeClaims. preemption: 0/6 nodes are available: 6 Preemption is not helpful for scheduling.
  Warning  FailedScheduling  60s (x2 over 62s)  default-scheduler  0/6 nodes are available: pod has unbound immediate PersistentVolumeClaims. preemption: 0/6 nodes are available: 6 Preemption is not helpful for scheduling.
