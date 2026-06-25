apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-debezium-kafka
  namespace: cbops
spec:
  podSelector:
    matchLabels:
      app: debezium-server

  policyTypes:
  - Egress

  egress:
  - to:
    - podSelector:
        matchLabels:
          app: kafka
    ports:
    - protocol: TCP
      port: 9092