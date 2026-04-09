apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: user-pdb
  namespace: {{ .Values.namespace }}

spec:
  minAvailable: {{ .Values.pdb.minAvailable }}
  selector:
    matchLabels:
      app: user-backend