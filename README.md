apiVersion: v1
kind: ConfigMap
metadata:
  name: notification-db-config
  namespace: backend
data:
  SPRING_DATASOURCE_URL: jdbc:postgresql://postgres-db:5432/notification_db
  SPRING_DATASOURCE_DRIVER_CLASS_NAME: org.postgresql.Driver
  SPRING_JPA_DATABASE_PLATFORM: org.hibernate.dialect.PostgreSQLDialect
  SPRING_JPA_HIBERNATE_DDL_AUTO: none


apiVersion: v1
kind: Secret
metadata:
  name: notification-db-secret
  namespace: backend
type: Opaque
stringData:
  SPRING_DATASOURCE_USERNAME: notification_user
  SPRING_DATASOURCE_PASSWORD: notification_password



echo -n "notification_password" | base64