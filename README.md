apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-kafka
spec:
  podSelector:
    matchLabels:
      app: login-service

  policyTypes:
  - Egress

  egress:
  - to:
    - namespaceSelector:
        matchLabels:
          kubernetes.io/metadata.name: uat-cbops1
    ports:
    - protocol: TCP
      port: 9092