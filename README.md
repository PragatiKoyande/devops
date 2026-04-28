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
      app: {{ .Values.labels.app }}

  template:
    metadata:
      labels:
        app: {{ .Values.labels.app }}

    spec:
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}
      enableServiceLinks: {{ .Values.deployment.enableServiceLinks }}

      {{- if .Values.hostAliases }}
      hostAliases:
{{ toYaml .Values.hostAliases | indent 8 }}
      {{- end }}

      securityContext:
{{ toYaml .Values.deployment.securityContext | indent 8 }}

      topologySpreadConstraints:
{{ toYaml .Values.deployment.topologySpreadConstraints | indent 8 }}

      containers:
        - name: {{ .Values.container.name }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.container.imagePullPolicy }}

          ports:
            - containerPort: {{ .Values.container.port }}

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
{{ toYaml .Values.env | indent 12 }}

          resources:
{{ toYaml .Values.resources | indent 12 }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
{{ toYaml .Values.probes.startup | indent 12 }}

          livenessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
{{ toYaml .Values.probes.liveness | indent 12 }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
{{ toYaml .Values.probes.readiness | indent 12 }}

          lifecycle:
            preStop:
              exec:
                command: {{ toJson .Values.lifecycle.preStop.command }}


_-------------


apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.service.name }}
  namespace: {{ .Values.namespace }}

spec:
  selector:
    app: {{ .Values.labels.app }}

  ports:
    - port: {{ .Values.service.port }}
      targetPort: {{ .Values.service.targetPort }}

  type: ClusterIP


-----------------

apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: {{ .Values.hpa.name }}
  namespace: {{ .Values.namespace }}

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: {{ .Values.deployment.name }}

  minReplicas: {{ .Values.hpa.minReplicas }}
  maxReplicas: {{ .Values.hpa.maxReplicas }}

  behavior:
{{ toYaml .Values.hpa.behavior | indent 4 }}

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: {{ .Values.hpa.cpu }}


---------

apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ .Values.pdb.name }}
  namespace: {{ .Values.namespace }}

spec:
  minAvailable: {{ .Values.pdb.minAvailable }}

  selector:
    matchLabels:
      app: {{ .Values.labels.app }}


--------

apiVersion: v1
kind: ServiceAccount
metadata:
  name: {{ .Values.serviceAccount.name }}
  namespace: {{ .Values.namespace }}