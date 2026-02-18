apiVersion: v1
kind: PersistentVolume
metadata:
  name: loki-pv
spec:
  capacity:
    storage: 200Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  storageClassName: manual
  hostPath:
    path: /mnt/loki-data

apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: loki-pvc
  namespace: logging
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: manual
  resources:
    requests:
      storage: 200Gi
_---_--------------------
volumeMounts:
  - name: storage
    mountPath: /loki
--------------------------
volumes:
  - name: storage
    persistentVolumeClaim:
      claimName: loki-pvc
--------------------------
limits_config:
  retention_period: 720h   # 30 days

compactor:
  working_directory: /loki/compactor
  shared_store: filesystem
  retention_enabled: true

schema_config:
  configs:
    - from: 2024-01-01
      store: boltdb-shipper
      object_store: filesystem
      schema: v11
      index:
        prefix: index_
        period: 24h

storage_config:
  boltdb_shipper:
    active_index_directory: /loki/index
    cache_location: /loki/cache
    shared_store: filesystem
  filesystem:
    directory: /loki/chunks