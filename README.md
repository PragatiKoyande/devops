Deployment file:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: notification-deployment
  namespace: backend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: notification-backend
  template:
    metadata:
      labels:
        app: notification-backend
    spec:
      containers:
        - name: notification-container
          image: h06vksharbor.corp.ad.sbi/cbops/notification-service:PRE-PROD-01
          envFrom:
          - configMapRef:
              name: config-postgres
          - configMapRef:
              name: config-redis
          - configMapRef:
              name: config-kafka
          - secretRef:
              name: kafka-aes-secret
          - secretRef:
              name: rsa-private-secret
          - secretRef:
              name: rsa-public-secret
          - secretRef:
              name: jwt-secret
          - secretRef:
              name: secret-postgres
          env:
            - name: SPRING_PROFILES_ACTIVE
              value: "preprod"
            - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
              value: "earliest"
            - name: SPRING_KAFKA_CONSUMER_GROUP_ID
              value: "notification-service-group"

          ports:
            - containerPort: 9010
          imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: notification-service
  namespace: backend
spec:
  selector:
    app: notification-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9010
  type: ClusterIP



  application-properties::

  # ==========================================
# PREPROD PROFILE
# ==========================================
server.port=9010

# LOGIN SERVICE KEY USED BY common-entities
jwt.secret=${JWT_SECRET}

# --- Database (SIT Postgres) ---
spring.datasource.url=${PSQL_SPRING_DATASOURCE_URL}
spring.datasource.username=${PSQL_SPRING_DATASOURCE_USERNAME}
spring.datasource.password=${PSQL_SPRING_DATASOURCE_PASSWORD}
spring.datasource.driver-class-name=${PSQL_SPRING_DATASOURCE_DRIVER_CLASS_NAME}

# Validate schema only. Do NOT auto-update.
# This prevents Hibernate from accidentally altering your permanent tables.
spring.jpa.hibernate.ddl-auto=validate
spring.jpa.show-sql=false

# --- Redis (SIT Redis) ---
spring.data.redis.host=${REDIS_HOST}
spring.data.redis=${REDIS_PORT}
# spring.data.redis.password=${REDIS_PASS}

# --- Kafka (SIT Cluster) ---
security.internal.kafka-aes-key=${KAFKA_AES_SECRET}
spring.kafka.consumer.bootstrap-servers=${KAFKA_CONSUMER_BOOTSTRAP_SERVERS}
spring.kafka.producer.bootstrap-servers=${KAFKA_PRODUCER_BOOTSTRAP_SERVERS}
spring.kafka.consumer.group-id=notification-service-group-sit
spring.kafka.consumer.auto-offset-reset=earliest

# --- Actuator (Secured for SIT) ---
# Only expose health, info, and metrics. Hide sensitive bean dumps.
management.endpoints.web.exposure.include=health,info,prometheus
management.endpoint.health.show-details=never

# --- Logging ---
logging.level.com.fincore=INFO
logging.level.root=WARN
