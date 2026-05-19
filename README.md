notification-service

apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Values.deployment.name }}
  namespace: {{ .Values.namespace }}
  labels:
    app: {{ .Values.labels.app }}

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
      serviceAccountName: {{ .Values.deployment.serviceAccountName }}
      enableServiceLinks: {{ .Values.deployment.enableServiceLinks }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}

      securityContext:
        {{- toYaml .Values.deployment.securityContext | nindent 8 }}

      volumes:
        {{- toYaml .Values.deployment.volumes | nindent 8 }}

      containers:
        - name: {{ .Values.container.name }}
          image: {{ .Values.image.repository }}:{{ .Values.image.tag }}
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          ports:
            - containerPort: {{ .Values.probes.port }}

          volumeMounts:
            {{- toYaml .Values.volumeMounts | nindent 12 }}

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
            {{- toYaml .Values.env | nindent 12 }}

          resources:
            {{- toYaml .Values.resources | nindent 12 }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            {{- toYaml .Values.probes.startup | nindent 12 }}

          livenessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            {{- toYaml .Values.probes.liveness | nindent 12 }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            {{- toYaml .Values.probes.readiness | nindent 12 }}

          lifecycle:
            preStop:
              exec:
                command: {{ toJson .Values.lifecycle.preStop.command }}

          securityContext:
            {{- toYaml .Values.containerSecurityContext | nindent 12 }}
