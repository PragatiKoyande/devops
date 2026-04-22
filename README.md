D:\Pragati\HELM-Latest-0904\Deployment>cd nwsa-variance

D:\Pragati\HELM-Latest-0904\Deployment\nwsa-variance>helm template nwsa-variance-dev . -f values.yaml -n backend --kubeconfig h06vksuatcbopscls.conf
Error: nwsa-variance-service/templates/deployment.yaml:42:26
  executing "nwsa-variance-service/templates/deployment.yaml" at <.Values.container.name>:
    nil pointer evaluating interface {}.name


This issue I m getting and below is my deploymnet file:

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
