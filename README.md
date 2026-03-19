env: 
  - name: SPRING_DATA_REDIS_HOST
    value: "redis-service"
  - name: SPRING_DATA_REDIS_PORT
    value: "6379"
  - name: SPRING_DATA_REDIS_CLIENT_TYPE
    value: "lettuce"
  - name: SPRING_PROFILES_ACTIVE  
    value: "dev"

  - name: SPRING_DATASOURCE_URL
    value: "jdbc:oracle:thin:@//<DB_HOST>:<PORT>/<SERVICE_NAME>"
  - name: SPRING_DATASOURCE_USERNAME
    value: "<DB_USERNAME>"
  - name: SPRING_DATASOURCE_PASSWORD
    value: "<DB_PASSWORD>"

  # 🔥 FORCE ORACLE (this fixes your issue)
  - name: SPRING_DATASOURCE_DRIVER_CLASS_NAME
    value: "oracle.jdbc.OracleDriver"
  - name: SPRING_DATASOURCE_PLATFORM
    value: "oracle"
  - name: SPRING_JPA_DATABASE_PLATFORM
    value: "org.hibernate.dialect.OracleDialect"