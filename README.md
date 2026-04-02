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

  # 🔥 FIX: Avoid multi-attach PVC issue
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
            initialDelaySeconds: 15
            periodSeconds: 10
            failureThreshold: 5

          livenessProbe:
            httpGet:
              path: /ready
              port: 3100
            initialDelaySeconds: 45
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

---
# ================================
# Loki ConfigMap (IMPORTANT ADDITION)
# ================================
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
      path_prefix: /var/loki
      replication_factor: 1

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
        cache_location: /var/loki/cache
        shared_store: filesystem

      filesystem:
        directory: /var/loki/chunks

    limits_config:
      retention_period: 720h   # 🔥 30 days (change as needed)

    compactor:
      working_directory: /var/loki/compactor
      shared_store: filesystem

    chunk_store_config:
      max_look_back_period: 720h

    table_manager:
      retention_deletes_enabled: true
      retention_period: 720h