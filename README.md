this is my deployment.yaml file:

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


-------------------------
my values-deafult.yaml file is diffenet and rherefore its not running fine so i m pasting my values.yaml file can you please make my values-dfault fine correct aligning with above deployment.yaml:
------------------------------------------------

name: user
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service
  tag: DEV06
  pullPolicy: Always

serviceAccount:
  name: user-sa

service:
  name: user-service
  port: 80
  targetPort: 8087

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
    - oracle-config
    - kafka-config
    - redis-config
    - ldap-config
  secrets:
    - oracle-secret

extraEnv:
  - name: SPRING_PROFILES_ACTIVE
    value: dev
  - name: JAVA_TOOL_OPTIONS
    value: "-Djava.net.preferIPv4Stack=true"
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "rbac-cache-group"

secretEnv:
  - name: LDAP_TRUSTSTORE_PASSWORD
    secretName: ldap-creds
    key: truststore-password

hostAliases:
  - ip: "10.189.42.83"
    hostnames:
      - "uatrootdc1.uatad.sbi"

volumes:
  - name: truststore-volume
    secret:
      secretName: ldap-truststore-file
      items:
        - key: ad-truststore.jks
          path: ad-truststore.jks

volumeMounts:
  - name: truststore-volume
    mountPath: /etc/fincore/secrets
    readOnly: true


    
