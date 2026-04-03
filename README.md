
D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pod loki-7974ccfdd5-lgtc4 -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-7974ccfdd5-lgtc4
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
  Type     Reason            Age                    From               Message
  ----     ------            ----                   ----               -------
  Warning  FailedScheduling  2m22s                  default-scheduler  0/6 nodes are available: pod has unbound immediate PersistentVolumeClaims. preemption: 0/6 nodes are available: 6 Preemption is not helpful for scheduling.
  Warning  FailedScheduling  2m18s (x2 over 2m21s)  default-scheduler  0/6 nodes are available: pod has unbound immediate PersistentVolumeClaims. preemption: 0/6 nodes are available: 6 Preemption is not helpful for scheduling.

D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl get sc -n logging --kubeconfig h06vksuatcbopscls.conf
NAME                       PROVISIONER              RECLAIMPOLICY   VOLUMEBINDINGMODE      ALLOWVOLUMEEXPANSION   AGE
h06-vks-sp-3 (default)     csi.vsphere.vmware.com   Delete          Immediate              true                   257d
h06-vks-sp-3-latebinding   csi.vsphere.vmware.com   Delete          WaitForFirstConsumer   true                   257d
h06-vks-sp-6               csi.vsphere.vmware.com   Delete          Immediate              true                   175d
h06-vks-sp-6-latebinding   csi.vsphere.vmware.com   Delete          WaitForFirstConsumer   true                   175d

D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl get pods -n logging --kubeconfig h06vksuatcbopscls.conf
NAME                    READY   STATUS    RESTARTS   AGE
loki-7974ccfdd5-lgtc4   0/1     Pending   0          3m6s

D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl get pods -n logging --kubeconfig h06vksuatcbopscls.conf
NAME                    READY   STATUS    RESTARTS   AGE
loki-7974ccfdd5-lgtc4   0/1     Pending   0          4m52s

D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pvc loki-pvc -n logging --kubeconfig h06vksuatcbopscls.conf
Name:          loki-pvc
Namespace:     logging
StorageClass:  h06-vks-sp-6
Status:        Bound
Volume:        pvc-6aa541cb-6609-4b30-ac09-ca788ffcc527
Labels:        <none>
Annotations:   pv.kubernetes.io/bind-completed: yes
               pv.kubernetes.io/bound-by-controller: yes
               volume.beta.kubernetes.io/storage-provisioner: csi.vsphere.vmware.com
               volume.kubernetes.io/storage-provisioner: csi.vsphere.vmware.com
               volumehealth.storage.kubernetes.io/health: accessible
               volumehealth.storage.kubernetes.io/health-timestamp: Fri Apr  3 09:32:36 UTC 2026
Finalizers:    [kubernetes.io/pvc-protection]
Capacity:      50Gi
Access Modes:  RWO
VolumeMode:    Filesystem
Used By:       loki-7974ccfdd5-lgtc4
Events:
  Type    Reason                 Age    From                                                                                                 Message
  ----    ------                 ----   ----                                                                                                 -------
  Normal  ExternalProvisioning   8m20s  persistentvolume-controller                                                                          Waiting for a volume to be created either by the external provisioner 'csi.vsphere.vmware.com' or manually by the system administrator. If volume creation is delayed, please verify that the provisioner is running and correctly registered.
  Normal  Provisioning           8m20s  csi.vsphere.vmware.com_vsphere-csi-controller-78b766d779-gttfr_af8ce061-ba45-4dcd-9b37-5997e132026e  External provisioner is provisioning volume for claim "logging/loki-pvc"
  Normal  ProvisioningSucceeded  8m18s  csi.vsphere.vmware.com_vsphere-csi-controller-78b766d779-gttfr_af8ce061-ba45-4dcd-9b37-5997e132026e  Successfully provisioned volume pvc-6aa541cb-6609-4b30-ac09-ca788ffcc527
