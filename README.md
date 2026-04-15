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
      app: {{ .Values.name }}

  template:
    metadata:
      labels:
        app: {{ .Values.name }}

    spec:
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      hostAliases:
      {{- toYaml .Values.hostAliases | nindent 6 }}

      volumes:
      {{- toYaml .Values.volumes | nindent 6 }}

      containers:
        - name: {{ .Values.name }}-container
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          ports:
            - containerPort: {{ .Values.service.targetPort }}

          volumeMounts:
          {{- toYaml .Values.volumeMounts | nindent 10 }}

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
          {{- toYaml .Values.extraEnv | nindent 10 }}
          {{- range .Values.secretEnv }}
            - name: {{ .name }}
              valueFrom:
                secretKeyRef:
                  name: {{ .secretName }}
                  key: {{ .key }}
          {{- end }}

          resources:
          {{- toYaml .Values.resources | nindent 10 }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

          livenessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          startupProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            failureThreshold: 60
            periodSeconds: 10

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

Error: YAML parse error on login-service/templates/deployment.yaml: error converting YAML to JSON: yaml: line 74: did not find expected key

getting this issue

