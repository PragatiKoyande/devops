apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  annotations:
    ako.vmware.com/controller-cluster-uuid: cluster-13e84635-e75a-4134-b68f-cd2069bd5e88
    ako.vmware.com/host-fqdn-vs-uuid-map: '{"fincore-uat.sbi":"virtualservice-77e3353e-7fb7-47ad-a22b-b90b4f3dcf14"}'
    ako.vmware.com/tenant-name: admin
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"networking.k8s.io/v1","kind":"Ingress","metadata":{"annotations":{"ako.vmware.com/controller-cluster-uuid":"cluster-13e84635-e75a-4134-b68f-cd2069bd5e88","ako.vmware.com/host-fqdn-vs-uuid-map":"{\"fincore-uat.sbi\":\"virtualservice-77e3353e-7fb7-47ad-a22b-b90b4f3dcf14\"}","ako.vmware.com/tenant-name":"admin"},"creationTimestamp":"2026-01-05T12:40:02Z","generation":2,"name":"uatcbops1-ing","namespace":"uat-cbops1","resourceVersion":"8714990","uid":"471feea1-ee95-447d-be83-2127fb877e51"},"spec":{"ingressClassName":"uatcbops1-ingressclass","rules":[{"host":"fincore-uat.sbi","http":{"paths":[{"backend":{"service":{"name":"react-service","port":{"number":80}}},"path":"/","pathType":"Prefix"},{"backend":{"service":{"name":"react-service","port":{"number":80}}},"path":"/","pathType":"Prefix"},{"backend":{"service":{"name":"login-service","port":{"number":80}}},"path":"/api/auth","pathType":"Prefix"},{"backend":{"service":{"name":"common-master-service","port":{"number":80}}},"path":"/api/announcements","pathType":"Prefix"},{"backend":{"service":{"name":"common-master-service","port":{"number":80}}},"path":"/api/balance-enquiry","pathType":"Prefix"},{"backend":{"service":{"name":"common-master-service","port":{"number":80}}},"path":"/api/calendar-config","pathType":"Prefix"},{"backend":{"service":{"name":"common-master-service","port":{"number":80}}},"path":"/api/common-master","pathType":"Prefix"},{"backend":{"service":{"name":"common-request-service","port":{"number":80}}},"path":"/api","pathType":"Prefix"},{"backend":{"service":{"name":"dashboard-service","port":{"number":80}}},"path":"/api/dashboard","pathType":"Prefix"},{"backend":{"service":{"name":"journal-service","port":{"number":80}}},"path":"/api/branches-journal","pathType":"Prefix"},{"backend":{"service":{"name":"journal-service","port":{"number":80}}},"path":"/api/cgl-journal","pathType":"Prefix"},{"backend":{"service":{"name":"journal-service","port":{"number":80}}},"path":"/api/journals","pathType":"Prefix"},{"backend":{"service":{"name":"notification-service","port":{"number":80}}},"path":"/api/notifications","pathType":"Prefix"},{"backend":{"service":{"name":"process-status-service","port":{"number":80}}},"path":"/api/process-status","pathType":"Prefix"},{"backend":{"service":{"name":"report-builder-service","port":{"number":80}}},"path":"/api/report-builder","pathType":"Prefix"},{"backend":{"service":{"name":"report-service","port":{"number":80}}},"path":"/api/reports","pathType":"Prefix"},{"backend":{"service":{"name":"transactions-service","port":{"number":80}}},"path":"/api/transaction-con","pathType":"Prefix"},{"backend":{"service":{"name":"template-config-service","port":{"number":80}}},"path":"/api/allowed-tables","pathType":"Prefix"},{"backend":{"service":{"name":"template-config-service","port":{"number":80}}},"path":"/api/template-config","pathType":"Prefix"},{"backend":{"service":{"name":"user-service","port":{"number":80}}},"path":"/api/role","pathType":"Prefix"},{"backend":{"service":{"name":"user-service","port":{"number":80}}},"path":"/api/user","pathType":"Prefix"},{"backend":{"service":{"name":"grafana","port":{"number":3000}}},"path":"/grafana","pathType":"Prefix"}]}}]},"status":{"loadBalancer":{"ingress":[{"hostname":"fincore-uat.sbi","ip":"10.177.107.105"}]}}}
  creationTimestamp: "2026-01-05T12:40:02Z"
  generation: 3
  name: uatcbops1-ing
  namespace: uat-cbops1
  resourceVersion: "24928288"
  uid: 471feea1-ee95-447d-be83-2127fb877e51
spec:
  ingressClassName: uatcbops1-ingressclass
  rules:
  - host: fincore-uat.sbi


This is the ingress I have tell me what should i add here my ingress is AVi LB so guide me.
