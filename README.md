apiVersion: v1
kind: ConfigMap
metadata:
  name: fluent-bit-config
  namespace: logging
data:
  fluent-bit.conf: |
    [SERVICE]
        Flush        1
        Log_Level    info
        Parsers_File parsers.conf

    @INCLUDE input-kubernetes.conf
    @INCLUDE filter-kubernetes.conf
    @INCLUDE output-loki.conf

  input-kubernetes.conf: |
    [INPUT]
        Name              tail
        Path              /var/log/containers/*.log
        Tag               kube.*
        Parser            docker
        Refresh_Interval  1
        Rotate_Wait       30
        Mem_Buf_Limit     100MB
        Skip_Long_Lines   On
        DB                /var/log/flb_kube.db

  filter-kubernetes.conf: |
    [FILTER]
        Name                kubernetes
        Match               kube.*
        Kube_Tag_Prefix     kube.var.log.containers.
        Merge_Log           On
        Keep_Log            Off
        Labels              Off
        Annotations         Off
        K8S-Logging.Parser  On
        K8S-Logging.Exclude Off

  output-loki.conf: |
    [OUTPUT]
       Name                  loki
       Match                 *
       Host                  loki.logging.svc.cluster.local
       Port                  3100
       Uri                   /loki/api/v1/push
       Labels                job=fluentbit,namespace=$kubernetes['namespace_name'],pod=$kubernetes['pod_name'],container=$kubernetes['container_name']
       LabelKeys             namespace,pod,container
       LabelMapPath          /fluent-bit/etc/kubernetes_labels.LabelMapPath
       AutoKubernetesLabels  On
       LineFormat            json


  parsers.conf: |
    [PARSER]
        Name        docker
        Format      json
        Time_Key    time
        Time_Format %Y-%m-%dT%H:%M:%S.%L

This is my Fluent-bit OUTPUT file please correct it I wanted to see labels in this fashion:


Label browser

1. Select labels to search in
Which labels would you like to consider for your search?
container
job
namespace
pod
