apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-dns-debezium
  namespace: cbops
spec:
  podSelector:
    matchLabels:
      app: debezium-server
  policyTypes:
  - Egress
  egress:
  - to:
    - namespaceSelector:
        matchLabels:
          kubernetes.io/metadata.name: kube-system
    ports:
    - protocol: UDP
      port: 53
    - protocol: TCP
      port: 53