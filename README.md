apiVersion: v1
kind: Service
metadata:
  name: {{ include "common-master.fullname" . }}
  namespace: {{ .Release.Namespace }}

spec:
  type: ClusterIP

  selector:
    app: {{ include "common-master.name" . }}

  ports:
    - name: http
      port: 80
      targetPort: {{ .Values.service.targetPort }}
      protocol: TCP