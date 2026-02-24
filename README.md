apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: loki-pvc
  namespace: cbops
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: h06-vks-sp-6
  resources:
    requests:
      storage: 5Gi
---
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
          persistentVolumeClaim:
            claimName: grafana-pvc
---
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

This is my configuration file please correct me 
