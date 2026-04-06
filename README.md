D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe pod loki-7974ccfdd5-tvzdw -n logging --kubeconfig h06vksuatcbopscls.conf
Name:             loki-7974ccfdd5-tvzdw
Namespace:        logging
Priority:         0
Service Account:  loki-sa
Node:             h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-lxq5g/10.244.5.98
Start Time:       Mon, 06 Apr 2026 16:09:11 +0530
Labels:           app=loki
                  pod-template-hash=7974ccfdd5
Annotations:      <none>
Status:           Pending
IP:
IPs:              <none>
Controlled By:    ReplicaSet/loki-7974ccfdd5
Containers:
  loki:
    Container ID:
    Image:         h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
    Image ID:
    Port:          3100/TCP
    Host Port:     0/TCP
    Args:
      -config.file=/etc/loki/loki.yaml
    State:          Waiting
      Reason:       ContainerCreating
    Ready:          False
    Restart Count:  0
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
  Type                        Status
  PodReadyToStartContainers   False
  Initialized                 True
  Ready                       False
  ContainersReady             False
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
  Type     Reason              Age   From                     Message
  ----     ------              ----  ----                     -------
  Normal   Scheduled           41s   default-scheduler        Successfully assigned logging/loki-7974ccfdd5-tvzdw to h06vksuatcbopscls-node-pool-1-xg7gx-rrg8c-lxq5g
  Warning  FailedAttachVolume  42s   attachdetach-controller  Multi-Attach error for volume "pvc-e6c7bb00-68f9-49db-8e10-a4b8663e6bea" Volume is already used by pod(s) loki-7974ccfdd5-pgb9d, loki-7974ccfdd5-7


  again this issue coming also i m attaching my configuration  file kindly check:

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
  storageClassName: h06-vks-sp-6-latebinding
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
              memory: "2Gi"
            limits:
              cpu: "1"
              memory: "4Gi"

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
immutable: false

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
      ingestion_burst_size_mb: 6
      max_streams_per_user: 5000
      max_query_parallelism: 2
      max_query_series: 10000

    ingester:
      chunk_idle_period: 3m
      chunk_retain_period: 30s
      chunk_target_size: 1048576
      max_chunk_age: 1h
      wal:
        enabled: false
        dir: /var/loki/wal

    compactor:
      working_directory: /var/loki/compactor
      shared_store: filesystem
      retention_enabled: true

    query_range:
      align_queries_with_step: true
      max_retries: 5
      cache_results: false

    frontend:
      log_queries_longer_than: 5s
