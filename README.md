apiVersion: v1
kind: ServiceAccount
metadata:
  name: {{ .Values.serviceAccount.name }}
  namespace: {{ .Values.namespace }}


apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Values.name }}-deployment
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
      app: template-app

  template:
    metadata:
      labels:
        app: template-app

    spec:
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

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
              app: template-app

      {{- if .Values.volumes }}
      volumes:
{{ toYaml .Values.volumes | indent 8 }}
      {{- end }}

      containers:
        - name: {{ .Values.name }}-container
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          ports:
            - containerPort: {{ .Values.service.targetPort }}

          {{- if .Values.volumeMounts }}
          volumeMounts:
{{ toYaml .Values.volumeMounts | indent 12 }}
          {{- end }}

          envFrom:
          {{- range .Values.envFrom.configMaps }}
            - configMapRef:
                name: {{ . }}
          {{- end }}
          {{- range .Values.envFrom.secrets }}
            - secretRef:
                name: {{ . }}
          {{- end }}

          resources:
{{ toYaml .Values.resources | indent 12 }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            failureThreshold: 30
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 3
            failureThreshold: 3

          readinessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 15
            periodSeconds: 5
            timeoutSeconds: 3
            failureThreshold: 3

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]




apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.service.name }}
  namespace: {{ .Values.namespace }}

spec:
  type: ClusterIP
  selector:
    app: template-app

  ports:
    - name: http
      port: {{ .Values.service.port }}
      targetPort: {{ .Values.service.targetPort }}




{{- if .Values.autoscaling.enabled }}
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: {{ .Values.name }}-hpa
  namespace: {{ .Values.namespace }}

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: {{ .Values.name }}-deployment

  minReplicas: {{ .Values.autoscaling.minReplicas }}
  maxReplicas: {{ .Values.autoscaling.maxReplicas }}

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
          averageUtilization: {{ .Values.autoscaling.cpuUtilization }}
{{- end }}



{{- if .Values.pdb.enabled }}
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ .Values.name }}-pdb
  namespace: {{ .Values.namespace }}

spec:
  minAvailable: {{ .Values.pdb.minAvailable }}

  selector:
    matchLabels:
      app: template-app
{{- end }}