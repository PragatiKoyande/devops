{{- define "common-master.name" -}}
common-master
{{- end }}

{{- define "common-master.fullname" -}}
{{ .Release.Name }}
{{- end }}