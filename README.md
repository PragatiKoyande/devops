[root@fcsitgateway ~]# k exec -it grafana-758f498965-w9p8m -- sh
/usr/share/grafana $ curl http://loki:3100/ready
curl: (6) Could not resolve host: loki
/usr/share/grafana $ exit
command terminated with exit code 6
[root@fcsitgateway ~]# k get pods -A | grep grafana
cbops                          grafana-758f498965-w9p8m                                1/1     Running             0                19d
[root@fcsitgateway ~]# k get svc | grep loki
[root@fcsitgateway ~]# k get svc -A | grep loki
logging                   loki                                ClusterIP      10.104.67.221    <none>           3100/TCP                     108d
[root@fcsitgateway ~]# k exec -it grafana-758f498965-w9p8m -- sh
/usr/share/grafana $ curl http://loki.logging.svc.cluster.local:3100/ready
^X^Z[1]+  Stopped                    curl http://loki.logging.svc.cluster.local:3100/ready
/usr/share/grafana $ cat /etc/resolv.conf
search cbops.svc.cluster.local svc.cluster.local cluster.local
nameserver 10.96.0.10
options ndots:5
/usr/share/grafana $ nslookup kubernetes.default.svc.cluster.local
Server:         10.96.0.10
Address:        10.96.0.10:53

Name:   kubernetes.default.svc.cluster.local
Address: 10.96.0.1
