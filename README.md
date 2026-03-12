These are my production ready file for loki deployment :
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
  storageClassName: h06-vks-sp-5
  resources:
    requests:
      storage: 5Gi
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
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

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

      # âœ… FIX ADDED: Required for PVC write permission
      securityContext:
        fsGroup: 10001

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: loki

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
            initialDelaySeconds: 10
            periodSeconds: 10
            failureThreshold: 5

          livenessProbe:
            httpGet:
              path: /ready
              port: 3100
            initialDelaySeconds: 30
            periodSeconds: 20
            failureThreshold: 5

          startupProbe:
            httpGet:
              path: /ready
              port: 3100
            failureThreshold: 30
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
    - port: 3100
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
    - ports:
        - protocol: TCP
          port: 3100

  egress:
    - to:
        - namespaceSelector: {}

        # ============================================
# ConfigMap for Loki (Enterprise Hardened)
# Aligned with secure deployment configuration
# ============================================
apiVersion: v1
kind: ConfigMap
metadata:
  name: loki-config
  namespace: logging

  # Protect ConfigMap from accidental deletion
  annotations:
    description: "Loki main configuration - production aligned"
    config.kubernetes.io/local-config: "true"

  labels:
    app: loki
    component: logging
    managed-by: kubernetes

immutable: true   # Prevent accidental runtime modification (enterprise safety)

data:
  loki.yaml: |
    # ============================================
    # Authentication
    # (unchanged as per requirement)
    # ============================================
    auth_enabled: false

    # ============================================
    # Server Configuration
    # ============================================
    server:
      http_listen_port: 3100

      # Graceful shutdown support (aligned with 60s terminationGracePeriod)
      graceful_shutdown_timeout: 60s

      # Prevent slow client abuse
      http_server_read_timeout: 30s
      http_server_write_timeout: 30s
      http_server_idle_timeout: 120s

    # ============================================
    # Common Configuration
    # ============================================
    common:
      instance_addr: 127.0.0.1
      path_prefix: /var/loki

      storage:
        filesystem:
          chunks_directory: /var/loki/chunks
          rules_directory: /var/loki/rules

      replication_factor: 1   # Unchanged (single replica deployment)

      ring:
        kvstore:
          store: inmemory     # Unchanged as required

    # ============================================
    # Schema Configuration
    # ============================================
    schema_config:
      configs:
        - from: 2024-01-01
          store: boltdb-shipper
          object_store: filesystem
          schema: v11
          index:
            prefix: index_
            period: 24h

    # ============================================
    # Limits Configuration
    # ============================================
    limits_config:
      retention_period: 168h   # 7 days (unchanged)

      # Enterprise safety controls (added)
      ingestion_rate_mb: 8
      ingestion_burst_size_mb: 16
      max_streams_per_user: 10000
      max_global_streams_per_user: 0

    # ============================================
    # Chunk Store Configuration
    # ============================================
    chunk_store_config:
      max_look_back_period: 168h

    # ============================================
    # Compactor Configuration
    # Required for boltdb-shipper in production
    # ============================================
    compactor:
      working_directory: /var/loki/boltdb-shipper-compactor
      shared_store: filesystem
      retention_enabled: true

    # ============================================
    # Table Manager (Retention Enforcement)
    # ============================================
    table_manager:
      retention_deletes_enabled: true
      retention_period: 168h

    # ============================================
    # Ingester Configuration
    # Prevent data loss on restart
    # ============================================
    ingester:
      chunk_idle_period: 5m
      chunk_retain_period: 30s
      wal:
        enabled: true
        dir: /var/loki/wal

    # ============================================
    # Query Range Optimization
    # Protect from heavy queries
    # ============================================
    query_range:
      align_queries_with_step: true
      max_retries: 5

    # ============================================
    # Frontend (Stability tuning)
    # ============================================
    frontend:
      log_queries_longer_than: 5s


      The above present files are for one env and I want to make similar on for other env so I m pasting my files which are not production ready and I want you to make these files same like production configuration so I m pasting the files below you edit and share me production ready:

      apiVersion: apps/v1
kind: Deployment
metadata:
  name: loki
  namespace: logging
spec:
  replicas: 1
  selector:
    matchLabels:
      app: loki
  template:
    metadata:
      labels:
        app: loki
    spec:
      containers:
        - name: loki
          image: h06vksharbor.corp.ad.sbi/cbops/grafana/loki:2.9.4
          args:
            - -config.file=/etc/loki/loki.yaml
          ports:
            - containerPort: 3100
          volumeMounts:
            - name: config
              mountPath: /etc/loki
            - name: storage
              mountPath: /var/loki
      volumes:
        - name: config
          configMap:
            name: loki-config
        - name: storage
          emptyDir: {}

          apiVersion: v1
kind: ConfigMap
metadata:
  name: loki-config
  namespace: logging
data:
  loki.yaml: |
    auth_enabled: false

    server:
      http_listen_port: 3100

    common:
      instance_addr: 127.0.0.1
      path_prefix: /var/loki
      storage:
        filesystem:
          chunks_directory: /var/loki/chunks
          rules_directory: /var/loki/rules
      replication_factor: 1
      ring:
        kvstore:
          store: inmemory
    schema_config:
      configs:
        - from: 2024-01-01
          store: boltdb-shipper
          object_store: filesystem
          schema: v11
          index:
            prefix: index_
            period: 24h

    limits_config:
      retention_period: 168h   # 7 days

    chunk_store_config:
      max_look_back_period: 168h

      apiVersion: v1
kind: Service
metadata:
  name: loki
  namespace: logging
spec:
  selector:
    app: loki
  ports:
    - port: 3100
      targetPort: 3100
      protocol: TCP
