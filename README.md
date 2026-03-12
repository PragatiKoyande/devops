This is mu production ready grafana file:

apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: grafana-pvc
  namespace: uat-cbops1
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: h06-vks-sp-5
  resources:
    requests:
      storage: 5Gi
--- 
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: grafana-pdb
  namespace: uat-cbops1
spec:
  minAvailable: 0
  selector:
    matchLabels:
      app: grafana
--- 
apiVersion: apps/v1
kind: Deployment
metadata:
  name: grafana
  namespace: uat-cbops1
spec:
  replicas: 1
  revisionHistoryLimit: 10
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1
  selector:
    matchLabels:
      app: grafana
  template:
    metadata:
      labels:
        app: grafana
    spec:
      terminationGracePeriodSeconds: 20

      affinity:
        podAntiAffinity:
          preferredDuringSchedulingIgnoredDuringExecution:
            - weight: 100
              podAffinityTerm:
                labelSelector:
                  matchExpressions:
                    - key: app
                      operator: In
                      values:
                        - grafana
                topologyKey: kubernetes.io/hostname

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: grafana

      containers:
        - name: grafana
          image: h06vksharbor.corp.ad.sbi/cbops/grafana/grafana:10.2.3
          ports:
            - containerPort: 3000

          resources:
            requests:
              cpu: "200m"
              memory: "512Mi"
            limits:
              cpu: "1"
              memory: "1Gi"

          livenessProbe:
            httpGet:
              path: /grafana/api/health
              port: 3000
            initialDelaySeconds: 20
            periodSeconds: 20
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            httpGet:
              path: /grafana/api/health
              port: 3000
            initialDelaySeconds: 10
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 3

          env:
            - name: GF_SECURITY_ADMIN_USER
              value: admin
            - name: GF_SECURITY_ADMIN_PASSWORD
              value: admin123
            - name: GF_SERVER_DOMAIN
              value: fincore-uat.sbi
            - name: GF_SERVER_HTTP_ADDR
              value: "0.0.0.0"
            - name: GF_SERVER_ROOT_URL
              value: https://fincore-uat.sbi/grafana/
            - name: GF_SERVER_SERVE_FROM_SUB_PATH
              value: "true"
            - name: GF_SECURITY_CONTENT_SECURITY_POLICY
              value: "false"
            - name: GF_ANALYTICS_CHECK_FOR_PLUGIN_UPDATES
              value: "false"
            - name: GF_ANALYTICS_REPORTING_ENABLED
              value: "false"
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
  namespace: uat-cbops1
spec:
  type: ClusterIP
  sessionAffinity: None
  selector:
    app: grafana
  ports:
    - port: 3000
      targetPort: 3000


      I want the similar pattern for another environment so for which I m pasting my old manisfest file dont alter the exsiting values just add on production ready setup to it:

      apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: grafana-pvc
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
      securityContext:
        fsGroup: 472

      containers:
        - name: grafana
          image: h06vksharbor.corp.ad.sbi/cbops/grafana/grafana:10.2.3
          ports:
            - containerPort: 3000

          env:
            - name: GF_SECURITY_ADMIN_USER
              value: admin
            - name: GF_SECURITY_ADMIN_PASSWORD
              value: admin123

            - name: GF_SERVER_DOMAIN
              value: fincorest.sbi
            - name: GF_SERVER_HTTP_ADDR
              value: "0.0.0.0"
            - name: GF_SERVER_ROOT_URL
              value: "https://fincorest.sbi/grafana/"
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
    - name: http
      port: 3000
      targetPort: 3000
