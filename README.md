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

      securityContext:
        runAsNonRoot: true
        runAsUser: {{ .Values.securityContext.runAsUser }}
        runAsGroup: {{ .Values.securityContext.runAsGroup }}
        fsGroup: {{ .Values.securityContext.fsGroup }}

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

          envFrom:
            - configMapRef:
                name: {{ .Values.env.configMaps.redis }}
            - configMapRef:
                name: {{ .Values.env.configMaps.oracle }}
            - secretRef:
                name: {{ .Values.env.secrets.oracle }}
            - configMapRef:
                name: {{ .Values.env.configMaps.kafka }}

          env:
            - name: SPRING_PROFILES_ACTIVE
              value: {{ .Values.springProfile }}

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
            failureThreshold: {{ .Values.startupProbe.failureThreshold }}
            periodSeconds: {{ .Values.startupProbe.periodSeconds }}

          livenessProbe:
            tcpSocket:
              port: {{ .Values.containerPort }}
            initialDelaySeconds: {{ .Values.livenessProbe.initialDelaySeconds }}
            periodSeconds: {{ .Values.livenessProbe.periodSeconds }}
            timeoutSeconds: {{ .Values.livenessProbe.timeoutSeconds }}
            failureThreshold: {{ .Values.livenessProbe.failureThreshold }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.containerPort }}
            initialDelaySeconds: {{ .Values.readinessProbe.initialDelaySeconds }}
            periodSeconds: {{ .Values.readinessProbe.periodSeconds }}
            timeoutSeconds: {{ .Values.readinessProbe.timeoutSeconds }}
            failureThreshold: {{ .Values.readinessProbe.failureThreshold }}

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

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