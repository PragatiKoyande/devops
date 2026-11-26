[root@fcppjump ~]# k describe deployment notification-deployment
Name:                   notification-deployment
Namespace:              backend
CreationTimestamp:      Tue, 18 Aug 2026 16:46:12 +0530
Labels:                 <none>
Annotations:            deployment.kubernetes.io/revision: 5
Selector:               app=notification-backend
Replicas:               1 desired | 1 updated | 1 total | 0 available | 1 unavailable
StrategyType:           RollingUpdate
MinReadySeconds:        0
RollingUpdateStrategy:  25% max unavailable, 25% max surge
Pod Template:
  Labels:       app=notification-backend
  Annotations:  kubectl.kubernetes.io/restartedAt: 2026-11-26T12:08:50+05:30
  Containers:
   notification-container:
    Image:      h06vksharbor.corp.ad.sbi/cbops/notification-service:preprod-01
    Port:       9010/TCP
    Host Port:  0/TCP
    Environment Variables from:
      config-postgres     ConfigMap  Optional: false
      config-redis        ConfigMap  Optional: false
      config-kafka        ConfigMap  Optional: false
      kafka-aes-secret    Secret     Optional: false
      rsa-private-secret  Secret     Optional: false
      rsa-public-secret   Secret     Optional: false
      jwt-secret          Secret     Optional: false
      secret-postgres     Secret     Optional: false
    Environment:
      SPRING_PROFILES_ACTIVE:                   preprod
      SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET:  earliest
      SPRING_KAFKA_CONSUMER_GROUP_ID:           notification-service-group
    Mounts:                                     <none>
  Volumes:                                      <none>
  Node-Selectors:                               <none>
  Tolerations:                                  <none>
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Progressing    True    NewReplicaSetAvailable
  Available      False   MinimumReplicasUnavailable
OldReplicaSets:  notification-deployment-5f99884c7b (0/0 replicas created), notification-deployment-6c665dd8fb (0/0 replicas created), notification-deployment-b9696757b (0/0 replicas created), notification-deployment-5d5b8c6cdc (0/0 replicas created)
NewReplicaSet:   notification-deployment-77679b5746 (1/1 replicas created)
Events:          <none>
