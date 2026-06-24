apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-communicationservice-to-kafka
  namespace: uat-cbops1
spec:
  podSelector:
    matchLabels:
      app: kafka
  policyTypes:
  - Ingress
  ingress:
  - from:
    - podSelector:
        matchLabels:
          app: communication-service
    ports:
    - protocol: TCP
      port: 9092