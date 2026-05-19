transactions-service

apiVersion: apps/v1
kind: Deployment

metadata:
  name: {{ .Values.deployment.name }}
  namespace: {{ .Values.namespace }}

spec:
  replicas: {{ .Values.deployment.replicas }}

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
      serviceAccountName: {{ .Values.serviceAccount.name }}
      automountServiceAccountToken: {{ .Values.serviceAccount.automountServiceAccountToken }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}

{{- if .Values.deployment.topologySpreadConstraints }}
      topologySpreadConstraints:
{{ toYaml .Values.deployment.topologySpreadConstraints | nindent 8 }}
{{- end }}

      securityContext:
{{ toYaml .Values.deployment.securityContext | nindent 8 }}

      containers:
        - name: {{ .Values.container.name }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.imagePullPolicy }}

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
            - containerPort: {{ .Values.probes.port }}

          resources:
{{ toYaml .Values.resources | nindent 12 }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.probes.startup.port }}
            failureThreshold: {{ .Values.probes.startup.failureThreshold }}
            periodSeconds: {{ .Values.probes.startup.periodSeconds }}
{{- if .Values.probes.startup.initialDelaySeconds }}
            initialDelaySeconds: {{ .Values.probes.startup.initialDelaySeconds }}
{{- end }}
{{- if .Values.probes.startup.timeoutSeconds }}
            timeoutSeconds: {{ .Values.probes.startup.timeoutSeconds }}
{{- end }}

          livenessProbe:
            tcpSocket:
              port: {{ .Values.probes.liveness.port }}
            initialDelaySeconds: {{ .Values.probes.liveness.initialDelaySeconds }}
            periodSeconds: {{ .Values.probes.liveness.periodSeconds }}
            timeoutSeconds: {{ .Values.probes.liveness.timeoutSeconds }}
            failureThreshold: {{ .Values.probes.liveness.failureThreshold }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.probes.readiness.port }}
            initialDelaySeconds: {{ .Values.probes.readiness.initialDelaySeconds }}
            periodSeconds: {{ .Values.probes.readiness.periodSeconds }}
            timeoutSeconds: {{ .Values.probes.readiness.timeoutSeconds }}
            failureThreshold: {{ .Values.probes.readiness.failureThreshold }}

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: false
            capabilities:
              drop:
                - ALL
