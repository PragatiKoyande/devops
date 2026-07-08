apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-egress-debezium
  namespace: backend

spec:
  podSelector:
    matchLabels:
      app: debezium-server

  policyTypes:
  - Egress

  egress:

  # Oracle
  - to:
    - ipBlock:
        cidr: 10.177.179.145/32
    ports:
    - protocol: TCP
      port: 1523

  # DNS
  - to:
    - namespaceSelector:
        matchLabels:
          kubernetes.io/metadata.name: kube-system
    ports:
    - protocol: UDP
      port: 53
    - protocol: TCP
      port: 53

  # Kafka
  - to:
    - podSelector:
        matchLabels:
          app: kafka
    ports:
    - protocol: TCP
      port: 9092