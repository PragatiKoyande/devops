# ============================================
# ConfigMap for Loki
# Non-Production Environment
# Aligned with enterprise deployment format
# ============================================
apiVersion: v1
kind: ConfigMap
metadata:
  name: loki-config
  namespace: logging

  # Protect ConfigMap metadata and describe purpose
  annotations:
    description: "Loki main configuration - non-production environment"
    config.kubernetes.io/local-config: "true"

  labels:
    app: loki
    component: logging
    managed-by: kubernetes

# Prevent accidental runtime edits
immutable: true

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

      replication_factor: 1  # Unchanged (single replica deployment)

      ring:
        kvstore:
          store: inmemory    # Unchanged as required

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