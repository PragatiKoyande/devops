{job="fluentbit"} 
| json 
| pod_name="react-app-deployment-867f4c884f-nvvpd"
| json 
| line_format "{{.level}} {{.msg}}"