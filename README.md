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
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: {{ .Values.deployment.strategy.maxUnavailable }}
      maxSurge: {{ .Values.deployment.strategy.maxSurge }}

  selector:
    matchLabels:
      app: {{ .Values.deployment.app }}

  template:
    metadata:
      labels:
        app: {{ .Values.deployment.app }}
      annotations:
        prometheus.io/scrape: "{{ .Values.deployment.annotations.scrape }}"
        prometheus.io/port: "{{ .Values.deployment.annotations.port }}"

    spec:
      serviceAccountName: {{ .Values.serviceAccount.name }}
      terminationGracePeriodSeconds: {{ .Values.deployment.terminationGracePeriodSeconds }}
      enableServiceLinks: {{ .Values.deployment.enableServiceLinks }}

      hostAliases:
{{ toYaml .Values.deployment.hostAliases | indent 6 }}

      topologySpreadConstraints:
{{ toYaml .Values.deployment.topologySpreadConstraints | indent 6 }}

      containers:
        - name: {{ .Values.container.name }}
          image: {{ .Values.container.image }}
          imagePullPolicy: {{ .Values.container.imagePullPolicy }}

          envFrom:
{{ toYaml .Values.container.envFrom | indent 12 }}

          env:
{{ toYaml .Values.container.env | indent 12 }}

          ports:
            - containerPort: {{ .Values.container.port }}

          resources:
{{ toYaml .Values.container.resources | indent 12 }}

          startupProbe:
{{ toYaml .Values.container.startupProbe | indent 12 }}

          livenessProbe:
{{ toYaml .Values.container.livenessProbe | indent 12 }}

          readinessProbe:
{{ toYaml .Values.container.readinessProbe | indent 12 }}

          lifecycle:
{{ toYaml .Values.container.lifecycle | indent 12 }}





apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.service.name }}
  namespace: {{ .Values.namespace }}

spec:
  selector:
    app: {{ .Values.service.selector }}

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
{{ toYaml .Values.hpa.behavior | indent 4 }}

  metrics:
{{ toYaml .Values.hpa.metrics | indent 4 }}



apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ .Values.pdb.name }}
  namespace: {{ .Values.namespace }}

spec:
  minAvailable: {{ .Values.pdb.minAvailable }}
  selector:
    matchLabels:
      app: {{ .Values.pdb.app }}


apiVersion: v2
name: nwsa-variance-service
description: Helm chart for NWSA Variance Service
type: application
version: 0.1.0
appVersion: "1.0"




namespace: backend

serviceAccount:
  name: nwsa-sa

deployment:
  name: nwsa-variance-deployment
  replicas: 2
  revisionHistoryLimit: 5

  strategy:
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: nwsa-variance-backend

  annotations:
    prometheus:
      scrape: "true"
      port: "8093"

  container:
    name: nwsa-variance-container
    image: a2p05vksharbor.corp.ad.sbi/cbops/nwsa-variance-service:PR-03
    imagePullPolicy: Always
    port: 8093

    env:
      - name: SPRING_PROFILES_ACTIVE
        value: "prod"
      - name: HADOOP_FS_HA_NN1
        value: "hdfs://10.190.224.102:8022"
      - name: HADOOP_FS_HA_NN2
        value: "hdfs://10.190.224.103:8022"
      - name: HADOOP_FS_HA_NN3
        value: "hdfs://10.190.224.104:8022"
      - name: HADOOP_FS_HA_NN4
        value: "hdfs://10.190.224.105:8022"
      - name: HADOOP_FS_HA_NN5
        value: "hdfs://10.190.224.106:8022"
      - name: NWSA_GENERATED_REPORT_ROOT
        value: "/reports"
      - name: NWSA_REPORT_ROOT
        value: "/reports"
      - name: HADOOP_FS_URI
        value: "hdfs://fincore:8022"
      - name: HADOOP_FS_USER
        value: "root"

    envFrom:
      configMaps:
        - redis-config
        - kafka-config
        - oracle-config
      secrets:
        - oracle-secret

    resources:
      requests:
        cpu: "200m"
        memory: "256Mi"
      limits:
        cpu: "500m"
        memory: "512Mi"

    probes:
      startup:
        port: 8093
        failureThreshold: 30
        periodSeconds: 10
      liveness:
        port: 8093
        initialDelaySeconds: 30
        periodSeconds: 10
        timeoutSeconds: 3
        failureThreshold: 3
      readiness:
        port: 8093
        initialDelaySeconds: 15
        periodSeconds: 5
        timeoutSeconds: 3
        failureThreshold: 3

    lifecycle:
      preStopSleep: 10

  hostAliases:
    - ip: "10.190.224.102"
      hostnames: ["fincore"]
    - ip: "10.190.224.103"
      hostnames: ["fincore"]
    - ip: "10.190.224.104"
      hostnames: ["fincore"]
    - ip: "10.190.224.105"
      hostnames: ["fincore"]
    - ip: "10.190.224.106"
      hostnames: ["fincore"]

  topologySpreadConstraints:
    maxSkew: 1
    topologyKey: kubernetes.io/hostname

service:
  name: nwsa-variance-service
  port: 80
  targetPort: 8093

hpa:
  name: nwsa-variance-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70
  behavior:
    scaleUp: 60
    scaleDown: 300

pdb:
  name: nwsa-variance-pdb
  minAvailable: 1



# DEV
helm install nwsa-dev . -f values-dev.yaml -n backend

# SIT
helm install nwsa-sit . -f values-sit.yaml -n backend

# UAT
helm install nwsa-uat . -f values-uat.yaml -n backend

# PROD
helm install nwsa-prod . -f values-prod.yaml -n backend
