apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: redis-vector-pvc
  namespace: uat-cbops1
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi # Enough space to hold tens of thousands of embedded banking rules
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-vector-deployment
  namespace: uat-cbops1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: redis-vector
  template:
    metadata:
      labels:
        app: redis-vector
    spec:
      containers:
      - name: redis-vector
        image: h06vksharbor.corp.ad.sbi/cbops/redis-vector:v1
        ports:
        - containerPort: 6379
        volumeMounts:
        - name: redis-data
          mountPath: /data
        resources:
          requests:
            memory: "2Gi" # Vectors reside in RAM, so allocate enough baseline
            cpu: "500m"
          limits:
            memory: "4Gi"
            cpu: "1000m"
      volumes:
      - name: redis-data
        persistentVolumeClaim:
          claimName: redis-vector-pvc
---
# =========================================================================
# REDIS SERVICE
# =========================================================================
apiVersion: v1
kind: Service
metadata:
  name: redis-vector-service
  namespace: uat-cbops1
spec:
  selector:
    app: redis-vector
  ports:
    - protocol: TCP
      port: 6380       # Port the Java App connects to (matches application.properties)
      targetPort: 6379 # Internal port Redis listens on

this above file is redis vector 

my requiuremnet is redis and redis vector

and below is my deployment file:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: help-service-deployment
  namespace: uat-cbops1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: help-service-backend
  template:
    metadata:
      labels:
        app: help-service-backend
    spec:
      containers:
      - name: help-service-container
        image: h06vksharbor.corp.ad.sbi/cbops/help-service:UAT08
        env:
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"
          - name: SPRING_PROFILES_ACTIVE
            value: "uat"
        ports:
        - containerPort: 9099
        imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: help-service
  namespace: uat-cbops1
spec:
  selector:
    app: help-service-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9099
  type: ClusterIP


alos i m attaching my application.properties file:

# ===================================================================
# SPRING DATASOURCE (ORACLE) - change this to uat
# ===================================================================
spring.datasource.url=jdbc:oracle:thin:@10.177.179.85:1523/fincorepdb1
spring.datasource.username=fincore
spring.datasource.password=Password#1234

# ===================================================================
# JPA / HIBERNATE CONFIGURATION
# ===================================================================
spring.jpa.database-platform=org.hibernate.dialect.OracleDialect
spring.jpa.hibernate.ddl-auto=validate
spring.jpa.show-sql=false
spring.jpa.properties.hibernate.format_sql=false
logging.level.org.hibernate.SQL=OFF
logging.level.org.hibernate.orm.jdbc.bind=OFF

# --- Redis Configuration ---
spring.data.redis.host=redis-service
spring.data.redis.port=6379
spring.cache.type=redis

# ==============================================================
# KUBERNETES AI CONFIGS (UAT REGION - fincore-cbops1)
# ==============================================================

# 1. Ollama Connection (Uses K8s CoreDNS to find the pod automatically)
langchain4j.ollama.base-url=http://finny-service.uat-cbops1.svc.cluster.local:11434
langchain4j.ollama.chat-model.name=llama-fincore
langchain4j.ollama.chat-model.temperature=0.1
# Note: Ensure this matches the exact name we built in the Dockerfile!
langchain4j.ollama.embedding-model.name=mxbai-embed-large

# 2. Redis Vector Store Connection
# Point to your Redis Vector Kubernetes Service
langchain4j.vector-store.redis.host=redis-vector-service.uat-cbops1.svc.cluster.local
langchain4j.vector-store.redis.port=6380
langchain4j.vector-store.redis.index-name=fincore-help-index-v2
langchain4j.vector-store.redis.prefix=fincore:doc:v2:
langchain4j.vector-store.redis.dimension=1024

please help me dugging the issue






