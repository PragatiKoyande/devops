apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ .Values.name }}-deployment
  namespace: {{ .Values.namespace }}
  labels:
    app: {{ .Values.name }}-backend

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
      enableServiceLinks: false
      terminationGracePeriodSeconds: 30

      securityContext:
        runAsNonRoot: true
        runAsUser: {{ .Values.securityContext.runAsUser }}
        runAsGroup: {{ .Values.securityContext.runAsGroup }}
        fsGroup: {{ .Values.securityContext.fsGroup }}

      volumes:
        - name: tmp-dir
          emptyDir:
            medium: Memory
            sizeLimit: {{ .Values.volumes.tmp.sizeLimit }}

        - name: logs-volume
          emptyDir: {}

      containers:
        - name: {{ .Values.name }}-container
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          volumeMounts:
            - name: tmp-dir
              mountPath: {{ .Values.volumes.tmp.mountPath }}

            - name: logs-volume
              mountPath: {{ .Values.volumes.logs.mountPath }}

          ports:
            - containerPort: {{ .Values.service.targetPort }}

          envFrom:
            {{- range .Values.configMaps }}
            - configMapRef:
                name: {{ . }}
            {{- end }}
            {{- range .Values.secretRefs }}
            - secretRef:
                name: {{ . }}
            {{- end }}

          env:
            - name: SPRING_KAFKA_CONSUMER_GROUP_ID
              value: {{ .Values.env.SPRING_KAFKA_CONSUMER_GROUP_ID | quote }}

            - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
              value: {{ .Values.env.SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET | quote }}

          resources:
            requests:
              cpu: {{ .Values.resources.requests.cpu }}
              memory: {{ .Values.resources.requests.memory }}
            limits:
              cpu: {{ .Values.resources.limits.cpu }}
              memory: {{ .Values.resources.limits.memory }}

          startupProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            failureThreshold: 30
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 3

          readinessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 15
            periodSeconds: 5

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: {{ .Values.securityContext.readOnlyRootFilesystem }}
            capabilities:
              drop:
                - ALL