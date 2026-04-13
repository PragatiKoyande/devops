apiVersion: v1
kind: ServiceAccount
metadata:
  name: {{ include "common-master.fullname" . }}-sa
  namespace: {{ .Release.Namespace }}
automountServiceAccountToken: false