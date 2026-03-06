---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: user-sa
  namespace: backend

---
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
                <pattern>%d{yyyy-MM-dd HH:mm:ss} %-5level %logger{36} - %msg%n</pattern>
            </encoder>
        </appender>
        <root level="INFO">
            <appender-ref ref="STDOUT"/>
        </root>
    </configuration>

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-deployment
  namespace: backend

spec:
  replicas: 2

  selector:
    matchLabels:
      app: user-backend

  template:
    metadata:
      labels:
        app: user-backend

    spec:
      serviceAccountName: user-sa

      volumes:
        - name: logback-config
          configMap:
            name: user-logback-config

        - name: logs
          emptyDir: {}

      containers:
        - name: user-container
          image: h06vksharbor.corp.ad.sbi/cbops/user-service:TEST-1
          imagePullPolicy: Always

          ports:
            - containerPort: 8087

          env:
            - name: LOGGING_CONFIG
              value: /config/logback.xml

            - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
              value: kafka-0.kafka.backend.svc.cluster.local:9092

            - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
              value: kafka-0.kafka.backend.svc.cluster.local:9092

            - name: SPRING_DATA_REDIS_HOST
              value: redis-service

            - name: SPRING_DATA_REDIS_PORT
              value: "6379"

          volumeMounts:
            - name: logback-config
              mountPath: /config

            - name: logs
              mountPath: /logs

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

          readinessProbe:
            tcpSocket:
              port: 8087
            initialDelaySeconds: 15
            periodSeconds: 5

          livenessProbe:
            tcpSocket:
              port: 8087
            initialDelaySeconds: 30
            periodSeconds: 10

---
apiVersion: v1
kind: Service
metadata:
  name: user-service
  namespace: backend
spec:
  selector:
    app: user-backend
  ports:
    - port: 80
      targetPort: 8087
  type: ClusterIP

---
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

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
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