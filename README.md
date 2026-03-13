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

      replication_factor: 1

      ring:
        kvstore:
          store: inmemory

    # ============================================
    # STORAGE CONFIGURATION (REQUIRED FOR BOLTDB SHIPPER)
    # ============================================
    storage_config:
      boltdb_shipper:
        active_index_directory: /var/loki/index
        cache_location: /var/loki/index_cache
        shared_store: filesystem

      filesystem:
        directory: /var/loki/chunks

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
      retention_period: 168h

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
    # ============================================
    compactor:
      working_directory: /var/loki/boltdb-shipper-compactor
      shared_store: filesystem
      retention_enabled: true

    # ============================================
    # Table Manager
    # ============================================
    table_manager:
      retention_deletes_enabled: true
      retention_period: 168h

    # ============================================
    # Ingester Configuration
    # ============================================
    ingester:
      chunk_idle_period: 5m
      chunk_retain_period: 30s
      wal:
        enabled: true
        dir: /var/loki/wal

    # ============================================
    # Query Range Optimization
    # ============================================
    query_range:
      align_queries_with_step: true
      max_retries: 5

    # ============================================
    # Frontend
    # ============================================
    frontend:
      log_queries_longer_than: 5s