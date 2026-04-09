apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Values.name }}-deployment
  namespace: {{ .Values.namespace }}

spec:
  replicas: {{ .Values.replicaCount }}

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: {{ .Values.name }}-backend

  template:
    metadata:
      labels:
        app: {{ .Values.name }}-backend

    spec:
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: 30

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: {{ .Values.name }}-backend

      securityContext:
        runAsNonRoot: true
        runAsUser: {{ .Values.securityContext.runAsUser }}
        fsGroup: {{ .Values.securityContext.fsGroup }}

      containers:
        - name: {{ .Values.name }}-container
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          envFrom:
            {{- range .Values.configMaps }}
            - configMapRef:
                name: {{ . }}
            {{- end }}
            {{- range .Values.secretRefs }}
            - secretRef:
                name: {{ . }}
            {{- end }}

          ports:
            - containerPort: {{ .Values.service.targetPort }}

          resources:
            {{- toYaml .Values.resources | nindent 12 }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: {{ .Values.containerSecurityContext.allowPrivilegeEscalation }}
            readOnlyRootFilesystem: {{ .Values.containerSecurityContext.readOnlyRootFilesystem }}
            capabilities:
              drop:
                - ALL