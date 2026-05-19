apiVersion: apps/v1
kind: Deployment

metadata:
  name: {{ .Values.deployment.name }}
  namespace: {{ .Values.namespace }}
  labels:
    app: {{ .Values.labels.app }}

spec:
  replicas: {{ .Values.deployment.replicas }}

  strategy:
    type: {{ .Values.deployment.strategy.type }}
    rollingUpdate:
      maxUnavailable: {{ .Values.deployment.strategy.maxUnavailable }}
      maxSurge: {{ .Values.deployment.strategy.maxSurge }}

  selector:
    matchLabels:
      app: {{ .Values.labels.app }}

  template:
    metadata:
      labels:
        app: {{ .Values.labels.app }}

    spec:
      serviceAccountName: {{ .Values.deployment.serviceAccountName }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}

{{- if .Values.deployment.securityContext }}
      securityContext:
{{ toYaml .Values.deployment.securityContext | nindent 8 }}
{{- end }}

{{- if .Values.deployment.topologySpreadConstraints }}
      topologySpreadConstraints:
{{ toYaml .Values.deployment.topologySpreadConstraints | nindent 8 }}
{{- end }}

      containers:
        - name: {{ .Values.container.name }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}

{{- if .Values.containerSecurityContext }}
          securityContext:
{{ toYaml .Values.containerSecurityContext | nindent 12 }}
{{- end }}

          ports:
            - containerPort: {{ .Values.probes.port }}

{{- if .Values.envFrom }}
          envFrom:
{{- range .Values.envFrom.configMaps }}
            - configMapRef:
                name: {{ . }}
{{- end }}
{{- range .Values.envFrom.secrets }}
            - secretRef:
                name: {{ . }}
{{- end }}
{{- end }}

{{- if .Values.env }}
          env:
{{ toYaml .Values.env | nindent 12 }}
{{- end }}

          resources:
{{ toYaml .Values.resources | nindent 12 }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            failureThreshold: {{ .Values.probes.startup.failureThreshold }}
            periodSeconds: {{ .Values.probes.startup.periodSeconds }}

          livenessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            initialDelaySeconds: {{ .Values.probes.liveness.initialDelaySeconds }}
            periodSeconds: {{ .Values.probes.liveness.periodSeconds }}
            timeoutSeconds: {{ .Values.probes.liveness.timeoutSeconds }}
            failureThreshold: {{ .Values.probes.liveness.failureThreshold }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            initialDelaySeconds: {{ .Values.probes.readiness.initialDelaySeconds }}
            periodSeconds: {{ .Values.probes.readiness.periodSeconds }}
            timeoutSeconds: {{ .Values.probes.readiness.timeoutSeconds }}
            failureThreshold: {{ .Values.probes.readiness.failureThreshold }}

{{- if .Values.lifecycle }}
          lifecycle:
{{ toYaml .Values.lifecycle | nindent 12 }}
{{- end }}