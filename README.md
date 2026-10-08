[root@fcuatgateway ENV-Changes]# k get deployment communication-deployment -o yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  annotations:
    deployment.kubernetes.io/revision: "61"
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"apps/v1","kind":"Deployment","metadata":{"annotations":{},"name":"communication-deployment","namespace":"uat-cbops1"},"spec":{"replicas":1,"selector":{"matchLabels":{"app":"communication-backend"}},"template":{"metadata":{"labels":{"app":"communication-backend"}},"spec":{"containers":[{"env":[{"name":"SPRING_PROFILES_ACTIVE","value":"uat"},{"name":"SPRING_KAFKA_CONSUMER_GROUP_ID","value":"communication-login-otp-group-v7"},{"name":"SPRING_KAFKA_ADMIN_PROPERTIES_REQUEST_TIMEOUT_MS","value":"60000"},{"name":"SPRING_KAFKA_PROPERTIES_SOCKET_CONNECTION_SETUP_TIMEOUT_MS","value":"30000"},{"name":"SPRING_KAFKA_ADMIN_AUTO_CREATE","value":"false"},{"name":"REPORT_SERVICE_URL","value":"report-service.uat-cbops1.svc.cluster.local:80"}],"envFrom":[{"configMapRef":{"name":"config-oracle"}},{"configMapRef":{"name":"config-kafka"}},{"configMapRef":{"name":"config-redis"}},{"secretRef":{"name":"oracle-secret"}},{"secretRef":{"name":"jwt-secret"}},{"secretRef":{"name":"kafka-aes-secret"}},{"secretRef":{"name":"rsa-private-secret"}},{"secretRef":{"name":"rsa-public-secret"}}],"image":"h06vksharbor.corp.ad.sbi/cbops/communication-service:UAT29","imagePullPolicy":"Always","name":"communication-container","ports":[{"containerPort":8001}]}]}}}}
    kubernetes.io/change-cause: kubectl set image deployment/communication-deployment
      communication-container=h06vksharbor.corp.ad.sbi/cbops/communication-service:UAT23
      --namespace=uat-cbops1 --record=true
  creationTimestamp: "2026-06-17T11:38:23Z"
  generation: 62
  name: communication-deployment
  namespace: uat-cbops1
  resourceVersion: "127247688"
  uid: 87fa5a9b-b439-4a21-9b49-3831a1b9f0c8
spec:
  progressDeadlineSeconds: 600
  replicas: 1
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: communication-backend
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      annotations:
        kubectl.kubernetes.io/restartedAt: "2026-09-29T16:32:09+05:30"
      creationTimestamp: null
      labels:
        app: communication-backend
    spec:
      containers:
      - env:
        - name: SPRING_PROFILES_ACTIVE
          value: uat
        - name: SPRING_KAFKA_CONSUMER_GROUP_ID
          value: communication-login-otp-group-v7
        - name: SPRING_KAFKA_ADMIN_PROPERTIES_REQUEST_TIMEOUT_MS
          value: "60000"
        - name: SPRING_KAFKA_PROPERTIES_SOCKET_CONNECTION_SETUP_TIMEOUT_MS
          value: "30000"
        - name: SPRING_KAFKA_ADMIN_AUTO_CREATE
          value: "false"
        - name: REPORT_SERVICE_URL
          value: report-service.uat-cbops1.svc.cluster.local:80
        envFrom:
        - configMapRef:
            name: config-oracle
        - configMapRef:
            name: config-kafka
        - configMapRef:
            name: config-redis
        - secretRef:
            name: oracle-secret
        - secretRef:
            name: jwt-secret
        - secretRef:
            name: kafka-aes-secret
        - secretRef:
            name: rsa-private-secret
        - secretRef:
            name: rsa-public-secret
        image: h06vksharbor.corp.ad.sbi/cbops/communication-service:UAT29
        imagePullPolicy: Always
        name: communication-container
        ports:
        - containerPort: 8001
          protocol: TCP
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
      dnsPolicy: ClusterFirst
      restartPolicy: Always
      schedulerName: default-scheduler
      securityContext: {}
      terminationGracePeriodSeconds: 30
status:
  conditions:
  - lastTransitionTime: "2026-09-16T08:25:45Z"
    lastUpdateTime: "2026-10-08T08:55:42Z"
    message: ReplicaSet "communication-deployment-6b85cdf6b8" has successfully progressed.
    reason: NewReplicaSetAvailable
    status: "True"
    type: Progressing
  - lastTransitionTime: "2026-10-08T08:59:49Z"
    lastUpdateTime: "2026-10-08T08:59:49Z"
    message: Deployment does not have minimum availability.
    reason: MinimumReplicasUnavailable
    status: "False"
    type: Available
  observedGeneration: 62
  replicas: 1
  unavailableReplicas: 1
  updatedReplicas: 1
[root@fcuatgateway ENV-Changes]# k get secret
NAME                                   TYPE                 DATA   AGE
airflow-api-secret-key                 Opaque               1      201d
airflow-broker-url                     Opaque               1      201d
airflow-fernet-key                     Opaque               1      201d
airflow-jwt-secret                     Opaque               1      201d
airflow-metadata                       Opaque               1      201d
airflow-redis-password                 Opaque               1      201d
airflow-s3-creds                       Opaque               5      163d
airflow-secret                         Opaque               2      56d
blocked-login-ip                       Opaque               1      56d
jwt-secret                             Opaque               1      57d
kafka-aes-secret                       Opaque               1      56d
ldap-truststore-file                   Opaque               1      56d
oracle-properties                      Opaque               6      206d
oracle-secret                          Opaque               1      57d
rsa-private-secret                     Opaque               1      16d
rsa-public-secret                      Opaque               1      16d
s3-ca-secret                           Opaque               1      163d
secret-druid                           Opaque               2      51d
secret-ldap                            Opaque               2      30d
secret-postgres                        Opaque               1      56d
secret-sftp                            Opaque               1      51d
sh.helm.release.v1.airflow.v1          helm.sh/release.v1   1      201d
sh.helm.release.v1.airflow.v2          helm.sh/release.v1   1      163d
sh.helm.release.v1.airflow.v3          helm.sh/release.v1   1      163d
sh.helm.release.v1.airflow.v4          helm.sh/release.v1   1      163d
sh.helm.release.v1.airflow.v5          helm.sh/release.v1   1      90d
sh.helm.release.v1.airflow.v6          helm.sh/release.v1   1      77d
sh.helm.release.v1.airflow.v7          helm.sh/release.v1   1      44d
sh.helm.release.v1.airflow.v8          helm.sh/release.v1   1      44d
sh.helm.release.v1.spark-operator.v1   helm.sh/release.v1   1      208d
sh.helm.release.v1.spark-operator.v2   helm.sh/release.v1   1      206d
sh.helm.release.v1.spark-operator.v3   helm.sh/release.v1   1      201d
spark-operator-webhook-certs           Opaque               4      208d
uat-common-app-secret                  Opaque               1      277d
