E:\Tushar Khade\Projects-CR-Document\Finanace-One\DEV-Deployment\Network-Policy>k describe pod notification-deployment-6d559c9f67-bp4tz -n backend
Name:             notification-deployment-6d559c9f67-bp4tz
Namespace:        backend
Priority:         0
Service Account:  default
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-smcqf-67hcr/10.244.5.109
Start Time:       Wed, 05 Aug 2026 14:45:04 +0530
Labels:           app=notification-backend
                  pod-template-hash=6d559c9f67
Annotations:      kubectl.kubernetes.io/restartedAt: 2026-08-05T14:45:04+05:30
                  nodeportlocal.antrea.io: [{"podPort":9010,"nodeIP":"10.244.5.109","nodePort":61076,"protocol":"tcp"}]
Status:           Running
IP:               192.168.2.102
IPs:
  IP:           192.168.2.102
Controlled By:  ReplicaSet/notification-deployment-6d559c9f67
Containers:
  notification-container:
    Container ID:   containerd://ab3fb6bc98a498374fbdf3d7cc6fa02c70ad13f1359a3c52375b91b8f124fbdd
    Image:          h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01
    Image ID:       h06vksharbor.corp.ad.sbi/cbops/notification-service@sha256:6f33fd408eab8fb1c7cd93f2d6a127983b6f2cfdbb800516e7d32e6cc0ee007d
    Port:           9010/TCP
    Host Port:      0/TCP
    State:          Waiting
      Reason:       CrashLoopBackOff
    Last State:     Terminated
      Reason:       Error
      Exit Code:    1
      Started:      Wed, 05 Aug 2026 14:48:38 +0530
      Finished:     Wed, 05 Aug 2026 14:48:45 +0530
    Ready:          False
    Restart Count:  5
    Environment Variables from:
      config-redis     ConfigMap  Optional: false
      config-postgres  ConfigMap  Optional: false
      kafka-config     ConfigMap  Optional: false
    Environment:
      SPRING_KAFKA_CONSUMER_GROUP_ID:           notification-service-group
      SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET:  earliest
      SPRING_DATA_REDIS_CLIENT_TYPE:            lettuce
      JWT_SECRET:                               <set to the key 'JWT_SECRET' in secret 'jwt-secret'>                            Optional: false
      PSQL_SPRING_DATASOURCE_PASSWORD:          <set to the key 'PSQL_SPRING_DATASOURCE_PASSWORD' in secret 'secret-postgres'>  Optional: false
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-jtmjz (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       False
  ContainersReady             False
  PodScheduled                True
Volumes:
  kube-api-access-jtmjz:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason     Age                  From               Message
  ----     ------     ----                 ----               -------
  Normal   Scheduled  4m4s                 default-scheduler  Successfully assigned backend/notification-deployment-6d559c9f67-bp4tz to h06vksuatcbopscls-node-pool-1-xg7gx-smcqf-67hcr
  Normal   Pulled     4m3s                 kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01" in 173ms (173ms including waiting). Image size: 271462999 bytes.
  Normal   Pulled     3m55s                kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01" in 108ms (108ms including waiting). Image size: 271462999 bytes.
  Normal   Pulled     3m35s                kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01" in 105ms (105ms including waiting). Image size: 271462999 bytes.
  Normal   Pulled     2m58s                kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01" in 111ms (111ms including waiting). Image size: 271462999 bytes.
  Normal   Pulled     119s                 kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01" in 191ms (191ms including waiting). Image size: 271462999 bytes.
  Normal   Pulling    30s (x6 over 4m3s)   kubelet            Pulling image "h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01"
  Normal   Created    30s (x6 over 4m3s)   kubelet            Created container: notification-container
  Normal   Started    30s (x6 over 4m3s)   kubelet            Started container notification-container
  Normal   Pulled     30s                  kubelet            Successfully pulled image "h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01" in 106ms (106ms including waiting). Image size: 271462999 bytes.
  Warning  BackOff    9s (x15 over 3m47s)  kubelet            Back-off restarting failed container notification-container in pod notification-deployment-6d559c9f67-bp4tz_backend(7312ed26-8a46-48c6-8d9b-3448ddca8225)
