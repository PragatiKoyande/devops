D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pod loki-6d6c946fb5-8vvld -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-6d6c946fb5-8vvld
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-vzw4b/10.244.5.99
Start Time:       Thu, 02 Apr 2026 18:47:42 +0530
Labels:           app=loki
                  pod-template-hash=6d6c946fb5
Annotations:      <none>
Status:           Running
IP:               192.168.2.183
IPs:
  IP:           192.168.2.183
Controlled By:  ReplicaSet/loki-6d6c946fb5
Containers:
  loki:
    Container ID:  containerd://ada3c22005534592f2edf5fe54116b875f03f0ecb1e3735047b75753627c562b
    Image:         h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
    Image ID:      h06vksharbor.corp.ad.sbi/cbops/grafana/loki@sha256:4a825ed37cf574f9cfeda62bd50c00fa1020b0aca8202aaa42cd0c0e5bfe0f63
    Port:          3100/TCP
    Host Port:     0/TCP
    Args:
      -config.file=/etc/loki/loki.yaml
    State:          Running
      Started:      Fri, 03 Apr 2026 13:49:15 +0530
    Last State:     Terminated
      Reason:       OOMKilled
      Exit Code:    137
      Started:      Fri, 03 Apr 2026 10:44:37 +0530
      Finished:     Fri, 03 Apr 2026 13:49:14 +0530
    Ready:          True
    Restart Count:  2
    Limits:
      cpu:     1
      memory:  3Gi
    Requests:
      cpu:        250m
      memory:     1Gi
    Liveness:     http-get http://:3100/ready delay=180s timeout=2s period=10s #success=1 #failure=3
    Readiness:    http-get http://:3100/ready delay=60s timeout=2s period=10s #success=1 #failure=3
    Startup:      http-get http://:3100/ready delay=0s timeout=2s period=10s #success=1 #failure=120
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
  Type     Reason     Age                From     Message
  ----     ------     ----               ----     -------
  Normal   Pulled     47m (x3 over 19h)  kubelet  Container image "h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4" already present on machine
  Normal   Created    47m (x3 over 19h)  kubelet  Created container: loki
  Normal   Started    47m (x3 over 19h)  kubelet  Started container loki
  Warning  Unhealthy  47m (x6 over 19h)  kubelet  Startup probe failed: HTTP probe failed with statuscode: 503


  I am getting this issue my loki is failing automatically and below I have pasted the loki configuration file:
  # ================================
# Loki ConfigMap 
# ================================
apiVersion: v1
kind: ConfigMap
metadata:
  name: loki-config
  namespace: logging
  annotations:
    description: "Loki production configuration"
  labels:
    app: loki
immutable: true

data:
  loki.yaml: |
    auth_enabled: false

    server:
      http_listen_port: 3100
      graceful_shutdown_timeout: 60s
      http_server_read_timeout: 30s
      http_server_write_timeout: 30s
      http_server_idle_timeout: 120s

    common:
      path_prefix: /var/loki
      replication_factor: 1
      ring:
        kvstore:
          store: inmemory

    schema_config:
      configs:
        - from: 2024-01-01
          store: boltdb-shipper
          object_store: filesystem
          schema: v13   
          index:
            prefix: index_
            period: 24h

    storage_config:
      boltdb_shipper:
        active_index_directory: /var/loki/index
        cache_location: /var/loki/index_cache
        shared_store: filesystem

      filesystem:
        directory: /var/loki/chunks

    limits_config:
      retention_period: 168h
      ingestion_rate_mb: 4
      ingestion_burst_size_mb: 8
      max_streams_per_user: 5000
      max_query_parallelism: 4
      max_query_series: 20000

    chunk_store_config:
      max_look_back_period: 720h

    compactor:
      working_directory: /var/loki/compactor
      shared_store: filesystem
      retention_enabled: false

    table_manager:
      retention_deletes_enabled: true
      retention_period: 168h

    ingester:
      chunk_idle_period: 5m
      chunk_retain_period: 30s
      chunk_target_size: 1048576
      wal:
        enabled: false
        dir: /var/loki/wal

    query_range:
      align_queries_with_step: true
      max_retries: 5

    frontend:
      log_queries_longer_than: 5s

---

# ================================
# Persistent Volume Claim
# ================================
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: loki-pvc
  namespace: logging
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: h06-vks-sp-6
  resources:
    requests:
      storage: 50Gi

---
# ================================
# Service Account
# ================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: loki-sa
  namespace: logging
automountServiceAccountToken: false

---
# ================================
# Pod Disruption Budget
# ================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: loki-pdb
  namespace: logging
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: loki

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
            initialDelaySeconds: 60
            periodSeconds: 10
            timeoutSeconds: 2

          livenessProbe:
            httpGet:
              path: /ready
              port: 3100
            initialDelaySeconds: 180
            periodSeconds: 10
            timeoutSeconds: 2

          startupProbe:
            httpGet:
              path: /ready
              port: 3100
            failureThreshold: 120
            periodSeconds: 10
            timeoutSeconds: 2

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

---
# ================================
# Service
# ================================
apiVersion: v1
kind: Service
metadata:
  name: loki
  namespace: logging
spec:
  type: ClusterIP
  selector:
    app: loki
  ports:
    - name: http
      port: 3100
      targetPort: 3100
      protocol: TCP

      Please give me suggestion 
