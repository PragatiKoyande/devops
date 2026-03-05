D:\Pragati\PROD-Deployment-Test>kubectl describe pod common-request-deployment-78679cbdb-4c8dq  -n backend --kubeconfig h06vksuatcbopscls.conf
Name:             common-request-deployment-78679cbdb-4c8dq
Namespace:        backend
Priority:         0
Service Account:  common-request-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b/10.244.5.99
Start Time:       Thu, 05 Mar 2026 14:20:17 +0530
Labels:           app=common-request-backend
                  pod-template-hash=78679cbdb
Annotations:      <none>
Status:           Running
IP:               192.168.2.195
IPs:
  IP:           192.168.2.195
Controlled By:  ReplicaSet/common-request-deployment-78679cbdb
Containers:
  common-request-container:
    Container ID:   containerd://5f82df6e710b2306eddd8b3180d956cb2d67b697ee602c92df22c66a2a548b8a
    Image:          h06vksharbor.corp.ad.sbi/cbops/common-request-service:DEV08
    Image ID:       h06vksharbor.corp.ad.sbi/cbops/common-request-service@sha256:9b6ebb9cce172fb8e9ac61f5001c058cb1b5e4e0b7f1cf31f05259b461a23e37
    Port:           9000/TCP
    Host Port:      0/TCP
    State:          Waiting
      Reason:       CrashLoopBackOff
    Last State:     Terminated
      Reason:       Error
      Exit Code:    1
      Started:      Thu, 05 Mar 2026 14:26:28 +0530
      Finished:     Thu, 05 Mar 2026 14:27:51 +0530
    Ready:          False
    Restart Count:  4
    Limits:
      cpu:     500m
      memory:  512Mi
    Requests:
      cpu:      200m
      memory:   256Mi
    Liveness:   http-get http://:9000/actuator/health delay=30s timeout=1s period=20s #success=1 #failure=5
    Readiness:  http-get http://:9000/actuator/health delay=15s timeout=1s period=10s #success=1 #failure=5
    Startup:    http-get http://:9000/actuator/health delay=0s timeout=1s period=10s #success=1 #failure=30
    Environment:
      SPRING_DATA_REDIS_HOST:         redis-service
      SPRING_DATA_REDIS_PORT:         6379
      SPRING_DATA_REDIS_CLIENT_TYPE:  lettuce
    Mounts:                           <none>
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       False
  ContainersReady             False
  PodScheduled                True
Volumes:                      <none>
QoS Class:                    Burstable
Node-Selectors:               <none>
Tolerations:                  node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                              node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Topology Spread Constraints:  kubernetes.io/hostname:ScheduleAnyway when max skew 1 is exceeded for selector app=common-request-backend
Events:
  Type     Reason     Age                     From               Message
  ----     ------     ----                    ----               -------
  Normal   Scheduled  8m3s                    default-scheduler  Successfully assigned backend/common-request-deployment-78679cbdb-4c8dq to h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b
  Normal   Pulled     8m3s                    kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/common-request-service:DEV08" in 814ms (814ms including waiting). Image size: 235798870 bytes.
  Normal   Pulled     6m39s                   kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/common-request-service:DEV08" in 492ms (492ms including waiting). Image size: 235798870 bytes.
  Warning  BackOff    5m13s                   kubelet            Back-off restarting failed container common-request-container in pod common-request-deployment-78679cbdb-4c8dq_backend(127261cb-1960-4ea7-bea0-b50fcb281d62)
  Normal   Pulled     5m3s                    kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/common-request-service:DEV08" in 874ms (874ms including waiting). Image size: 235798870 bytes.
  Normal   Pulled     3m8s                    kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/common-request-service:DEV08" in 550ms (550ms including waiting). Image size: 235798870 bytes.
  Warning  Unhealthy  2m44s (x28 over 7m54s)  kubelet            Startup probe failed: Get "http://192.168.2.195:9000/actuator/health": dial tcp 192.168.2.195:9000: connect: connection refused
  Normal   Killing    2m24s                   kubelet            Container common-request-container failed startup probe, will be restarted
  Normal   Pulling    114s (x5 over 8m4s)     kubelet            Pulling image "h06vksharbor.corp.ad.sbi/cbops/common-request-service:DEV08"
  Normal   Created    113s (x5 over 8m3s)     kubelet            Created container: common-request-container
  Normal   Started    113s (x5 over 8m3s)     kubelet            Started container common-request-container
  Normal   Pulled     113s                    kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/common-request-service:DEV08" in 806ms (806ms including waiting). Image size: 23579887
