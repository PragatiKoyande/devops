apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-postgres-egress
  namespace: cbops
spec:
  podSelector:
    matchLabels:
      app: notification-service
  policyTypes:
  - Egress
  egress:
  - to:
    - ipBlock:
        cidr: 10.20.30.40/32   # PostgreSQL IP
    ports:
    - protocol: TCP
      port: 5432