[root@fcsitgateway SIT-Grafana]# kubectl describe cm fluent-bit-config -n tanzu-system-logging --kubeconfig h06vkssitcbopscls.conf
Name:         fluent-bit-config
Namespace:    tanzu-system-logging
Labels:       k8s-app=fluent-bit
              kapp.k14s.io/app=1774340937926061702
              kapp.k14s.io/association=v1.1eef7be45479a3b8c126212f0855b047
Annotations:  kapp.k14s.io/identity: v1;tanzu-system-logging//ConfigMap/fluent-bit-config;v1
              kapp.k14s.io/original:
                {"apiVersion":"v1","data":{"filters.conf":"[FILTER]\n  Name                kubernetes\n  Match               kube.*\n  Kube_URL           ...
              kapp.k14s.io/original-diff-md5: c6e94dc94aed3401b5d0f26ed6c0bff3

Data
====
inputs.conf:
----
[INPUT]
  Name                tail
  Path                /var/log/containers/*.log
  Parser              cri
  DB                  /var/log/flb_kube.db
  Tag                 kube.*
  Mem_Buf_Limit       50MB
  Skip_Long_Lines     On
  Refresh_Interval    10

[INPUT]
  Name                systemd
  Tag                 kube_systemd.*
  Path                /var/log/journal
  DB                  /var/log/flb_kube_systemd.db
  Systemd_Filter      _SYSTEMD_UNIT=kubelet.service
  Systemd_Filter      _SYSTEMD_UNIT=containerd.service
  Read_From_Tail      On
  Strip_Underscores   On

[INPUT]
  Name              tail
  Tag               apiserver_audit
  Path              /var/log/kubernetes/audit.log
  Parser            syslog
  DB                /var/log/flb_kube_audit.db
  Mem_Buf_Limit     50MB
  Refresh_Interval  10
  Skip_Long_Lines   On

[INPUT]
  Name                tail
  Tag                 audit.*
  Path                /var/log/audit/audit.log
  Parser              auditlog
  DB                  /var/log/flb_system_audit.db
  Mem_Buf_Limit       50MB
  Buffer_Chunk_Size   10MB
  Buffer_Max_Size     50MB
  Skip_Long_Lines     On
  Refresh_Interval    10

outputs.conf:
----
[OUTPUT]
  Name                 stdout
  Match                *

[OUTPUT]
  Name                 syslog
  Match                kube.*
  Host                 10.176.58.109
  Port                 514
  Mode                 tcp
  Syslog_Format        rfc5424
  Syslog_Hostname_key  tkg_cluster
  Syslog_Appname_key   pod_name
  Syslog_Procid_key    container_name
  Syslog_Message_key   message
  Syslog_SD_key        k8s
  Syslog_SD_key        labels
  Syslog_SD_key        annotations
  Syslog_SD_key        tkg
# Syslog - systemd

[OUTPUT]
  Name                  syslog
  Match                 kube.audit
  Host                  10.176.58.109
  Port                  514
  Mode                  tcp
  Syslog_Format         rfc5424
  Syslog_Hostname_key   node_name
  Syslog_Appname_key    kubernetes
  Syslog_Message_key    message

[OUTPUT]
  Name                  syslog
  Match                 audit.*
  Host                  10.176.58.109
  Port                  514
  Mode                  tcp
  Syslog_Format         rfc5424
  Syslog_Hostname_key   node_name
  Syslog_Appname_key    kubernetes
  Syslog_Message_key    message

[OUTPUT]
  Name                  syslog
  Match                 apiserver_audit
  Host                  10.176.58.109
  Port                  514
  Mode                  tcp
  Syslog_Format         rfc5424
  #Syslog_Hostname_key   host
  #Syslog_Appname_key    userAgent
  #Syslog_Procid_key     auditID
  Syslog_Message_key    log
  syslog_maxsize        8192

[OUTPUT]
  Name                  loki
  Match                 *
  Host                  loki.logging.svc.cluster.local
  Port                  3100
  uri                   /loki/api/v1/push
  labels                job=fluentbit
  label_keys            $kubernetes['namespace_name'],$kubernetes['pod_name'],$kubernetes['container_name']
  line_format           json

parsers.conf:
----
[PARSER]
  Name multiline
  Format regex
  Regex /(?<time>[A-Za-z]+ \d+ \d+\:\d+\:\d+)(?<message>.*)/
  Time_Key  time
  Time_Format %b %d %H:%M:%S
[PARSER]
  Name                  json
  Format                json
  Time_Key              time
  Time_Format           %d/%b/%Y:%H:%M:%S %z


[PARSER]
  Name                 logfmt
  Format               logfmt

[PARSER]
  Name                 auditlog
  Format               regex
  Regex                ^(type=\w+)\s+msg=audit\((\d+\.\d+:\d+)\):\s+(.*)
  Time_Key             timestamp
  Time_Format          %s.%L

[PARSER]
  Name                 docker
  Format               json
  Time_Key             time
  Time_Format          %Y-%m-%dT%H:%M:%S.%L
  Time_Keep            On

[PARSER]
  Name                 docker-daemon
  Format               regex
  Regex                time="(?<time>[^ ]*)" level=(?<level>[^ ]*) msg="(?<msg>[^ ].*)"
  Time_Key             time
  Time_Format          %Y-%m-%dT%H:%M:%S.%L
  Time_Keep            On

[PARSER]
  Name                 cri
  Format               regex
  Regex                ^(?<time>[^ ]+) (?<stream>stdout|stderr) (?<logtag>[^ ]*) (?<message>.*)$
  Time_Key             time
  Time_Format          %Y-%m-%dT%H:%M:%S.%L%z

[PARSER]
  Name   auditlog
  Format regex
  Regex  ^(type=\w+)\s+msg=audit\((\d+\.\d+:\d+)\):\s+(.*)
  Time_Key timestamp
  Time_Format %s.%L

[PARSER]
  Name        syslog
  Format      regex
  Regex       ^\<(?<pri>[0-9]+)\>(?<time>[^ ]* {1,2}[^ ]* [^ ]*) (?<host>[^ ]*) (?<ident>[a-zA-Z0-9_\/\.\-]*)(?:\[(?<pid>[0-9]+)\])?(?:[^\:]*\:)? *(?<message>.*)$
  Time_Key    time
  Time_Format %b %d %H:%M:%S

[PARSER]
  Name                 syslog-rfc5424
  Format               regex
  Regex                ^\<(?<pri>[0-9]{1,5})\>1 (?<time>[^ ]+) (?<host>[^ ]+) (?<ident>[^ ]+) (?<pid>[-0-9]+) (?<msgid>[^ ]+) (?<extradata>(\[(.*)\]|-)) (?<message>.+)$
  Time_Key             time
  Time_Format          %Y-%m-%dT%H:%M:%S.%L
  Time_Keep            On

[PARSER]
  Name                 kube-custom
  Format               regex
  Regex                (?<tag>[^.]+)?\.?(?<pod_name>[a-z0-9](?:[-a-z0-9]*[a-z0-9])?(?:\.[a-z0-9]([-a-z0-9]*[a-z0-9])?)*)_(?<namespace_name>[^_]+)_(?<container_name>.+)-(?<docker_id>[a-z0-9]{64})\.log$

plugins.conf:
----

streams.conf:
----

filters.conf:
----
[FILTER]
  Name                kubernetes
  Match               kube.*
  Kube_URL            https://kubernetes.default.svc:443
  Kube_CA_File        /var/run/secrets/kubernetes.io/serviceaccount/ca.crt
  Kube_Token_File     /var/run/secrets/kubernetes.io/serviceaccount/token
  Kube_Tag_Prefix     kube.var.log.containers.
  Merge_Log           On
  Merge_Log_Key       log_processed
  K8S-Logging.Parser  On
  K8S-Logging.Exclude On

[FILTER]
  Name                record_modifier
  Match               *
  Record tkg_instance h06vkspreprodscfucls
  Record tkg_cluster  h06vkspreprodscfucls

[FILTER]
  Name                record_modifier
  Match               apiserver_audit
  Record tkg_instance h06vkssitcbopscls
  Record tkg_cluster  h06vkssitcbopscls

[FILTER]
  Name        record_modifier
  Match       audit.*
  Record      node_name ${HOSTNAME}


[FILTER]
  Name                  modify
  Match                 kube.*
  Copy                  kubernetes k8s


[FILTER]
  Name                  nest
  Match                 kube.*
  Operation             lift
  Nested_Under          kubernetes

fluent-bit.conf:
----
[Service]
  Flush         1
  Log_Level     info
  Daemon        off
  Parsers_File  parsers.conf
  HTTP_Server   On
  HTTP_Listen   0.0.0.0
  HTTP_Port     2020
  HTTP_Listen   0.0.0.0
@INCLUDE inputs.conf
@INCLUDE filters.conf
@INCLUDE outputs.conf


BinaryData
====



this data i have
