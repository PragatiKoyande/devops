[root@fcsitgateway SIT-Microservice]# k get svc postgres-db -n cbops -o wide
NAME          TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)    AGE    SELECTOR
postgres-db   ClusterIP   10.107.5.121   <none>        5432/TCP   177d   app=postgres-db
[root@fcsitgateway SIT-Microservice]# k get endpoints postgres-db -n cbops -o wide
NAME          ENDPOINTS           AGE
postgres-db   192.168.8.21:5432   177d
[root@fcsitgateway SIT-Microservice]# k describe netpol allow-postgres-egress -n egress
Error from server (NotFound): namespaces "egress" not found
[root@fcsitgateway SIT-Microservice]# k describe netpol allow-postgres-egress -n cbops
Name:         allow-postgres-egress
Namespace:    cbops
Created on:   2026-06-25 14:38:34 +0530 IST
Labels:       <none>
Annotations:  <none>
Spec:
  PodSelector:     <none> (Allowing the specific traffic to all pods in this namespace)
  Not affecting ingress traffic
  Allowing egress traffic:
    To Port: 5432/TCP
    To:
      IPBlock:
        CIDR: 10.177.179.51/32
        Except:
  Policy Types: Egress
