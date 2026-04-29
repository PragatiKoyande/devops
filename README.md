apiVersion: v1
kind: ServiceAccount
metadata:
  name: {{ .Values.serviceAccount.name }}
  namespace: {{ .Values.namespace }}



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
      serviceAccountName: {{ .Values.deployment.serviceAccountName }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}
      enableServiceLinks: {{ .Values.deployment.enableServiceLinks }}

      securityContext:
{{ toYaml .Values.deployment.securityContext | indent 8 }}

      topologySpreadConstraints:
{{ toYaml .Values.deployment.topologySpreadConstraints | indent 8 }}

      volumes:
{{ toYaml .Values.deployment.volumes | indent 8 }}

      containers:
        - name: {{ .Values.container.name }}
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.imagePullPolicy }}

          securityContext:
{{ toYaml .Values.containerSecurityContext | indent 12 }}

          volumeMounts:
{{ toYaml .Values.deployment.volumeMounts | indent 12 }}

          envFrom:
{{ toYaml .Values.envFrom | indent 12 }}

          ports:
            - containerPort: {{ .Values.container.port }}

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



apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.service.name }}
  namespace: {{ .Values.namespace }}

spec:
  selector:
    app: {{ .Values.deployment.labels.app }}

  ports:
    - name: http
      protocol: TCP
      port: {{ .Values.service.port }}
      targetPort: {{ .Values.service.targetPort }}

  type: {{ .Values.service.type }}




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
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: {{ .Values.hpa.cpuUtilization }}


apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ .Values.pdb.name }}
  namespace: {{ .Values.namespace }}

spec:
  minAvailable: {{ .Values.pdb.minAvailable }}
  selector:
    matchLabels:
      app: {{ .Values.deployment.labels.app }}



