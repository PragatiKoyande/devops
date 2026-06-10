apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-egress-to-oracle-db
  namespace: be-test
spec:
  podSelector:
    matchLabels:
      app: help-service-backend

  policyTypes:
  - Egress

  egress:
  - to:
    - ipBlock:
        cidr: 10.177.179.85/32
    ports:
    - protocol: TCP
      port: 1523