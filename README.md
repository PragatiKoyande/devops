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
      retention_period: 720h
      ingestion_rate_mb: 8
      ingestion_burst_size_mb: 16
      max_streams_per_user: 10000
      max_query_parallelism: 16
      max_query_series: 100000

    chunk_store_config:
      max_look_back_period: 720h

    compactor:
      working_directory: /var/loki/compactor
      shared_store: filesystem
      retention_enabled: true

    table_manager:
      retention_deletes_enabled: true
      retention_period: 720h

    ingester:
      chunk_idle_period: 5m
      chunk_retain_period: 30s
      chunk_target_size: 1048576
      wal:
        enabled: true
        dir: /var/loki/wal

    query_range:
      align_queries_with_step: true
      max_retries: 5

    frontend:
      log_queries_longer_than: 5s

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
              memory: "512Mi"
            limits:
              cpu: "1"
              memory: "1Gi"

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
            readOnlyRootFilesystem: true
            capabilities:
              drop:
                - ALL

          volumeMounts:
            - name: config
              mountPath: /etc/loki
              readOnly: true
            - name: storage
              mountPath: /var/loki

      volumes:
        - name: config
          configMap:
            name: loki-config
        - name: storage
          persistentVolumeClaim:
            claimName: loki-pvc

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

---
# ================================
# Network Policy
# ================================
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: loki-network-policy
  namespace: logging
spec:
  podSelector:
    matchLabels:
      app: loki

  policyTypes:
    - Ingress
    - Egress

  ingress:
    - from:
        - namespaceSelector: {}
      ports:
        - protocol: TCP
          port: 3100

  egress:
    - to:
        - namespaceSelector: {}

These are my loki configuartion file
