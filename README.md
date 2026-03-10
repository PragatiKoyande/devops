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
# Logback Override ConfigMap
# --------------------------------------------
apiVersion: v1
kind: ConfigMap
metadata:
  name: user-logback-config
  namespace: backend
data:
  logback.xml: |
    <configuration>
        <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
            <encoder>
                <pattern>%d{yyyy-MM-dd HH:mm:ss} %-5level %logger - %msg%n</pattern>
            </encoder>
        </appender>

        <root level="INFO">
            <appender-ref ref="STDOUT"/>
        </root>
    </configuration>

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
  replicas: 2
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

      topologySpreadConstraints:
      - maxSkew: 1
        topologyKey: kubernetes.io/hostname
        whenUnsatisfiable: ScheduleAnyway
        labelSelector:
          matchLabels:
            app: user-backend

      volumes:
      - name: logs-volume
        emptyDir: {}

      - name: logback-config
        configMap:
          name: user-logback-config

      # LDAP Truststore Secret Volume
      - name: truststore-volume
        secret:
          secretName: ldap-truststore-file
          items:
            - key: ad-truststore.jks
              path: ad-truststore.jks

      containers:
      - name: user-container
        image: h06vksharbor.corp.ad.sbi/cbops/user-service:TEST-1
        imagePullPolicy: Always

        volumeMounts:
        - name: logs-volume
          mountPath: /logs

        - name: logback-config
          mountPath: /config

        - name: truststore-volume
          mountPath: /etc/fincore/secrets
          readOnly: true

        env:

        # Logging
        - name: JAVA_TOOL_OPTIONS
          value: "-Djava.net.preferIPv4Stack=true -Dlogging.config=/config/logback.xml -Djavax.net.debug=ssl:handshake"

        # Kafka
        - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
          value: "kafka-0.kafka.backend.svc.cluster.local:9092"

        - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
          value: "kafka-0.kafka.backend.svc.cluster.local:9092"

        - name: SPRING_KAFKA_CONSUMER_GROUP_ID
          value: "rbac-cache-group"

        # Redis
        - name: SPRING_DATA_REDIS_HOST
          value: "redis-service"

        - name: SPRING_DATA_REDIS_PORT
          value: "6379"

        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: "lettuce"

        # LDAP
        - name: SPRING_LDAP_URLS
          value: "ldaps://uatrootdc1.uatad.sbi:3269"

        - name: LDAP_TRUSTSTORE_PATH
          value: "file:/etc/fincore/secrets/ad-truststore.jks"

        - name: SPRING_LDAP_USERNAME
          value: "fincorecbops@UATAD.SBI"

        - name: SPRING_LDAP_PASSWORD
          value: "F1C0re#15"

        - name: LDAP_TRUSTSTORE_PASSWORD
          valueFrom:
            secretKeyRef:
              name: ldap-creds
              key: truststore-password

        ports:
        - containerPort: 8087

        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        startupProbe:
          tcpSocket:
            port: 8087
          failureThreshold: 30
          periodSeconds: 10

        livenessProbe:
          tcpSocket:
            port: 8087
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        readinessProbe:
          tcpSocket:
            port: 8087
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

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