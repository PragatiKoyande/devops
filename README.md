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
      app: {{ .Values.deployment.labels.app }}

  template:
    metadata:
      labels:
        app: {{ .Values.deployment.labels.app }}

    spec:
      serviceAccountName: {{ .Values.deployment.serviceAccountName }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}
      enableServiceLinks: {{ .Values.deployment.enableServiceLinks }}

{{- if .Values.deployment.securityContext }}
      securityContext:
{{ toYaml .Values.deployment.securityContext | nindent 8 }}
{{- end }}

{{- if .Values.hostAliases }}
      hostAliases:
{{ toYaml .Values.hostAliases | nindent 8 }}
{{- end }}

{{- if .Values.deployment.topologySpreadConstraints }}
      topologySpreadConstraints:
{{ toYaml .Values.deployment.topologySpreadConstraints | nindent 8 }}
{{- end }}

{{- if .Values.deployment.volumes }}
      volumes:
{{ toYaml .Values.deployment.volumes | nindent 8 }}
{{- end }}

      containers:
        - name: {{ .Values.container.name }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.imagePullPolicy }}

{{- if .Values.deployment.volumeMounts }}
          volumeMounts:
{{ toYaml .Values.deployment.volumeMounts | nindent 12 }}
{{- end }}

{{- if .Values.envFrom }}
          envFrom:
{{ toYaml .Values.envFrom | nindent 12 }}
{{- end }}

{{- if or .Values.env .Values.envCommon }}
          env:
{{- range .Values.env }}
            - name: {{ .name }}
{{- if hasKey . "value" }}
              value: {{ .value | quote }}
{{- end }}
{{- if hasKey . "valueFrom" }}
              valueFrom:
{{ toYaml .valueFrom | nindent 16 }}
{{- end }}
{{- end }}

{{- range .Values.envCommon }}
            - name: {{ .name }}
{{- if hasKey . "value" }}
              value: {{ .value | quote }}
{{- end }}
{{- if hasKey . "valueFrom" }}
              valueFrom:
{{ toYaml .valueFrom | nindent 16 }}
{{- end }}
{{- end }}
{{- end }}

          ports:
            - containerPort: {{ .Values.container.port }}

          resources:
{{ toYaml .Values.resources | nindent 12 }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            initialDelaySeconds: {{ .Values.probes.startup.initialDelaySeconds }}
            periodSeconds: {{ .Values.probes.startup.periodSeconds }}
            timeoutSeconds: {{ .Values.probes.startup.timeoutSeconds }}
            failureThreshold: {{ .Values.probes.startup.failureThreshold }}

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

{{- if .Values.lifecycle.preStop }}
          lifecycle:
            preStop:
              exec:
                command:
{{ toYaml .Values.lifecycle.preStop | nindent 18 }}
{{- end }}

{{- if .Values.containerSecurityContext }}
          securityContext:
{{ toYaml .Values.containerSecurityContext | nindent 12 }}
{{- end }}








lifecycle:
  preStop:
    - /bin/sh
    - -c
    - sleep 10