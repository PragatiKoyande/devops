[root@fcsitgateway SIT-Microservice]# kubectl describe daemonset fluent-bit -n logging --kubeconfig h06vkssitcbopscls.conf
Name:           fluent-bit
Selector:       app=fluent-bit
Node-Selector:  <none>
Labels:         <none>
Annotations:    deprecated.daemonset.template.generation: 32
Desired Number of Nodes Scheduled: 3
Current Number of Nodes Scheduled: 3
Number of Nodes Scheduled with Up-to-date Pods: 3
Number of Nodes Scheduled with Available Pods: 3
Number of Nodes Misscheduled: 0
Pods Status:  3 Running / 0 Waiting / 0 Succeeded / 0 Failed
Pod Template:
  Labels:           app=fluent-bit
  Annotations:      kubectl.kubernetes.io/restartedAt: 2026-02-17T15:30:46+05:30
  Service Account:  fluent-bit
  Containers:
   fluent-bit:
    Image:        h06vksharbor.corp.ad.sbi/cbops/fluent-bit-2.2.2
    Port:         <none>
    Host Port:    <none>
    Environment:  <none>
    Mounts:
      /fluent-bit/etc from config (rw)
      /var/log from varlog (rw)
  Volumes:
   varlog:
    Type:          HostPath (bare host directory volume)
    Path:          /var/log
    HostPathType:
   config:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      fluent-bit-config
    Optional:  false
Events:        <none>
[root@fcsitgateway SIT-Microservice]# kubectl describe daemonset fluent-bit -n logging --kubeconfig h06vkssitcbopscls.conf
Name:           fluent-bit
Selector:       app=fluent-bit
Node-Selector:  <none>
Labels:         <none>
Annotations:    deprecated.daemonset.template.generation: 32
Desired Number of Nodes Scheduled: 3
Current Number of Nodes Scheduled: 3
Number of Nodes Scheduled with Up-to-date Pods: 3
Number of Nodes Scheduled with Available Pods: 3
Number of Nodes Misscheduled: 0
Pods Status:  3 Running / 0 Waiting / 0 Succeeded / 0 Failed
Pod Template:
  Labels:           app=fluent-bit
  Annotations:      kubectl.kubernetes.io/restartedAt: 2026-02-17T15:30:46+05:30
  Service Account:  fluent-bit
  Containers:
   fluent-bit:
    Image:        h06vksharbor.corp.ad.sbi/cbops/fluent-bit-2.2.2
    Port:         <none>
    Host Port:    <none>
    Environment:  <none>
    Mounts:
      /fluent-bit/etc from config (rw)
      /var/log from varlog (rw)
  Volumes:
   varlog:
    Type:          HostPath (bare host directory volume)
    Path:          /var/log
    HostPathType:
   config:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      fluent-bit-config
    Optional:  false
Events:        <none>
