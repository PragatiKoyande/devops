Similar to react service now I want to do the helm deployment with different 3 environments for another service which is redis service and I am sharing the manifest with you for the same

apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-deployment
  namespace: be-test
spec:
  replicas: 1
  selector:
    matchLabels:
      app: redis-server
  template:
    metadata:
      labels:
        app: redis-server
    spec:
      containers:
      - name: redis-container
        # Use a standard Redis image
        image: h06vksharbor.corp.ad.sbi/cbops/redis-server:latest
        env:
          - name: ALLOW_EMPTY_PASSWORD
            value: "yes"          
        ports:
        - containerPort: 6379
        imagePullPolicy: Always
---
apiVersion: v1
kind: Service
metadata:
  name: redis-service # This name becomes the internal DNS hostname
  namespace: be-test
spec:
  selector:
    app: redis-server
  ports:
    - protocol: TCP
      port: 6379
      targetPort: 6379
  type: ClusterIP
