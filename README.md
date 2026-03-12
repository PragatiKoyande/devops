This is my production reday file for config configuration

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

I want similar configuration for another file for different env which is non production so I m pasting below can you transform in below file in above mentioned format:

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
