apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ include "common-master.fullname" . }}
  namespace: {{ .Release.Namespace }}

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
      app: {{ include "common-master.name" . }}

  template:
    metadata:
      labels:
        app: {{ include "common-master.name" . }}

    spec:
      serviceAccountName: {{ include "common-master.fullname" . }}-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
{{ toYaml .Values.securityContext | indent 8 }}

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: {{ include "common-master.name" . }}

      containers:
        - name: common-master-container
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: Always

          ports:
            - containerPort: {{ .Values.service.targetPort }}

          envFrom:
{{- range .Values.envFrom.configMaps }}
            - configMapRef:
                name: {{ . }}
{{- end }}
{{- range .Values.envFrom.secrets }}
            - secretRef:
                name: {{ . }}
{{- end }}

          resources:
{{ toYaml .Values.resources | indent 12 }}

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
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: false
            capabilities:
              drop:
                - ALL