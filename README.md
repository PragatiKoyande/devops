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
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
{{ toYaml .Values.deployment.securityContext | indent 8 }}

      {{- if .Values.deployment.hostAliases }}
      hostAliases:
{{ toYaml .Values.deployment.hostAliases | indent 8 }}
      {{- end }}

      {{- if .Values.deployment.volumes }}
      volumes:
{{ toYaml .Values.deployment.volumes | indent 8 }}
      {{- end }}

      containers:
        - name: {{ .Values.deployment.container.name }}
          image: {{ .Values.deployment.container.image }}
          imagePullPolicy: {{ .Values.deployment.container.imagePullPolicy }}

          ports:
            - containerPort: {{ .Values.deployment.container.port }}

          {{- if .Values.deployment.container.volumeMounts }}
          volumeMounts:
{{ toYaml .Values.deployment.container.volumeMounts | indent 12 }}
          {{- end }}

          {{- if .Values.deployment.container.env }}
          env:
{{ toYaml .Values.deployment.container.env | indent 12 }}
          {{- end }}

          {{- if .Values.deployment.container.envFrom }}
          envFrom:
            {{- range .Values.deployment.container.envFrom.configMaps }}
            - configMapRef:
                name: {{ . }}
            {{- end }}
            {{- range .Values.deployment.container.envFrom.secrets }}
            - secretRef:
                name: {{ . }}
            {{- end }}
          {{- end }}

          resources:
{{ toYaml .Values.deployment.container.resources | indent 12 }}

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

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep {{ .Values.deployment.container.lifecycle.preStopSleep }}"]

This is my deployment.yaml file and below is my values.yaml file: is not aligned with my deployment file and hence it is throwing issue so can you please make necessary chnages in values.yaml file and sen dme back entie

name: report
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/report-service
  tag: DEV16
  pullPolicy: Always

serviceAccount:
  name: report-sa

service:
  name: report-service
  port: 80
  targetPort: 9005

autoscaling:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

pdb:
  enabled: true
  minAvailable: 1

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

envFrom:
  configMaps:
    - redis-config
    - oracle-config
    - kafka-config
  secrets:
    - oracle-secret

extraEnv:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

secretEnv: []

hostAliases: []
volumes: []
volumeMounts: []


                
