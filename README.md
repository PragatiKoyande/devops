I am providing a Kubernetes YAML file for one microservice.

STRICT RULES:

1. DO NOT change any existing values.
   - Do NOT modify names
   - Do NOT rename resources
   - Do NOT change image
   - Do NOT change ports
   - Do NOT change env variables
   - Do NOT change replicas
   - Do NOT change logic
   - Do NOT remove any production or enterprise features

2. Convert this plain YAML into Helm chart compatible structure
   based on my existing reusable Helm chart:
   charts/springboot-service/

3. The output must:
   - Generate environments/base/<service-name>.yaml
   - Generate environments/dev/<service-name>.yaml if needed
   - Map values correctly into:
       namespace
       deployment.name
       service.name
       hpa.name
       pdb.name
       networkPolicy.name
       labels.app
       image.repository
       image.tag
       probes.port
       env
       resources

4. If YAML contains:
   - Secrets → map to secret.enabled block
   - ConfigMaps → map to configMap.enabled block
   - DB credentials → map to database.enabled block
   - Enterprise features → preserve them exactly

5. Do NOT redesign the YAML.
6. Do NOT simplify it.
7. Do NOT restructure logic.
8. Only parameterize safely to fit springboot-service chart.

9. Provide:
   - values file for base
   - dev override file if needed
   - exact helm upgrade command

Here is the YAML:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: common-master-deployment
  namespace: be-test
spec:
  replicas: 1
  selector:
    matchLabels:
      app: common-master-backend
  template:
    metadata:
      labels:
        app: common-master-backend
    spec:
      containers:
      - name: common-master-container
        image: h06vksharbor.corp.ad.sbi/cbops/common-master-service:DEV01
        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"        
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"       
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"                   
        ports:
        - containerPort: 2000
        imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: common-master-service
  namespace: be-test
spec:
  selector:
    app: common-master-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 2000
  type: ClusterIP
