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
      retention_period: 168h   # 7 days

    # ============================================
    # Chunk Store Configuration
    # ============================================
    chunk_store_config:
      max_look_back_period: 168h