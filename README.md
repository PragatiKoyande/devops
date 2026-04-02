D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pod loki-7dd69f7fc5-wshg5  -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-7dd69f7fc5-wshg5
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b/10.244.5.99
Start Time:       Thu, 02 Apr 2026 18:38:10 +0530
Labels:           app=loki
                  pod-template-hash=7dd69f7fc5
Annotations:      <none>
Status:           Running
IP:               192.168.2.182
IPs:
  IP:           192.168.2.182
Controlled By:  ReplicaSet/loki-7dd69f7fc5
Containers:
  loki:
    Container ID:  containerd://f2b146ca5feba6573acf23b4f1f33e0b6d6abb7554ff383992270be43264af48
    Image:         h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
    Image ID:      h06vksharbor.corp.ad.sbi/cbops/grafana/loki@sha256:4a825ed37cf574f9cfeda62bd50c00fa1020b0aca8202aaa42cd0c0e5bfe0f63
    Port:          3100/TCP
    Host Port:     0/TCP
    Args:
      -config.file=/etc/loki/loki.yaml
    State:          Running
      Started:      Thu, 02 Apr 2026 18:38:15 +0530
    Ready:          True
    Restart Count:  0
    Limits:
      cpu:     1
      memory:  3Gi
    Requests:
      cpu:        250m
      memory:     1Gi
    Liveness:     http-get http://:3100/ready delay=90s timeout=1s period=15s #success=1 #failure=3
    Readiness:    http-get http://:3100/ready delay=30s timeout=1s period=10s #success=1 #failure=3
    Startup:      http-get http://:3100/ready delay=0s timeout=1s period=10s #success=1 #failure=60
    Environment:  <none>
    Mounts:
      /etc/loki from config (ro)
      /tmp from tmp (rw)
      /var/loki from storage (rw)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       True
  ContainersReady             True
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
  Type     Reason                  Age                   From                     Message
  ----     ------                  ----                  ----                     -------
  Warning  FailedScheduling        3m30s                 default-scheduler        0/6 nodes are available: pod has unbound immediate PersistentVolumeClaims. preemption: 0/6 nodes are available: 6 Preemption is not helpful for scheduling.
  Warning  FailedScheduling        3m28s                 default-scheduler        0/6 nodes are available: pod has unbound immediate PersistentVolumeClaims. preemption: 0/6 nodes are available: 6 Preemption is not helpful for scheduling.
  Normal   Scheduled               3m26s                 default-scheduler        Successfully assigned logging/loki-7dd69f7fc5-wshg5 to h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b
  Normal   SuccessfulAttachVolume  3m25s                 attachdetach-controller  AttachVolume.Attach succeeded for volume "pvc-64417e3b-2fd3-4295-84ef-414a12cf9486"
  Normal   Pulled                  3m21s                 kubelet                  Container image "h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4" already present on machine
  Normal   Created                 3m21s                 kubelet                  Created container: loki
  Normal   Started                 3m21s                 kubelet                  Started container loki
  Warning  Unhealthy               3m1s (x2 over 3m11s)  kubelet                  Startup probe failed: HTTP probe failed with statuscode: 503

  probe realted issue:

  ---
# ================================
# Deployment
# ================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: loki
  namespace: logging
spec:
  replicas: 1
  strategy:
    type: Recreate  
  revisionHistoryLimit: 1

  selector:
    matchLabels:
      app: loki

  template:
    metadata:
      labels:
        app: loki

    spec:
      serviceAccountName: loki-sa
      terminationGracePeriodSeconds: 60

      securityContext:
        fsGroup: 10001

      containers:
        - name: loki
          image: h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
          args:
            - -config.file=/etc/loki/loki.yaml

          ports:
            - containerPort: 3100

          resources:
            requests:
              cpu: "250m"
              memory: "1Gi"
            limits:
              cpu: "1"
              memory: "3Gi"

          readinessProbe:
            httpGet:
              path: /ready
              port: 3100
            initialDelaySeconds: 30
            periodSeconds: 10

          livenessProbe:
            httpGet:
              path: /ready
              port: 3100
            initialDelaySeconds: 90
            periodSeconds: 15

          startupProbe:
            httpGet:
              path: /ready
              port: 3100
            failureThreshold: 60
            periodSeconds: 10

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 20"]

          securityContext:
            allowPrivilegeEscalation: false
            capabilities:
              drop:
                - ALL

          volumeMounts:
            - name: config
              mountPath: /etc/loki
              readOnly: true
            - name: storage
              mountPath: /var/loki
            - name: tmp
              mountPath: /tmp   

      volumes:
        - name: config
          configMap:
            name: loki-config
        - name: storage
          persistentVolumeClaim:
            claimName: loki-pvc
        - name: tmp
          emptyDir: {}


          my manifest for probe
