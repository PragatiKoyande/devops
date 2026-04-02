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
              memory: "1Gi"
            limits:
              cpu: "1"
              memory: "3Gi"

          readinessProbe:
            httpGet:
              path: /ready
              port: 3100
            initialDelaySeconds: 60
            periodSeconds: 10
            timeoutSeconds: 2

          livenessProbe:
            httpGet:
              path: /ready
              port: 3100
            initialDelaySeconds: 180
            periodSeconds: 10
            timeoutSeconds: 2

          startupProbe:
            httpGet:
              path: /ready
              port: 3100
            failureThreshold: 120
            periodSeconds: 10
            timeoutSeconds: 2

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 20"]

          securityContext:
            allowPrivilegeEscalation: false
            capabilities:
              drop:
                - ALL

          volumeMounts:
            - name: config
              mountPath: /etc/loki
              readOnly: true
            - name: storage
              mountPath: /var/loki
            - name: tmp
              mountPath: /tmp

      volumes:
        - name: config
          configMap:
            name: loki-config
        - name: storage
          persistentVolumeClaim:
            claimName: loki-pvc
        - name: tmp
          emptyDir: {}

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