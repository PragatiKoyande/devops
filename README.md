apiVersion: v1
kind: ServiceAccount
metadata:
  name: process-status-sa
  namespace: {{ .Values.namespace }}
automountServiceAccountToken: false