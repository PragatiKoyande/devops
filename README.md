apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-apps-to-kafka
  namespace: be-test
spec:
  podSelector: {}
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
        - protocol: TCP
          port: 9093