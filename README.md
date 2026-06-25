apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-dns
  namespace: cbops
spec:
  podSelector:
    matchLabels:
      app: notificationservice
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



apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-kafka
  namespace: cbops
spec:
  podSelector:
    matchLabels:
      app: notificationservice
  policyTypes:
  - Egress
  egress:
  - to:
    - namespaceSelector:
        matchLabels:
          kubernetes.io/metadata.name: messaging
    ports:
    - protocol: TCP
      port: 9092