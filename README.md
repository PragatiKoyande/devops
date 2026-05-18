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

      securityContext:
{{ toYaml .Values.deployment.securityContext | indent 8 }}

      hostAliases:
{{ toYaml .Values.hostAliases | nindent 8 }}

      topologySpreadConstraints:
{{ toYaml .Values.deployment.topologySpreadConstraints | nindent 8 }}

      volumes:
{{ toYaml .Values.deployment.volumes | nindent 8 }}

      containers:
        - name: {{ .Values.container.name }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.imagePullPolicy }}

          volumeMounts:
{{ toYaml .Values.deployment.volumeMounts | nindent 12 }}

          envFrom:
{{ toYaml .Values.envFrom | nindent 12 }}

          env:
{{ toYaml .Values.env | nindent 12 }}
{{ toYaml .Values.envCommon | nindent 12 }}

          ports:
            - containerPort: {{ .Values.container.port }}

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

          lifecycle:
{{ toYaml .Values.lifecycle | nindent 12 }}

          securityContext:
{{ toYaml .Values.containerSecurityContext | nindent 12 }}