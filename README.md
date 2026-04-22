deployment.yaml:

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
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "{{ .Values.deployment.container.port }}"

    spec:
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
{{ toYaml .Values.deployment.securityContext | indent 8 }}

      hostAliases:
{{ toYaml .Values.deployment.hostAliases | indent 8 }}

      volumes:
{{ toYaml .Values.deployment.volumes | indent 8 }}

      containers:
        - name: {{ .Values.deployment.container.name }}
          image: {{ .Values.deployment.container.image }}
          imagePullPolicy: {{ .Values.deployment.container.imagePullPolicy }}

          ports:
            - containerPort: {{ .Values.deployment.container.port }}

          volumeMounts:
{{ toYaml .Values.deployment.container.volumeMounts | indent 12 }}

          env:
{{ toYaml .Values.deployment.container.env | indent 12 }}

          envFrom:
            {{- range .Values.deployment.container.envFrom.configMaps }}
            - configMapRef:
                name: {{ . }}
            {{- end }}
            {{- range .Values.deployment.container.envFrom.secrets }}
            - secretRef:
                name: {{ . }}
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

----------------------------------
  hpa.yaml:
  ----------------------------
    {{- if .Values.hpa }}
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

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: {{ .Values.hpa.cpuUtilization }}

  behavior:
    scaleUp:
      stabilizationWindowSeconds: {{ .Values.hpa.behavior.scaleUpStabilization }}
    scaleDown:
      stabilizationWindowSeconds: {{ .Values.hpa.behavior.scaleDownStabilization }}

{{- end }}

----------------------------------
  pdb.yaml:
  ----------------------------
  {{- if .Values.pdb.enabled }}
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ .Values.name }}-pdb
  namespace: {{ .Values.namespace }}
spec:
  minAvailable: {{ .Values.pdb.minAvailable }}
  selector:
    matchLabels:
      app: {{ .Values.name }}-backend
{{- end }}

----------------------------------
  service.yaml:
  ----------------------------
apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.service.name }}
  namespace: {{ .Values.namespace }}
spec:
  type: ClusterIP
  selector:
    app: {{ .Values.name }}-backend
  ports:
    - port: {{ .Values.service.port }}
      targetPort: {{ .Values.service.targetPort }}
      protocol: TCP

----------------------------------
  serviceaccount.yaml:
  ----------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: {{ .Values.serviceAccount.name }}
  namespace: {{ .Values.namespace }}


  Can you make my values.yaml for the above mentioned templates??
  
