apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-postgres-notification
  namespace: cbops
spec:
  podSelector:
    matchLabels:
      app: notification-backend

  policyTypes:
  - Egress

  egress:
  - to:
    - podSelector:
        matchLabels:
          app: postgres-db
    ports:
    - protocol: TCP
      port: 5432