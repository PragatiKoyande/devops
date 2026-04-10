# =====================================================
# Service Account
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: {{ .Values.processStatus.serviceAccount.name }}
  namespace: {{ .Values.namespace }}
automountServiceAccountToken: false

---
# =====================================================
# Deployment
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Values.processStatus.deployment.name }}
  namespace: {{ .Values.namespace }}

spec:
  replicas: {{ .Values.processStatus.replicaCount }}
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: {{ .Values.processStatus.appLabel }}

  template:
    metadata:
      labels:
        app: {{ .Values.processStatus.appLabel }}

    spec:
      serviceAccountName: {{ .Values.processStatus.serviceAccount.name }}
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
              app: {{ .Values.processStatus.appLabel }}

      containers:
        - name: process-status-container
          image: "{{ .Values.processStatus.image.repository }}:{{ .Values.processStatus.image.tag }}"
          imagePullPolicy: {{ .Values.processStatus.image.pullPolicy }}

          volumeMounts:
            - name: tmp-dir
              mountPath: /tmp

          envFrom:
            - configMapRef:
                name: {{ .Values.processStatus.redisConfigName }}
            - configMapRef:
                name: {{ .Values.processStatus.oracleConfigName }}
            - secretRef:
                name: {{ .Values.processStatus.oracleSecretName }}

          ports:
            - containerPort: {{ .Values.processStatus.containerPort }}

          resources:
            requests:
              cpu: {{ .Values.processStatus.resources.requests.cpu }}
              memory: {{ .Values.processStatus.resources.requests.memory }}
            limits:
              cpu: {{ .Values.processStatus.resources.limits.cpu }}
              memory: {{ .Values.processStatus.resources.limits.memory }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.processStatus.containerPort }}
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: {{ .Values.processStatus.containerPort }}
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: {{ .Values.processStatus.containerPort }}
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
  name: {{ .Values.processStatus.service.name }}
  namespace: {{ .Values.namespace }}

spec:
  selector:
    app: {{ .Values.processStatus.appLabel }}

  ports:
    - name: http
      protocol: TCP
      port: {{ .Values.processStatus.service.port }}
      targetPort: {{ .Values.processStatus.containerPort }}

  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler
# =====================================================
{{- if .Values.processStatus.hpa.enabled }}
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: {{ .Values.processStatus.hpa.name }}
  namespace: {{ .Values.namespace }}

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: {{ .Values.processStatus.deployment.name }}

  minReplicas: {{ .Values.processStatus.hpa.minReplicas }}
  maxReplicas: {{ .Values.processStatus.hpa.maxReplicas }}

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
          averageUtilization: {{ .Values.processStatus.hpa.cpuUtilization }}
{{- end }}

---
# =====================================================
# Pod Disruption Budget
# =====================================================
{{- if .Values.processStatus.pdb.enabled }}
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ .Values.processStatus.pdb.name }}
  namespace: {{ .Values.namespace }}

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: {{ .Values.processStatus.appLabel }}
{{- end }}