report-builder-service

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
{{ toYaml .Values.hostAliases | indent 8 }}
      {{- end }}

      securityContext:
{{ toYaml .Values.deployment.securityContext | indent 8 }}

      topologySpreadConstraints:
{{ toYaml .Values.deployment.topologySpreadConstraints | indent 8 }}

      containers:
        - name: {{ .Values.container.name }}
          image: {{ .Values.image.repository }}:{{ .Values.image.tag }}
          imagePullPolicy: {{ .Values.container.imagePullPolicy }}

          ports:
            - containerPort: {{ .Values.container.port }}

          envFrom:
            {{- range .Values.envFrom.configMaps }}
            - configMapRef:
                name: {{ . }}
            {{- end }}
            {{- range .Values.envFrom.secrets }}
            - secretRef:
                name: {{ . }}
            {{- end }}

          env:
{{ toYaml .Values.env | indent 12 }}

          resources:
{{ toYaml .Values.resources | indent 12 }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
{{ toYaml .Values.probes.startup | indent 12 }}

          livenessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
{{ toYaml .Values.probes.liveness | indent 12 }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
{{ toYaml .Values.probes.readiness | indent 12 }}

          lifecycle:
            preStop:
              exec:
                command: {{ toJson .Values.lifecycle.preStop.command }}
