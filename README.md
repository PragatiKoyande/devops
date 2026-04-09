apiVersion: v1
kind: ServiceAccount
metadata:
  name: {{ ( .Values.serviceAccount | default dict ).name | default "user-sa" }}
  namespace: {{ .Values.namespace | default "backend" }}