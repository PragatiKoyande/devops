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
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}

      securityContext:
        runAsNonRoot: {{ .Values.deployment.securityContext.runAsNonRoot }}
        runAsUser: {{ .Values.deployment.securityContext.runAsUser }}
        fsGroup: {{ .Values.deployment.securityContext.fsGroup }}

      topologySpreadConstraints:
        - maxSkew: {{ .Values.deployment.topologySpreadConstraints.maxSkew }}
          topologyKey: {{ .Values.deployment.topologySpreadConstraints.topologyKey }}
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: {{ .Values.deployment.labels.app }}

      containers:
        - name: {{ .Values.container.name }}
          image: {{ .Values.image.repository }}:{{ .Values.image.tag }}
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          envFrom:
{{ toYaml .Values.envFrom | indent 12 }}

          env:
{{ toYaml .Values.env | indent 12 }}

          ports:
            - containerPort: {{ .Values.ports.containerPort }}

          resources:
{{ toYaml .Values.resources | indent 12 }}

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
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
{{ toYaml .Values.containerSecurityContext | indent 12 }}
