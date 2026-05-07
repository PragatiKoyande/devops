I want to add like this in my configuration:

secretEnv:
  - name: LDAP_TRUSTSTORE_PASSWORD
    secretName: ldap-creds
    key: truststore-password



I am sending the entire values and deployment file sso you can add above configs and send me back

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

    spec:
      serviceAccountName: {{ .Values.deployment.pod.serviceAccountName }}
      terminationGracePeriodSeconds: {{ .Values.deployment.pod.terminationGracePeriodSeconds }}
      enableServiceLinks: {{ .Values.deployment.pod.enableServiceLinks }}

      securityContext:
        runAsNonRoot: {{ .Values.deployment.pod.securityContext.runAsNonRoot }}
        runAsUser: {{ .Values.deployment.pod.securityContext.runAsUser }}
        fsGroup: {{ .Values.deployment.pod.securityContext.fsGroup }}

      {{- if .Values.hostAliases }}
      hostAliases:
        {{- toYaml .Values.hostAliases | nindent 8 }}
      {{- end }}

      {{- if .Values.deployment.pod.volumes }}
      volumes:
        {{- toYaml .Values.deployment.pod.volumes | nindent 8 }}
      {{- end }}

      containers:
        - name: {{ .Values.container.name }}
          image: {{ .Values.image.repository }}:{{ .Values.image.tag }}
          imagePullPolicy: Always

          ports:
            - containerPort: {{ .Values.ports.containerPort }}

          {{- if .Values.volumeMounts }}
          volumeMounts:
            {{- toYaml .Values.volumeMounts | nindent 12 }}
          {{- end }}

          {{- if .Values.envFrom }}
          envFrom:
            {{- range .Values.envFrom.configMaps }}
            - configMapRef:
                name: {{ . }}
            {{- end }}
            {{- range .Values.envFrom.secrets }}
            - secretRef:
                name: {{ . }}
            {{- end }}
          {{- end }}

          {{- if .Values.env }}
          env:
            {{- toYaml .Values.env | nindent 12 }}
          {{- end }}

          resources:
            {{- toYaml .Values.resources | nindent 12 }}

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
                command: {{ toYaml .Values.lifecycle.preStop.command | nindent 18 }}

          securityContext:
            allowPrivilegeEscalation: {{ .Values.securityContext.allowPrivilegeEscalation }}
            readOnlyRootFilesystem: {{ .Values.securityContext.readOnlyRootFilesystem }}
            capabilities:
              drop:
                {{- toYaml .Values.securityContext.capabilities.drop | nindent 16 }}



  values.yaml:

  namespace: backend

serviceAccount:
  name: login-sa
  automountServiceAccountToken: false

deployment:
  name: login-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: login-backend

  pod:
    serviceAccountName: login-sa
    terminationGracePeriodSeconds: 30
    enableServiceLinks: false

    securityContext:
      runAsNonRoot: true
      runAsUser: 10001
      fsGroup: 10001

    hostAliases: []   # overridden per env

    volumes:
      - name: truststore-volume
        secret:
          secretName: ldap-truststore-file
          items:
            - key: ad-truststore.jks
              path: ad-truststore.jks

      - name: logs-volume
        emptyDir: {}

container:
  name: login-backend-container

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/login-service
  tag: DEV13

ports:
  containerPort: 8085

volumeMounts:
  - name: truststore-volume
    mountPath: /etc/fincore/secrets
    readOnly: true
  - name: logs-volume
    mountPath: /logs

env:
  - name: SPRING_PROFILES_ACTIVE
    value: "dev"

envFrom:
  configMaps:
    - redis-config
    - oracle-config
    - ldap-config
  secrets:
    - oracle-secret

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

probes:
  port: 8085

  readiness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 5

  liveness:
    initialDelaySeconds: 90
    periodSeconds: 15
    timeoutSeconds: 5
    failureThreshold: 5

  startup:
    failureThreshold: 60
    periodSeconds: 10

lifecycle:
  preStop:
    command: ["/bin/sh", "-c", "sleep 10"]

securityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: false
  capabilities:
    drop:
      - ALL

service:
  name: login-service
  port: 80
  targetPort: 8085

hpa:
  name: login-hpa
  minReplicas: 1
  maxReplicas: 3
  cpuUtilization: 70

pdb:
  name: login-pdb
  minAvailable: 1
