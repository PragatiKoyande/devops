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




        this is my current configuration file can you please add production grade requiremnt in this what you have mentione dand send me back the entire file
