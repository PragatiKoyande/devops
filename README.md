
login-service


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
      serviceAccountName: {{ .Values.deployment.pod.serviceAccountName }}
      terminationGracePeriodSeconds: {{ .Values.deployment.pod.terminationGracePeriodSeconds }}
      enableServiceLinks: {{ .Values.deployment.pod.enableServiceLinks }}

      securityContext:
        runAsNonRoot: {{ .Values.deployment.pod.securityContext.runAsNonRoot }}
        runAsUser: {{ .Values.deployment.pod.securityContext.runAsUser }}
        fsGroup: {{ .Values.deployment.pod.securityContext.fsGroup }}

      {{- if .Values.hostAliases }}
      hostAliases:
        {{- toYaml .Values.hostAliases | nindent 8 }}
      {{- end }}

      {{- if .Values.deployment.pod.volumes }}
      volumes:
        {{- toYaml .Values.deployment.pod.volumes | nindent 8 }}
      {{- end }}

      containers:
        - name: {{ .Values.container.name }}
          image: {{ .Values.image.repository }}:{{ .Values.image.tag }}
          imagePullPolicy: Always

          ports:
            - containerPort: {{ .Values.ports.containerPort }}

          {{- if .Values.volumeMounts }}
          volumeMounts:
            {{- toYaml .Values.volumeMounts | nindent 12 }}
          {{- end }}

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

          env:
            {{- if .Values.env }}
            {{- toYaml .Values.env | nindent 12 }}
            {{- end }}

            {{- if .Values.secretEnv }}
            {{- range .Values.secretEnv }}
            - name: {{ .name }}
              valueFrom:
                secretKeyRef:
                  name: {{ .secretName }}
                  key: {{ .key }}
            {{- end }}
            {{- end }}

          resources:
            {{- toYaml .Values.resources | nindent 12 }}

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
            preStop:
              exec:
                command: {{ toYaml .Values.lifecycle.preStop.command | nindent 18 }}

          securityContext:
            allowPrivilegeEscalation: {{ .Values.securityContext.allowPrivilegeEscalation }}
            readOnlyRootFilesystem: {{ .Values.securityContext.readOnlyRootFilesystem }}
            capabilities:
              drop:
                {{- toYaml .Values.securityContext.capabilities.drop | nindent 16 }}
