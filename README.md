        - name: SPRING_DATASOURCE_URL
          value: "jdbc:postgresql://postgres-db:5432/notification_db"

        - name: SPRING_DATASOURCE_USERNAME
          value: "notification_user"

        - name: SPRING_DATASOURCE_PASSWORD
          value: "notification_password"

        - name: SPRING_DATASOURCE_DRIVER_CLASS_NAME
          value: "org.postgresql.Driver"

        - name: SPRING_JPA_DATABASE_PLATFORM
          value: "org.hibernate.dialect.PostgreSQLDialect"

        - name: SPRING_JPA_HIBERNATE_DDL_AUTO
          value: "none"


          want to amke config maps and secrts for this env
