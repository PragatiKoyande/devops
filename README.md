apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-egress-to-oracle
  namespace: backend
spec:
  podSelector:
    matchLabels:
      app: debezium-server
  policyTypes:
  - Egress
  egress:
  - to:
    - ipBlock:
        cidr: 10.177.179.145/32
    ports:
    - protocol: TCP
      port: 1523