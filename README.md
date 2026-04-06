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
      compactor_address: ""

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

    # chunk_store_config:
    #   max_look_back_period: 720h

    compactor:
      working_directory: /var/loki/compactor
      shared_store: filesystem
      retention_enabled: false
      compaction_interval: 999999h

    table_manager:
      retention_deletes_enabled: true
      retention_period: 168h

    ingester:
      chunk_idle_period: 3m
      chunk_retain_period: 30s
      chunk_target_size: 1048576
      max_chunk_age: 1h
      wal:
        enabled: false
        dir: /var/loki/wal

    query_range:
      align_queries_with_step: true
      max_retries: 5
      cache_results: false

    frontend:
      log_queries_longer_than: 5s