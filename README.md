D:\pragati\HELM_LATEST_26082026>k get deployment
NAME                         READY   UP-TO-DATE   AVAILABLE   AGE
common-master-deployment     1/1     1            1           67d
common-request-deployment    1/1     1            1           67d
communication-deployment     1/1     1            1           21d
dashboard-deployment         1/1     1            1           67d
debezium-server              0/1     1            0           67d
enquiry-deployment           1/1     1            1           67d
login-deployment             1/1     1            1           22d
process-status-deployment    1/1     1            1           66d
redis-deployment             1/1     1            1           63d
report-deployment            1/1     1            1           66d
template-config-deployment   1/1     1            1           66d
transactions-deployment      1/1     1            1           66d
user-deployment              1/1     1            1           63d
voucher-deployment           1/1     1            1           66d
voucher-enquiry-deployment   1/1     1            1           66d

D:\pragati\HELM_LATEST_26082026>k describe deployment debezium-server
Name:                   debezium-server
Namespace:              backend
CreationTimestamp:      Thu, 17 Sep 2026 13:53:08 +0530
Labels:                 <none>
Annotations:            deployment.kubernetes.io/revision: 2
Selector:               app=debezium-server
Replicas:               1 desired | 1 updated | 1 total | 0 available | 1 unavailable
StrategyType:           RollingUpdate
MinReadySeconds:        0
RollingUpdateStrategy:  25% max unavailable, 25% max surge
Pod Template:
  Labels:       app=debezium-server
  Annotations:  kubectl.kubernetes.io/restartedAt: 2026-09-17T15:46:30+05:30
  Containers:
   debezium-server:
    Image:      h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1
    Port:       8080/TCP
    Host Port:  0/TCP
    Limits:
      cpu:     2
      memory:  3Gi
    Requests:
      cpu:     500m
      memory:  1Gi
    Environment:
      JAVA_OPTS:  -Xms512m -Xmx2g
    Mounts:
      /debezium/conf from config-volume (rw)
      /debezium/data from data-volume (rw)
  Volumes:
   config-volume:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      debezium-server-config
    Optional:  false
   data-volume:
    Type:          PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
    ClaimName:     debezium-pvc
    ReadOnly:      false
  Node-Selectors:  <none>
  Tolerations:     <none>
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Progressing    True    NewReplicaSetAvailable
  Available      False   MinimumReplicasUnavailable
OldReplicaSets:  debezium-server-86c8fbbbcb (0/0 replicas created)
NewReplicaSet:   debezium-server-f5c5498d (1/1 replicas created)
Events:          <none>
