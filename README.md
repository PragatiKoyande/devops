apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Values.deployment.name }}
  namespace: {{ .Values.namespace }}
  labels:
    app: {{ .Values.labels.app }}

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
      serviceAccountName: {{ .Values.deployment.serviceAccountName }}
      enableServiceLinks: {{ .Values.deployment.enableServiceLinks }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}

      securityContext:
        {{- toYaml .Values.deployment.securityContext | nindent 8 }}

      volumes:
        {{- toYaml .Values.deployment.volumes | nindent 8 }}

      containers:
        - name: {{ .Values.container.name }}
          image: {{ .Values.image.repository }}:{{ .Values.image.tag }}
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          ports:
            - containerPort: {{ .Values.probes.port }}

          volumeMounts:
            {{- toYaml .Values.volumeMounts | nindent 12 }}

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
            {{- toYaml .Values.env | nindent 12 }}

          resources:
            {{- toYaml .Values.resources | nindent 12 }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            {{- toYaml .Values.probes.startup | nindent 12 }}

          livenessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            {{- toYaml .Values.probes.liveness | nindent 12 }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.probes.port }}
            {{- toYaml .Values.probes.readiness | nindent 12 }}

          lifecycle:
            preStop:
              exec:
                command: {{ toJson .Values.lifecycle.preStop.command }}

          securityContext:
            {{- toYaml .Values.containerSecurityContext | nindent 12 }}




namespace: backend

serviceAccount:
  name: notification-sa

deployment:
  name: notification-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: notification-backend

  serviceAccountName: notification-sa
  enableServiceLinks: false
  terminationGracePeriodSeconds: 30

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

  volumes:
    - name: tmp-dir
      emptyDir:
        medium: Memory
        sizeLimit: 64Mi

container:
  name: notification-container

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/notification-service
  tag: TEST-1
  pullPolicy: Always

service:
  name: notification-service
  type: ClusterIP
  port: 80
  targetPort: 9010

probes:
  port: 9010

  startup:
    failureThreshold: 30
    periodSeconds: 10

  liveness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 3

  readiness:
    initialDelaySeconds: 15
    periodSeconds: 5

resources:
  requests:
    cpu: "200m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

volumeMounts:
  - name: tmp-dir
    mountPath: /tmp

envFrom:
  configMaps:
    - postgres-config
    - redis-config
    - kafka-config
  secrets:
    - postgres-secret

env:
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "notification-service-group"
  - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
    value: "earliest"
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

lifecycle:
  preStop:
    command: ["/bin/sh","-c","sleep 10"]

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: true
  capabilities:
    drop:
      - ALL

hpa:
  name: notification-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70

pdb:
  name: notification-pdb
  minAvailable: 1

labels:
  app: notification-backend
