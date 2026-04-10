# =====================================================
# Service Account
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: {{ .Values.serviceAccountName }}
  namespace: {{ .Values.namespace }}
automountServiceAccountToken: false

---
# =====================================================
# Deployment
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Values.deploymentName }}
  namespace: {{ .Values.namespace }}

spec:
  replicas: {{ .Values.replicaCount }}
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: {{ .Values.appLabel }}

  template:
    metadata:
      labels:
        app: {{ .Values.appLabel }}

    spec:
      serviceAccountName: {{ .Values.serviceAccountName }}
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      volumes:
        - name: tmp-dir
          emptyDir:
            medium: Memory
            sizeLimit: 64Mi

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: {{ .Values.appLabel }}

      containers:
        - name: {{ .Values.containerName }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          volumeMounts:
            - name: tmp-dir
              mountPath: /tmp

          envFrom:
            - configMapRef:
                name: {{ .Values.redisConfigName }}
            - configMapRef:
                name: {{ .Values.oracleConfigName }}
            - secretRef:
                name: {{ .Values.oracleSecretName }}

          ports:
            - containerPort: {{ .Values.containerPort }}

          resources:
            requests:
              cpu: {{ .Values.resources.requests.cpu }}
              memory: {{ .Values.resources.requests.memory }}
            limits:
              cpu: {{ .Values.resources.limits.cpu }}
              memory: {{ .Values.resources.limits.memory }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.containerPort }}
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: {{ .Values.containerPort }}
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: {{ .Values.containerPort }}
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: true
            capabilities:
              drop:
                - ALL

---
# =====================================================
# Service
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.serviceName }}
  namespace: {{ .Values.namespace }}

spec:
  selector:
    app: {{ .Values.appLabel }}

  ports:
    - name: http
      protocol: TCP
      port: {{ .Values.servicePort }}
      targetPort: {{ .Values.containerPort }}

  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler
# =====================================================
{{- if .Values.hpa.enabled }}
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: {{ .Values.hpaName }}
  namespace: {{ .Values.namespace }}

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: {{ .Values.deploymentName }}

  minReplicas: {{ .Values.hpa.minReplicas }}
  maxReplicas: {{ .Values.hpa.maxReplicas }}

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: {{ .Values.hpa.cpuUtilization }}
{{- end }}

---
# =====================================================
# Pod Disruption Budget
# =====================================================
{{- if .Values.pdb.enabled }}
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ .Values.pdbName }}
  namespace: {{ .Values.namespace }}

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: {{ .Values.appLabel }}
{{- end }}