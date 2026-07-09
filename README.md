apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-reportservice-kafka-dns
  namespace: be-test
spec:
  podSelector:
    matchLabels:
      app: report-service      # Change to your ReportService pod label
  policyTypes:
    - Egress
  egress:
    # Allow Kafka
    - to:
        - namespaceSelector:
            matchLabels:
              kubernetes.io/metadata.name: be-test
          podSelector:
            matchLabels:
              app: kafka
      ports:
        - protocol: TCP
          port: 9092

    # Allow CoreDNS
    - to:
        - namespaceSelector:
            matchLabels:
              kubernetes.io/metadata.name: kube-system
          podSelector:
            matchLabels:
              k8s-app: kube-dns
      ports:
        - protocol: UDP
          port: 53
        - protocol: TCP
          port: 53