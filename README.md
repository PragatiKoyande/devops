apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-egress-to-redis
  namespace: <your-namespace>
spec:
  podSelector:
    matchExpressions:
      - key: app
        operator: In
        values:
          - auth-service
          - user-service
          - customer-service
          - account-service
          - dashboard-service
          - notification-service
          - common-request
          - payment-service
          - report-service
          - gateway-service
          - login-service
          - audit-service
          - config-service
          - frontend-service
  policyTypes:
    - Egress
  egress:
    - to:
        - podSelector:
            matchLabels:
              app: redis
      ports:
        - protocol: TCP
          port: 6379