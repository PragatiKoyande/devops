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
  name: template-config-deployment
  namespace: cbops
spec:
  replicas: 1
  selector:
    matchLabels:
      app: template-app
  template:
    metadata:
      labels:
        app: template-app
    spec:
      # Add this securityContext block under spec:
      containers:
      - name: template-config-container
        image: h06vksharbor.corp.ad.sbi/cbops/template-config-service:DEV01
        env:
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.179.46:1523/fincorepdb1"
          - name: SPRING_DATASOURCE_USERNAME			
            value: "fincore"		  
          - name: SPRING_DATASOURCE_PASSWORD			
            value: "Password#1234"      
        ports:
        - containerPort: 8090
        imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: template-config-service
  namespace: cbops
spec:
  selector:
    app: template-app
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8090
  type: ClusterIP
  

_________________________________________________________________________________________________________________________
____________________________________________________________________________________________________________________________________________
____________________________________________________________________________________________________________________________________________
