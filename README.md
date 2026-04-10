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
        runAsUser: 10001
        fsGroup: 10001

      hostAliases:
        {{- range .Values.hostAliases }}
        - ip: {{ .ip | quote }}
          hostnames:
            {{- range .hostnames }}
            - {{ . | quote }}
            {{- end }}
        {{- end }}

      volumes:
        - name: truststore-volume
          secret:
            secretName: {{ .Values.volumes.truststore.secretName }}
            items:
              - key: {{ .Values.volumes.truststore.fileName }}
                path: {{ .Values.volumes.truststore.fileName }}

        - name: logs-volume
          emptyDir: {}

      containers:
        - name: {{ .Values.name }}-container
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          imagePullPolicy: {{ .Values.image.pullPolicy }}

          ports:
            - containerPort: {{ .Values.service.targetPort }}

          volumeMounts:
            - name: truststore-volume
              mountPath: {{ .Values.volumes.truststore.mountPath }}
              readOnly: true

            - name: logs-volume
              mountPath: {{ .Values.volumes.logs.mountPath }}

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
            - name: SPRING_PROFILES_ACTIVE
              value: {{ .Values.env.SPRING_PROFILES_ACTIVE | quote }}

            - name: JAVA_TOOL_OPTIONS
              value: {{ .Values.env.JAVA_TOOL_OPTIONS | quote }}

            - name: LDAP_TRUSTSTORE_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: {{ .Values.extraSecrets.ldapCreds.name }}
                  key: {{ .Values.extraSecrets.ldapCreds.key }}

          resources:
            requests:
              cpu: {{ .Values.resources.requests.cpu }}
              memory: {{ .Values.resources.requests.memory }}
            limits:
              cpu: {{ .Values.resources.limits.cpu }}
              memory: {{ .Values.resources.limits.memory }}

          readinessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

          livenessProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          startupProbe:
            tcpSocket:
              port: {{ .Values.service.targetPort }}
            failureThreshold: 60
            periodSeconds: 10

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: false
            capabilities:
              drop:
                - ALL