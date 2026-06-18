apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-oracle
spec:
  podSelector:
    matchLabels:
      app: voucher-service
  policyTypes:
  - Egress
  egress:
  - to:
    - ipBlock:
        cidr: 10.177.103.192/32
    ports:
    - protocol: TCP
      port: 1523