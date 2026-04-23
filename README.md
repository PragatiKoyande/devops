namespace: backend

serviceAccount:
  name: report-sa

deployment:
  name: report-deployment

  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: report-backend

  container:
    name: report-container
    image: a2p05vksharbor.corp.ad.sbi/cbops/report-service:PR-09
    imagePullPolicy: Always

    port: 9005

    env:
      - name: SPRING_PROFILES_ACTIVE
        value: "prod"
      - name: HADOOP_FS_URI
        value: "hdfs://10.190.224.102:8022"
      - name: HADOOP_FS_USER
        value: "root"
      - name: JAVA_OPTS
        value: "-Xms16g -Xmx16g -XX:+UseG1GC -XX:MaxDirectMemorySize=6g"

    envFrom:
      configMaps:
        - redis-config
        - kafka-config
        - oracle-config
      secrets:
        - oracle-secret

    resources:
      requests:
        memory: "20Gi"
        cpu: "2000m"
      limits:
        memory: "24Gi"
        cpu: "4000m"

    probes:
      startup:
        port: 9005
        failureThreshold: 60
        periodSeconds: 10

      liveness:
        port: 9005
        initialDelaySeconds: 90
        periodSeconds: 15
        timeoutSeconds: 5
        failureThreshold: 5

      readiness:
        port: 9005
        initialDelaySeconds: 30
        periodSeconds: 10
        timeoutSeconds: 5
        failureThreshold: 5

    lifecycle:
      preStopSleep: 10

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

  hostAliases:
    - ip: "10.190.224.102"
      hostnames:
        - "fincore"
    - ip: "10.190.224.103"
      hostnames:
        - "fincore"
    - ip: "10.190.224.104"
      hostnames:
        - "fincore"
    - ip: "10.190.224.105"
      hostnames:
        - "fincore"
    - ip: "10.190.224.106"
      hostnames:
        - "fincore"

  topologySpreadConstraints:
    maxSkew: 1
    topologyKey: kubernetes.io/hostname

service:
  name: report-service
  type: ClusterIP
  port: 80
  targetPort: 9005

hpa:
  name: report-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70
  behavior:
    scaleUpStabilization: 60
    scaleDownStabilization: 300

pdb:
  name: report-pdb
  minAvailable: 1




  This is my values-prod.yaml file and my deployment file is slightly different i guess below i m pastiong that also: please correct the deployment file and send me back entite file

  apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Values.name }}-deployment
  namespace: {{ .Values.namespace }}

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
      app: {{ .Values.name }}-backend

  template:
    metadata:
      labels:
        app: {{ .Values.name }}-backend

    spec:
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      {{- if .Values.hostAliases }}
      hostAliases:
{{ toYaml .Values.hostAliases | indent 8 }}
      {{- end }}

      {{- if .Values.volumes }}
      volumes:
{{ toYaml .Values.volumes | indent 8 }}
      {{- end }}

      containers:
        - name: {{ .Values.name }}-container
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          ports:
            - containerPort: {{ .Values.service.targetPort }}

          {{- if .Values.volumeMounts }}
          volumeMounts:
{{ toYaml .Values.volumeMounts | indent 12 }}
          {{- end }}

          envFrom:
          {{- range .Values.envFrom.configMaps }}
            - configMapRef:
                name: {{ . }}
          {{- end }}
          {{- range .Values.envFrom.secrets }}
            - secretRef:
                name: {{ . }}
          {{- end }}

          {{- if or .Values.extraEnv .Values.secretEnv }}
          env:
          {{- if .Values.extraEnv }}
{{ toYaml .Values.extraEnv | indent 12 }}
          {{- end }}
          {{- range .Values.secretEnv }}
            - name: {{ .name }}
              valueFrom:
                secretKeyRef:
                  name: {{ .secretName }}
                  key: {{ .key }}
          {{- end }}
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
