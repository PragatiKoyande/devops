apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: grafana-pvc
  namespace: cbops
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: h06-vks-sp-3
  resources:
    requests:
      storage: 5Gi
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: grafana
  namespace: cbops
spec:
  replicas: 1
  selector:
    matchLabels:
      app: grafana
  template:
    metadata:
      labels:
        app: grafana
    spec:
      containers:
        - name: grafana
          image: h06vksharbor.corp.ad.sbi/cbops/grafana/grafana:10.2.3
          ports:
            - containerPort: 3000
          env:
            - name: GF_SECURITY_ADMIN_USER
              value: admin

            - name: GF_SERVER_DOMAIN
              value: fincoreuat.sbi
            - name: GF_SERVER_HTTP_ADDR
              value: "0.0.0.0"
            - name: GF_SERVER_ROOT_URL
              value: https://fincoreuat.sbi/grafana/
            - name: GF_SERVER_SERVE_FROM_SUB_PATH
              value: "true"

          volumeMounts:
            - name: grafana-storage
              mountPath: /var/lib/grafana

      volumes:
        - name: grafana-storage
          persistentVolumeClaim:
            claimName: grafana-pvc
---
apiVersion: v1
kind: Service
metadata:
  name: grafana
  namespace: cbops
spec:
  type: ClusterIP
  selector:
    app: grafana
  ports:
    - port: 3000
      targetPort: 3000

      This is my grafana configuration file where exaactly we ned to do chnages
