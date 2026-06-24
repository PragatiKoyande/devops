[root@fcuatgateway ~]# k get networkpolicy -A
NAMESPACE    NAME                      POD-SELECTOR        AGE
logging      loki-network-policy       app=loki            105d
uat-cbops1   allow-egress-to-redis     <none>              14d
uat-cbops1   allow-finny               <none>              2d
uat-cbops1   allow-kafka               app=login-backend   21h
uat-cbops1   allow-kafka-access        app=kafka           101m
uat-cbops1   allow-kafka-ingress       app=kafka           20h
uat-cbops1   allow-ldap-egress         app=login-backend   5d
uat-cbops1   allow-ldap-email-server   <none>              18d
uat-cbops1   allow-oracle-db-egress    <none>              15d
uat-cbops1   allow-redis-vector        <none>              47h
uat-cbops1   allow-sms-functionality   <none>              14d
[root@fcuatgateway ~]# k get pods -n uat-cbops1 --show-labels | grep kafka
kafka-0                                       1/1     Running            0                  7d2h    app=kafka,apps.kubernetes.io/pod-index=0,controller-revision-hash=kafka-8b75b5d7b,statefulset.kubernetes.io/pod-name=kafka-0
[root@fcuatgateway ~]# k get svc -n uat-cbops1 | grep kafka
kafka                                                    ClusterIP   None             <none>        9092/TCP,9093/TCP   170d
[root@fcuatgateway ~]# k describe networkpolicy allow-kafka-access -n uat-cbops1
Name:         allow-kafka-access
Namespace:    uat-cbops1
Created on:   2026-06-24 14:48:45 +0530 IST
Labels:       <none>
Annotations:  <none>
Spec:
  PodSelector:     app=kafka
  Allowing ingress traffic:
    To Port: 9092/TCP
    From:
      PodSelector: <none>
  Not affecting egress traffic
  Policy Types: Ingress
