D:\Pragati\DEV-Deployment\Grafana-Deployment\Loki>kubectl describe cm fluent-bit-config -n tanzu-system-logging --kubeconfig h06vksuatcbopscls.conf
Name:         fluent-bit-config
Namespace:    tanzu-system-logging
Labels:       k8s-app=fluent-bit
              kapp.k14s.io/app=1774341192231442519
              kapp.k14s.io/association=v1.1eef7be45479a3b8c126212f0855b047
Annotations:  kapp.k14s.io/identity: v1;tanzu-system-logging//ConfigMap/fluent-bit-config;v1
              kapp.k14s.io/original:
                {"apiVersion":"v1","data":{"filters.conf":"[FILTER]\n  Name                kubernetes\n  Match               kube.*\n  Kube_URL           ...
              kapp.k14s.io/original-diff-md5: c6e94dc94aed3401b5d0f26ed6c0bff3

Data
====
fluent-bit.conf:
----
[Service]
  Flush         1
  Log_Level     info
  Daemon        off
  Parsers_File  parsers.conf
  HTTP_Server   On
  HTTP_Listen   0.0.0.0
  HTTP_Port     2020
  HTTP_Listen   0.0.0.0
@INCLUDE inputs.conf
@INCLUDE filters.conf
@INCLUDE outputs.conf


inputs.conf:
----
[INPUT]
  Name                tail
  Path                /var/log/containers/*.log
  Parser              cri
  DB                  /var/log/flb_kube.db
  Tag                 kube.*
  Mem_Buf_Limit       50MB
  Skip_Long_Lines     On
  Refresh_Interval    10

[INPUT]
  Name                systemd
  Tag                 kube_systemd.*
  Path                /var/log/journal
  DB                  /var/log/flb_kube_systemd.db
  Systemd_Filter      _SYSTEMD_UNIT=kubelet.service
  Systemd_Filter      _SYSTEMD_UNIT=containerd.service
  Read_From_Tail      On
  Strip_Underscores   On

[INPUT]
  Name              tail
  Tag               apiserver_audit
  Path              /var/log/kubernetes/audit.log
  Parser            syslog
  DB                /var/log/flb_kube_audit.db
  Mem_Buf_Limit     50MB
  Refresh_Interval  10
  Skip_Long_Lines   On

[INPUT]
  Name                tail
  Tag                 audit.*
  Path                /var/log/audit/audit.log
  Parser              auditlog
  DB                  /var/log/flb_system_audit.db
  Mem_Buf_Limit       50MB
  Buffer_Chunk_Size   10MB
  Buffer_Max_Size     50MB
  Skip_Long_Lines     On
  Refresh_Interval    10


outputs.conf:
----
[OUTPUT]
  Name                 stdout
  Match                *

[OUTPUT]
  Name                 syslog
  Match                kube.*
  Host                 10.176.58.109
  Port                 514
  Mode                 tcp
  Syslog_Format        rfc5424
  Syslog_Hostname_key  tkg_cluster
  Syslog_Appname_key   pod_name
  Syslog_Procid_key    container_name
  Syslog_Message_key   message
  Syslog_SD_key        k8s
  Syslog_SD_key        labels
  Syslog_SD_key        annotations
  Syslog_SD_key        tkg
# Syslog - systemd

[OUTPUT]
  Name                  syslog
  Match                 kube.audit
  Host                  10.176.58.109
  Port                  514
  Mode                  tcp
  Syslog_Format         rfc5424
  Syslog_Hostname_key   node_name
  Syslog_Appname_key    kubernetes
  Syslog_Message_key    message

[OUTPUT]
  Name                  syslog
  Match                 audit.*
  Host                  10.176.58.109
  Port                  514
  Mode                  tcp
  Syslog_Format         rfc5424
  Syslog_Hostname_key   node_name
  Syslog_Appname_key    kubernetes
  Syslog_Message_key    message

[OUTPUT]
  Name                  syslog
  Match                 apiserver_audit
  Host                  10.176.58.109
  Port                  514
  Mode                  tcp
  Syslog_Format         rfc5424
  #Syslog_Hostname_key   host
  #Syslog_Appname_key    userAgent
  #Syslog_Procid_key     auditID
  Syslog_Message_key    log
  syslog_maxsize        8192

[OUTPUT]
  Name                  loki
  Match                 *
  Host                  loki.logging.svc.cluster.local
  Port                  3100
  uri                   /loki/api/v1/push
  labels                job=fluentbit
  label_keys            $kubernetes['namespace_name'],$kubernetes['pod_name'],$kubernetes['container_name']
  line_format           json


parsers.conf:
----
[PARSER]
  Name multiline
  Format regex
  Regex /(?<time>[A-Za-z]+ \d+ \d+\:\d+\:\d+)(?<message>.*)/
  Time_Key  time
  Time_Format %b %d %H:%M:%S
[PARSER]
  Name                  json
  Format                json
  Time_Key              time
  Time_Format           %d/%b/%Y:%H:%M:%S %z


[PARSER]
  Name                 logfmt
  Format               logfmt

[PARSER]
  Name                 auditlog
  Format               regex
  Regex                ^(type=\w+)\s+msg=audit\((\d+\.\d+:\d+)\):\s+(.*)
  Time_Key             timestamp
  Time_Format          %s.%L

[PARSER]
  Name                 docker
  Format               json
  Time_Key             time
  Time_Format          %Y-%m-%dT%H:%M:%S.%L
  Time_Keep            On

[PARSER]
  Name                 docker-daemon
  Format               regex
  Regex                time="(?<time>[^ ]*)" level=(?<level>[^ ]*) msg="(?<msg>[^ ].*)"
  Time_Key             time
  Time_Format          %Y-%m-%dT%H:%M:%S.%L
  Time_Keep            On

[PARSER]
  Name                 cri
  Format               regex
  Regex                ^(?<time>[^ ]+) (?<stream>stdout|stderr) (?<logtag>[^ ]*) (?<message>.*)$
  Time_Key             time
  Time_Format          %Y-%m-%dT%H:%M:%S.%L%z

[PARSER]
  Name   auditlog
  Format regex
  Regex  ^(type=\w+)\s+msg=audit\((\d+\.\d+:\d+)\):\s+(.*)
  Time_Key timestamp
  Time_Format %s.%L

[PARSER]
  Name        syslog
  Format      regex
  Regex       ^\<(?<pri>[0-9]+)\>(?<time>[^ ]* {1,2}[^ ]* [^ ]*) (?<host>[^ ]*) (?<ident>[a-zA-Z0-9_\/\.\-]*)(?:\[(?<pid>[0-9]+)\])?(?:[^\:]*\:)? *(?<message>.*)$
  Time_Key    time
  Time_Format %b %d %H:%M:%S

[PARSER]
  Name                 syslog-rfc5424
  Format               regex
  Regex                ^\<(?<pri>[0-9]{1,5})\>1 (?<time>[^ ]+) (?<host>[^ ]+) (?<ident>[^ ]+) (?<pid>[-0-9]+) (?<msgid>[^ ]+) (?<extradata>(\[(.*)\]|-)) (?<message>.+)$
  Time_Key             time
  Time_Format          %Y-%m-%dT%H:%M:%S.%L
  Time_Keep            On

[PARSER]
  Name                 kube-custom
  Format               regex
  Regex                (?<tag>[^.]+)?\.?(?<pod_name>[a-z0-9](?:[-a-z0-9]*[a-z0-9])?(?:\.[a-z0-9]([-a-z0-9]*[a-z0-9])?)*)_(?<namespace_name>[^_]+)_(?<container_name>.+)-(?<docker_id>[a-z0-9]{64})\.log$



  This is my fleunt-bit config yaml file and configuartion provided by infra team and I have my loki configuration:

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

      # FIX ADDED: Required for PVC write permission
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

we rae not able to see the  label_keys            $kubernetes['namespace_name'],$kubernetes['pod_name'],$kubernetes['container_name'] in label browser and thus not able to see the data recommend few thins
      
