apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: loginservice-egress
  namespace: backend
spec:
  podSelector:
    matchLabels:
      app: login-service

  policyTypes:
  - Egress

  egress:

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

  # LDAP
  - to:
    - ipBlock:
        cidr: <LDAP_IP>/32
    ports:
    - protocol: TCP
      port: 3269

  # Oracle
  - to:
    - ipBlock:
        cidr: <ORACLE_IP>/32
    ports:
    - protocol: TCP
      port: 1521