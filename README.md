apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-kafka-access
  namespace: cbops
spec:
  podSelector:
    matchLabels:
      app: kafka
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector: {}   # Allow all pods in cbops namespace
      ports:
        - protocol: TCP
          port: 9092