sharing the manifest file: 
user-deployment in this file only i have service:

# --------------------------------------------
# Service Account
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: user-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-deployment
  namespace: backend

spec:
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: user-backend

  template:
    metadata:
      labels:
        app: user-backend

    spec:
      serviceAccountName: user-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      hostAliases:
        - ip: "10.189.42.83"
          hostnames:
            - "uatrootdc1.uatad.sbi"

      volumes:
        - name: truststore-volume
          secret:
            secretName: ldap-truststore-file
            items:
              - key: ad-truststore.jks
                path: ad-truststore.jks

      containers:
        - name: user-container
          image: h06vksharbor.corp.ad.sbi/cbops/user-service:UAT10
          imagePullPolicy: Always

          volumeMounts:
            - name: truststore-volume
              mountPath: /etc/fincore/secrets
              readOnly: true

          envFrom:
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret
            - configMapRef:
                name: kafka-config
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: ldap-config
            - secretRef:
                name: ldap-secret

          env:
            - name: SPRING_PROFILES_ACTIVE
              value: "uat"

            - name: JAVA_TOOL_OPTIONS
              value: "-Djava.net.preferIPv4Stack=true"

            - name: SPRING_KAFKA_CONSUMER_GROUP_ID
              value: "rbac-cache-group"

            - name: LDAP_TRUSTSTORE_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: ldap-creds
                  key: truststore-password

          ports:
            - containerPort: 8087

          resources:
            requests:
              cpu: "250m"
              memory: "512Mi"
            limits:
              cpu: "500m"
              memory: "1Gi"

          startupProbe:
            tcpSocket:
              port: 8087
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 8087
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 8087
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

---
# --------------------------------------------
# Service
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: user-service
  namespace: backend

spec:
  selector:
    app: user-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8087

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: user-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: user-deployment

  minReplicas: 1
  maxReplicas: 5

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
# --------------------------------------------
# Pod Disruption Budget
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: user-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: user-backend


oracle-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: oracle-config
  namespace: backend

data:
  SPRING_DATASOURCE_URL: "jdbc:oracle:thin:@10.177.179.85:1523/fincorepdb1"
  SPRING_DATASOURCE_DRIVER_CLASS_NAME: "oracle.jdbc.OracleDriver"
  
oracle-secret:
apiVersion: v1
kind: Secret
metadata:
  name: oracle-secret
  namespace: backend

type: Opaque

data:
  SPRING_DATASOURCE_USERNAME: ZmluY29yZQ==
  SPRING_DATASOURCE_PASSWORD: UGFzc3dvcmQjMTIzNA==

redis-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: redis-config
  namespace: backend

data:
  SPRING_DATA_REDIS_HOST: "redis-service"
  SPRING_DATA_REDIS_PORT: "6379"
  SPRING_DATA_REDIS_CLIENT_TYPE: "lettuce"

  kafka-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: kafka-config
  namespace: backend

data:
  SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS: "kafka-0.kafka.backend.svc.cluster.local:9092"
  SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS: "kafka-0.kafka.backend.svc.cluster.local:9092"

  ldap-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: ldap-config
  namespace: backend
data:
  SPRING_LDAP_URLS: "ldaps://uatrootdc1.uatad.sbi:3269"
  LDAP_TRUSTSTORE_PATH: "file:/etc/fincore/secrets/ad-truststore.jks"
  SPRING_LDAP_USERNAME: "fincorecbops@UATAD.SBI"

  ldap-secret:
apiVersion: v1
kind: Secret
metadata:
  name: ldap-secret
  namespace: backend
type: Opaque
data:
  SPRING_LDAP_PASSWORD: RjFDMHJlIzE1


  As you can see here I am having secrets and configmaps please be very careful 

  your query: 
  1) for namepasces: my all backend services those 14 microservioces and kafka are present in one namespace and only one frontend microservice is present in another name so i have 2 nampaces one for backend and another for frontend deployment
  2) kafka is manages inside k8s only as statefulset and also DB
  3) i want one chart per microservice I think that will be better
