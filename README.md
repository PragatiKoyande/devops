C:\Windows\System32>k get pods --show-labels | grep -i redis
redis-deployment-9fb78d586-7759r              1/1     Running   0          3d20h   app.kubernetes.io/instance=redis-service,app.kubernetes.io/name=redis,pod-template-hash=9fb78d586

C:\Windows\System32>k get svc redis-service -n backend -o yaml
apiVersion: v1
kind: Service
metadata:
  annotations:
    meta.helm.sh/release-name: redis-service
    meta.helm.sh/release-namespace: backend
  creationTimestamp: "2026-09-17T09:02:36Z"
  labels:
    app.kubernetes.io/instance: redis-service
    app.kubernetes.io/managed-by: Helm
    app.kubernetes.io/name: redis
    app.kubernetes.io/version: 1.16.0
    helm.sh/chart: redis-service-0.1.0
  name: redis-service
  namespace: backend
  resourceVersion: "170206036"
  uid: 62cedb13-5e71-4613-b2fc-b41259afce15
spec:
  clusterIP: 10.110.234.135
  clusterIPs:
  - 10.110.234.135
  internalTrafficPolicy: Cluster
  ipFamilies:
  - IPv4
  ipFamilyPolicy: SingleStack
  ports:
  - name: http
    port: 80
    protocol: TCP
    targetPort: 6379
  selector:
    app.kubernetes.io/instance: redis-service
    app.kubernetes.io/name: redis
  sessionAffinity: None
  type: ClusterIP
status:
  loadBalancer: {}
