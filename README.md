apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-debezium-oracle
  namespace: cbops
spec:
  podSelector:
    matchLabels:
      app: debezium-server

  policyTypes:
  - Egress

  egress:
  - to:
    - ipBlock:
        cidr: 10.177.179.46/32
    ports:
    - protocol: TCP
      port: 1523