apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-dns-notification
  namespace: cbops
spec:
  podSelector:
    matchLabels:
      app: notification-backend
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
  name: allow-postgres-egress
  namespace: cbops
spec:
  egress:
  - ports:
    - port: 5432
      protocol: TCP
    to:
    - ipBlock:
        cidr: 10.177.179.51/32
  podSelector: {}
  policyTypes:
  - Egress
