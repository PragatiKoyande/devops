<?xml version="1.0" encoding="UTF-8"?>
<configuration>

    <!-- 1. CONSOLE APPENDER (Text for Humans) -->
    <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>
                %d{yyyy-MM-dd HH:mm:ss.SSS} %highlight(%-5level) [%blue(%t)] %yellow(%C{1}): %msg %n%throwable
            </pattern>
        </encoder>
    </appender>

    <!-- 2. JSON FILE APPENDER (For Machines/ETL) -->
    <appender name="JSON_FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <file>logs/application-json.log</file>

        <rollingPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">
            <!-- Rotate daily or when size > 10MB -->
            <fileNamePattern>logs/archived/app-json-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
            <maxFileSize>10MB</maxFileSize>
            <maxHistory>30</maxHistory>
        </rollingPolicy>

        <encoder class="net.logstash.logback.encoder.LoggingEventCompositeJsonEncoder">
            <providers>
                <timestamp>
                    <timeZone>Asia/Kolkata</timeZone>
                </timestamp>
                <pattern>
                    <pattern>
                        {
                        "level": "%level",
                        "service": "${spring.application.name:-LoginService}",
                        "traceId": "%mdc{traceId}",
                        "userId": "%mdc{userId}",
                        "clientIp": "%mdc{clientIp}",
                        "apiPath": "%mdc{apiPath}",
                        "class": "%logger{40}",
                        "message": "%message",
                        "stack_trace": "%exception{10}"
                        }
                    </pattern>
                </pattern>
            </providers>
        </encoder>
    </appender>

    <!-- 3. ROOT LOGGER -->
    <root level="INFO">
        <appender-ref ref="CONSOLE" />
        <appender-ref ref="JSON_FILE" />
    </root>

</configuration>
