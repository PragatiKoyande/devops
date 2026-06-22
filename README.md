# ==========================================
# 1. THE DEPLOYMENT
# ==========================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: finny-deployment
  namespace: uat-cbops1
spec:
  replicas: 1 # The HPA will take control of this number once deployed
  selector:
    matchLabels:
      app: ollama
  template:
    metadata:
      labels:
        app: ollama
    spec:
      containers:
      - name: ollama
        # Point to your custom, baked image
        image: h06vksharbor.corp.ad.sbi/cbops/finny:v1
        imagePullPolicy: Always
        ports:
        - containerPort: 11434
        env:
        # Keep models in memory forever (no 5m timeouts)
        - name: OLLAMA_KEEP_ALIVE
          value: "-1"
        # Force Ollama to keep BOTH the Chat and Embedding models loaded at the same time
        - name: OLLAMA_MAX_LOADED_MODELS
          value: "2"
        - name: OLLAMA_NUM_PARALLEL
          value: "1"
        resources:
          requests:
            # Baseline required to hold the 8B LLM and Embedding Model
            memory: "8Gi"
            cpu: "4000m"
          limits:
            # Ceiling raised to prevent OOMKills during long context chats
            memory: "12Gi"
            cpu: "12000m"
            # IF YOUR DEV CLUSTER HAS GPUs, UNCOMMENT THE LINE BELOW:
            # nvidia.com/gpu: 1

---
# ==========================================
# 2. THE SERVICE
# ==========================================
apiVersion: v1
kind: Service
metadata:
  name: finny-service
  namespace: uat-cbops1
spec:
  selector:
    app: ollama
  ports:
  - protocol: TCP
    port: 11434
    targetPort: 11434
---
# ==========================================
# 3. HORIZONTAL POD AUTOSCALER (HPA)
# ==========================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: ollama-hpa
  namespace: uat-cbops1
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: finny-deployment
  minReplicas: 1
  # CAUTION: Max Replicas = 3 means at peak traffic, this will consume up to 36GB of Cluster RAM (12Gi * 3).
  maxReplicas: 3
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 80 # Scale up if CPU goes above 80%

