apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-notification-to-kafka
  namespace: uat-cbops1
spec:
  podSelector:
    matchLabels:
      app: notification-service   # Change to your NotificationService pod label
  policyTypes:
    - Egress
  egress:
    - to:
        - podSelector:
            matchLabels:
              app: kafka          # Change if your Kafka pods use a different label
      ports:
        - protocol: TCP
          port: 9092
    - to:
        - namespaceSelector: {}
      ports:
        - protocol: UDP
          port: 53
        - protocol: TCP
          port: 53