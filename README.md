behavior:
  scaleUp:
    stabilizationWindowSeconds: {{ .Values.hpa.behavior.scaleUp }}
  scaleDown:
    stabilizationWindowSeconds: {{ .Values.hpa.behavior.scaleDown }}