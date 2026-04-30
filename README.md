I am providing a Kubernetes YAML file.

IMPORTANT RULES — FOLLOW STRICTLY:

1. DO NOT change any existing values.
   - Do NOT modify names
   - Do NOT change image, ports, env, replicas
   - Do NOT rename uresorces
   - Do NOT alter existing logic

2. ONLY add enterprise-grade / production-grade Kubernetes features on top of the existing YAML.

3. Add all REQUIRED production and enterprise best practices EXCEPT Prometheus or monitoring annotations.
   Add things like:
   - resources requests & limits
   - liveness/readiness/startup probes (safe defaults)
   - rolling update strategy
   - security context
   - service account
   - HPA (CPU based)
   - PodDisruptionBudget
   - lifecycle preStop hook
   - topology spread constraints
   - graceful shutdown settings
   - any other MUST-HAVE enterprise features

4. Do NOT add Prometheus annotations or monitoring-related configs.

5. Keep YAML structure clean and production-ready.

6. Do not ask for permission before adding missing enterprise features — just add them.

7. After YAML, explain briefly what new things were added and why.
8. add also comments in yaml file for better understanding 

Here is the YAML:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: notification-deployment
  namespace: cbops
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
          image: h06vksharbor.corp.ad.sbi/cbops/notification-service:SIT01          
          env:
            - name: SPRING_DATASOURCE_URL
              value: "jdbc:postgresql://postgres-db:5432/notification_db"
            - name: SPRING_DATASOURCE_USERNAME
              value: "notification_user"
            - name: SPRING_DATASOURCE_PASSWORD
              value: "notification_password"  
            - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
              value: "kafka.cbops.svc.cluster.local:9092"  
            - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
              value: "kafka.cbops.svc.cluster.local:9092"               
            - name: SPRING_KAFKA_CONSUMER_GROUP_ID
              value: "notification-service-group"              
            - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
              value: "earliest"     
            - name: SPRING_DATA_REDIS_HOST
              value: "redis-service"        
            - name: SPRING_DATA_REDIS_PORT
              value: "6379"       
            - name: SPRING_DATA_REDIS_CLIENT_TYPE
              value: "lettuce"             
          ports:
            - containerPort: 9010
          imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: notification-service
  namespace: cbops
spec:
  selector:
    app: notification-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9010
  type: ClusterIP

____________________________________________________________________________________________________________________________________________
____________________________________________________________________________________________________________________________________________
____________________________________________________________________________________________________________________________________________
