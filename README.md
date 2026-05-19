journal-service

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
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}

      securityContext:
{{ toYaml .Values.deployment.securityContext | indent 8 }}

      topologySpreadConstraints:
{{ toYaml .Values.deployment.topologySpreadConstraints | indent 8 }}

      containers:
        - name: {{ .Values.container.name }}

          image: {{ .Values.image.repository }}:{{ .Values.image.tag }}
          imagePullPolicy: {{ .Values.image.imagePullPolicy }}

          envFrom:
{{ toYaml .Values.envFrom | indent 12 }}

          env:
{{ toYaml .Values.env | indent 12 }}

          ports:
            - containerPort: {{ .Values.probes.port }}

          resources:
{{ toYaml .Values.resources | indent 12 }}

          securityContext:
{{ toYaml .Values.containerSecurityContext | indent 12 }}

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

          startupProbe:
            tcpSocket:
              port: {{ .Values.probes.startup.port }}
            initialDelaySeconds: {{ .Values.probes.startup.initialDelaySeconds }}
            periodSeconds: {{ .Values.probes.startup.periodSeconds }}
            timeoutSeconds: {{ .Values.probes.startup.timeoutSeconds }}
            failureThreshold: {{ .Values.probes.startup.failureThreshold }}

          lifecycle:
{{ toYaml .Values.lifecycle | indent 12 }}
