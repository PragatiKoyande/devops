apiVersion: apps/v1
kind: Deployment

metadata:
  name: {{ .Values.deployment.name }}
  namespace: {{ .Values.namespace }}

spec:
  replicas: {{ .Values.deployment.replicas }}
  revisionHistoryLimit: {{ .Values.deployment.revisionHistoryLimit }}

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
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}
      enableServiceLinks: {{ .Values.deployment.enableServiceLinks }}

{{- if .Values.hostAliases }}
      hostAliases:
{{ toYaml .Values.hostAliases | nindent 8 }}
{{- end }}

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
          imagePullPolicy: {{ .Values.image.imagePullPolicy }}

          ports:
            - containerPort: {{ .Values.container.port }}

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
{{ toYaml .Values.probes.startup | nindent 12 }}

          livenessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
{{ toYaml .Values.probes.liveness | nindent 12 }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
{{ toYaml .Values.probes.readiness | nindent 12 }}

{{- if .Values.lifecycle }}
          lifecycle:
{{ toYaml .Values.lifecycle | nindent 12 }}
{{- end }}