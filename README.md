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
  name: nwsa-variance-deployment
  namespace: be-test
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nwsa-variance-backend
  template:
    metadata:
      labels:
        app: nwsa-variance-backend
    spec:
      containers:
      - name: nwsa-variance-container
        image: h06vksharbor.corp.ad.sbi/cbops/nwsa-variance-service:DEV01
        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"        
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"       
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce" 
          - name: SPRING_KAFKA_BOOTSTRAP_SERVERS
            value: "kafka-0.kafka.be-test.svc.cluster.local:9092"
          - name: HADOOP_FS_URI
            value: "hdfs://10.177.103.199:8022"
          - name: HADOOP_FS_USER
            value: "root"
          - name: NWSA_GENERATED_REPORT_ROOT
            value: "/reports"
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.103.192:1523/fincorepdb1"        
          - name: SPRING_DATASOURCE_USERNAME
            value: "fincore"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "Password#1234" 
          - name: NWSA_REPORT_ROOT
            value: "/reports"             
        ports:
        - containerPort: 8093
        imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: nwsa-variance-service
  namespace: be-test
spec:
  selector:
    app: nwsa-variance-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8093
  type: ClusterIP
 
