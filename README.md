apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Values.deployment.name }}
  namespace: {{ .Values.namespace }}

spec:
  replicas: {{ .Values.deployment.replicas }}

  revisionHistoryLimit: {{ .Values.deployment.revisionHistoryLimit }}

  strategy:
    type: RollingUpdate
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
      annotations:
        prometheus.io/scrape: "{{ .Values.deployment.annotations.prometheus.scrape }}"
        prometheus.io/port: "{{ .Values.deployment.annotations.prometheus.port }}"

    spec:
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      hostAliases:
{{ toYaml .Values.deployment.hostAliases | indent 6 }}

      topologySpreadConstraints:
        - maxSkew: {{ .Values.deployment.topologySpreadConstraints.maxSkew }}
          topologyKey: {{ .Values.deployment.topologySpreadConstraints.topologyKey }}
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: {{ .Values.deployment.labels.app }}

      containers:
        - name: {{ .Values.deployment.container.name }}
          image: {{ .Values.deployment.container.image }}
          imagePullPolicy: {{ .Values.deployment.container.imagePullPolicy }}

          ports:
            - containerPort: {{ .Values.deployment.container.port }}

          # =========================
          # ENV FROM
          # =========================
          envFrom:
{{- range .Values.deployment.container.envFrom.configMaps }}
            - configMapRef:
                name: {{ . }}
{{- end }}
{{- range .Values.deployment.container.envFrom.secrets }}
            - secretRef:
                name: {{ . }}
{{- end }}

          # =========================
          # ENV
          # =========================
          env:
{{ toYaml .Values.deployment.container.env | indent 12 }}

          # =========================
          # RESOURCES
          # =========================
          resources:
{{ toYaml .Values.deployment.container.resources | indent 12 }}

          # =========================
          # PROBES
          # =========================
          startupProbe:
            tcpSocket:
              port: {{ .Values.deployment.container.probes.startup.port }}
            failureThreshold: {{ .Values.deployment.container.probes.startup.failureThreshold }}
            periodSeconds: {{ .Values.deployment.container.probes.startup.periodSeconds }}

          livenessProbe:
            tcpSocket:
              port: {{ .Values.deployment.container.probes.liveness.port }}
            initialDelaySeconds: {{ .Values.deployment.container.probes.liveness.initialDelaySeconds }}
            periodSeconds: {{ .Values.deployment.container.probes.liveness.periodSeconds }}
            timeoutSeconds: {{ .Values.deployment.container.probes.liveness.timeoutSeconds }}
            failureThreshold: {{ .Values.deployment.container.probes.liveness.failureThreshold }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.deployment.container.probes.readiness.port }}
            initialDelaySeconds: {{ .Values.deployment.container.probes.readiness.initialDelaySeconds }}
            periodSeconds: {{ .Values.deployment.container.probes.readiness.periodSeconds }}
            timeoutSeconds: {{ .Values.deployment.container.probes.readiness.timeoutSeconds }}
            failureThreshold: {{ .Values.deployment.container.probes.readiness.failureThreshold }}

          # =========================
          # LIFECYCLE
          # =========================
          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh","-c","sleep {{ .Values.deployment.container.lifecycle.preStopSleep }}"]