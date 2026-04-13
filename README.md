apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ include "common-master.fullname" . }}-pdb
  namespace: {{ .Release.Namespace }}

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: {{ include "common-master.name" . }}