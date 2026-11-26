[root@fcppjump PRE-PROD-Microservices]# k get cm config-postgres  -o yaml
apiVersion: v1
data:
  PSQL_SPRING_DATASOURCE_DRIVER_CLASS_NAME: org.postgresql.Driver
  PSQL_SPRING_DATASOURCE_URL: jdbc:postgresql://10.177.179.164:8480/fincore
  PSQL_SPRING_DATASOURCE_USERNAME: fcdev
  SPRING_JPA_PROPERTIES_HIBERNATE_DIALECT: org.hibernate.dialect.PostgreSQLDialect
kind: ConfigMap
metadata:
  creationTimestamp: "2026-11-26T09:18:17Z"
  name: config-postgres
  namespace: backend
  resourceVersion: "121661942"
  uid: 3d5fdf82-7fa2-4eb6-a7af-9f0eb7812bd4
[root@fcppjump PRE-PROD-Microservices]# k get secret secret-postgres -n backend -o go-template='{{range $k,$v := .data}}{{printf "%s\n" $k}}{{end}}'
PSQL_SPRING_DATASOURCE_PASSWORD
[root@fcppjump PRE-PROD-Microservices]# k get pods -n backend  -l app=notification-backend
NAME                                       READY   STATUS             RESTARTS      AGE
notification-deployment-686994d545-lnmlx   0/1     CrashLoopBackOff   6 (30s ago)   6m55s
