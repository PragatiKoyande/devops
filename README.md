E:\Tushar Khade\Projects-CR-Document\Finanace-One\DEV-Deployment\Network-Policy>k get cm config-postgres -n backend -o yaml
apiVersion: v1
data:
  PSQL_SPRING_DATASOURCE_DRIVER_CLASS_NAME: org.postgresql.Driver
  PSQL_SPRING_DATASOURCE_URL: jdbc:postgresql://10.177.103.196:5432/fincore
  PSQL_SPRING_DATASOURCE_USERNAME: fincore
kind: ConfigMap
metadata:
  creationTimestamp: "2026-07-31T12:35:59Z"
  name: config-postgres
  namespace: backend
  resourceVersion: "149904010"
  uid: 310b9fdb-6d3f-483b-b39f-233c56107e06

E:\Tushar Khade\Projects-CR-Document\Finanace-One\DEV-Deployment\Network-Policy>k get deployment notification-deployment -n backend -o yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  annotations:
    deployment.kubernetes.io/revision: "8"
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"apps/v1","kind":"Deployment","metadata":{"annotations":{},"name":"notification-deployment","namespace":"backend"},"spec":{"replicas":1,"selector":{"matchLabels":{"app":"notification-backend"}},"template":{"metadata":{"labels":{"app":"notification-backend"}},"spec":{"containers":[{"env":[{"name":"SPRING_KAFKA_CONSUMER_GROUP_ID","value":"notification-service-group"},{"name":"SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET","value":"earliest"},{"name":"SPRING_DATA_REDIS_CLIENT_TYPE","value":"lettuce"},{"name":"JWT_SECRET","valueFrom":{"secretKeyRef":{"key":"JWT_SECRET","name":"jwt-secret"}}},{"name":"PSQL_SPRING_DATASOURCE_PASSWORD","valueFrom":{"secretKeyRef":{"key":"PSQL_SPRING_DATASOURCE_PASSWORD","name":"secret-postgres"}}}],"envFrom":[{"configMapRef":{"name":"config-redis"}},{"configMapRef":{"name":"config-postgres"}},{"configMapRef":{"name":"kafka-config"}}],"image":"h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01","imagePullPolicy":"Always","name":"notification-container","ports":[{"containerPort":9010}]}]}}}}
  creationTimestamp: "2026-08-05T07:16:41Z"
  generation: 8
  name: notification-deployment
  namespace: backend
  resourceVersion: "149912512"
  uid: fc784e76-83a4-4b4f-b080-d65692f52d52
spec:
  progressDeadlineSeconds: 600
  replicas: 1
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: notification-backend
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      annotations:
        kubectl.kubernetes.io/restartedAt: "2026-08-05T14:45:04+05:30"
      creationTimestamp: null
      labels:
        app: notification-backend
    spec:
      containers:
      - env:
        - name: SPRING_KAFKA_CONSUMER_GROUP_ID
          value: notification-service-group
        - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
          value: earliest
        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: lettuce
        - name: JWT_SECRET
          valueFrom:
            secretKeyRef:
              key: JWT_SECRET
              name: jwt-secret
        - name: PSQL_SPRING_DATASOURCE_PASSWORD
          valueFrom:
            secretKeyRef:
              key: PSQL_SPRING_DATASOURCE_PASSWORD
              name: secret-postgres
        envFrom:
        - configMapRef:
            name: config-redis
        - configMapRef:
            name: config-postgres
        - configMapRef:
            name: kafka-config
        image: h06vksharbor.corp.ad.sbi/cbops/notification-service:EV-01
        imagePullPolicy: Always
        name: notification-container
        ports:
        - containerPort: 9010
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
  - lastTransitionTime: "2026-08-05T07:16:41Z"
    lastUpdateTime: "2026-08-05T09:15:06Z"
    message: ReplicaSet "notification-deployment-6d559c9f67" has successfully progressed.
    reason: NewReplicaSetAvailable
    status: "True"
    type: Progressing
  - lastTransitionTime: "2026-08-05T09:21:42Z"
    lastUpdateTime: "2026-08-05T09:21:42Z"
    message: Deployment does not have minimum availability.
    reason: MinimumReplicasUnavailable
    status: "False"
    type: Available
  observedGeneration: 8
  replicas: 1
  unavailableReplicas: 1
  updatedReplicas: 1
