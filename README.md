\apiVersion: apps/v1
kind: Deployment
metadata:
  name: dashboard-deployment
  namespace: be-test
spec:
  replicas: 1
  selector:
    matchLabels:
      app: dashboard-backend
  template:
    metadata:
      labels:
        app: dashboard-backend
    spec:
      containers:
      - name: dashboard-container
        image: h06vksharbor.corp.ad.sbi/cbops/dashboard-service:DEV01
        env:
          - name: SPRING_DATA_REDIS_HOST
            value: "redis-service"        
          - name: SPRING_DATA_REDIS_PORT
            value: "6379"       
          - name: SPRING_DATA_REDIS_CLIENT_TYPE
            value: "lettuce"                   
        ports:
        - containerPort: 9015
        imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: dashboard-service
  namespace: be-test
spec:
  selector:
    app: dashboard-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9015
  type: ClusterIP
