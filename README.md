[root@fcuatgateway UAT-Grafana]# kubectl describe pod grafana-965694fdf-mx49c -n uat-cbops1 --kubeconfig h06vksuat1cbopscls.conf
Name:             grafana-965694fdf-mx49c
Namespace:        uat-cbops1
Priority:         0
Service Account:  default
Node:             <none>
Labels:           app=grafana
                  pod-template-hash=965694fdf
Annotations:      <none>
Status:           Pending
SeccompProfile:   RuntimeDefault
IP:
IPs:              <none>
Controlled By:    ReplicaSet/grafana-965694fdf
Containers:
  grafana:
    Image:      h06vksharbor.corp.ad.sbi/cbops/grafana/grafana:10.2.3
    Port:       3000/TCP
    Host Port:  0/TCP
    Limits:
      cpu:     1
      memory:  1Gi
    Requests:
      cpu:      200m
      memory:   512Mi
    Liveness:   http-get http://:3000/grafana/api/health delay=60s timeout=5s period=20s #success=1 #failure=5
    Readiness:  http-get http://:3000/grafana/api/health delay=30s timeout=5s period=10s #success=1 #failure=3
    Environment:
      GF_SECURITY_ADMIN_USER:         admin
      GF_SERVER_DOMAIN:               fincoreuat.sbi
      GF_SERVER_HTTP_ADDR:            0.0.0.0
      GF_SERVER_ROOT_URL:             https://fincoreuat.sbi/grafana/
      GF_SERVER_SERVE_FROM_SUB_PATH:  true
    Mounts:
      /var/lib/grafana from grafana-storage (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-gkmm7 (ro)
Conditions:
  Type           Status
  PodScheduled   False
Volumes:
  grafana-storage:
    Type:       PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName:  grafana-pvc
    ReadOnly:   false
  kube-api-access-gkmm7:
    Type:                     Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:   3607
    ConfigMapName:            kube-root-ca.crt
    Optional:                 false
    DownwardAPI:              true
QoS Class:                    Burstable
Node-Selectors:               <none>
Tolerations:                  node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                              node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Topology Spread Constraints:  kubernetes.io/hostname:ScheduleAnyway when max skew 1 is exceeded for selector app=grafana
Events:
  Type     Reason            Age                  From               Message
  ----     ------            ----                 ----               -------
  Warning  FailedScheduling  11m                  default-scheduler  0/6 nodes are available: pod has unbound immediate PersistentVolumeClaims. preemption: 0/6 nodes are available: 6 Preemption is not helpful for scheduling.
  Warning  FailedScheduling  51s (x2 over 5m51s)  default-scheduler  0/6 nodes are available: pod has unbound immediate PersistentVolumeClaims. preemption: 0/6 nodes are available: 6 Preemption is not helpful for scheduling.
