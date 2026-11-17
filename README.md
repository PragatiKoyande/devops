D:\pragati\HELM_LATEST_26082026>helm history react-service -n backend
REVISION        UPDATED                         STATUS          CHART                   APP VERSION     DESCRIPTION

9               Wed Oct 14 16:51:18 2026        superseded      react-service-0.1.0     1.16.0          Upgrade complete

10              Fri Oct 16 18:13:29 2026        superseded      react-service-0.1.0     1.16.0          Upgrade complete

11              Fri Oct 16 18:14:20 2026        superseded      react-service-0.1.0     1.16.0          Upgrade complete

12              Fri Oct 23 11:03:37 2026        failed          react-service-0.1.0     1.16.0          Upgrade "react-service" failed: conflict occurred while applying object cbops/react-deployment apps/v1, Kind=Deployment: Apply failed with 1 conflict: conflict with "kubectl-edit" using apps/v1: .spec.template.spec.containers[name="react"].image
13              Fri Oct 23 11:04:23 2026        failed          react-service-0.1.0     1.16.0          Upgrade "react-service" failed: conflict occurred while applying object cbops/react-deployment apps/v1, Kind=Deployment: Apply failed with 1 conflict: conflict with "kubectl-edit" using apps/v1: .spec.template.spec.containers[name="react"].image
14              Fri Oct 23 11:05:27 2026        failed          react-service-0.1.0     1.16.0          Upgrade "react-service" failed: conflict occurred while applying object cbops/react-deployment apps/v1, Kind=Deployment: Apply failed with 1 conflict: conflict with "kubectl-edit" using apps/v1: .spec.template.spec.containers[name="react"].image
15              Fri Oct 23 11:07:15 2026        superseded      react-service-0.1.0     1.16.0          Upgrade complete

16              Tue Oct 27 12:51:52 2026        superseded      react-service-0.1.0     1.16.0          Upgrade complete

17              Fri Oct 30 15:47:56 2026        superseded      react-service-0.1.0     1.16.0          Upgrade complete

18              Mon Nov  2 15:30:06 2026        deployed        react-service-0.1.0     1.16.0          Upgrade complete


D:\pragati\HELM_LATEST_26082026>helm list -A
NAME                    NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                           APP VERSION
airflow                 cbops           8               2026-11-03 18:27:48.7457005 +0530 IST   failed          airflow-1.18.0                  3.0.2
ako-1752988337          avi-system      2               2026-07-09 10:12:34.710055353 +0530 IST deployed        ako-1.13.4                      1.13.4
apache-airflow          cbops           1               2025-12-19 16:40:36.2066692 +0530 IST   failed          airflow-1.18.0                  3.0.2
common-master-service   backend         7               2026-10-15 17:30:18.7587078 +0530 IST   deployed        common-master-service-0.1.0     1.16.0
common-request-service  backend         4               2026-10-14 16:05:20.5231319 +0530 IST   deployed        common-request-service-0.1.0    1.16.0
communication-service   backend         3               2026-11-02 16:00:36.2316147 +0530 IST   deployed        communication-service-0.1.0     1.16.0
dashboard-service       backend         4               2026-10-16 12:29:58.7669926 +0530 IST   deployed        dashboard-service-0.1.0         1.16.0
enquiry-service         backend         4               2026-10-27 12:40:44.3175625 +0530 IST   deployed        enquiry-service-0.1.0           1.16.0
kubernetes-dashboard    cbops           15              2026-04-16 11:30:53.2075029 +0530 IST   deployed        kubernetes-dashboard-7.14.0
login-service           backend         1               2026-11-02 10:36:23.359767 +0530 IST    deployed        login-service-0.1.0             1.16.0
mon                     monitoring      1               2026-10-13 19:15:48.7223448 +0530 IST   deployed        kube-prometheus-stack-92.3.0    v0.94.1
notification-service    backend         1               2026-10-16 12:26:33.5159998 +0530 IST   deployed        notification-service-0.1.0      1.16.0
process-status-service  backend         3               2026-10-19 17:58:46.4648724 +0530 IST   deployed        process-status-service-0.1.0    1.16.0
react-service           backend         18              2026-11-02 15:30:06.2146656 +0530 IST   deployed        react-service-0.1.0             1.16.0
react-service           cbops           8               2026-09-09 06:43:53.108603022 +0000 UTC deployed        react-service-0.1.0             1.0
redis-service           backend         1               2026-09-21 12:33:24.5565189 +0530 IST   deployed        redis-service-0.1.0             1.16.0
report-service          backend         3               2026-10-27 12:41:47.5357232 +0530 IST   deployed        report-service-0.1.0            1.16.0
spark-operator          cbops           1               2026-01-06 18:49:16.0398487 +0530 IST   deployed        spark-operator-2.3.0            2.3.0
template-config-service backend         3               2026-10-21 18:22:18.9757297 +0530 IST   deployed        template-config-service-0.1.0   1.16.0
transactions-service    backend         4               2026-10-19 18:04:14.2729885 +0530 IST   deployed        transactions-service-0.1.0      1.16.0
user-service            backend         8               2026-10-14 17:34:01.2153692 +0530 IST   deployed        user-service-0.1.0              1.16.0
voucher-enquiry-service backend         4               2026-10-30 15:47:24.4016725 +0530 IST   deployed        voucher-enquiry-service-0.1.0   1.16.0
voucher-service         backend         3               2026-10-14 17:09:59.8733411 +0530 IST   deployed        voucher-service-0.1.0           1.16.0

D:\pragati\HELM_LATEST_26082026>helm env
HELM_BIN="helm"
HELM_BURST_LIMIT="100"
HELM_CACHE_HOME="C:\Users\v1023950\AppData\Local\Temp\helm"
HELM_CONFIG_HOME="C:\Users\v1023950\AppData\Roaming\helm"
HELM_CONTENT_CACHE="C:\Users\v1023950\AppData\Local\Temp\helm\content"
HELM_DATA_HOME="C:\Users\v1023950\AppData\Roaming\helm"
HELM_DEBUG="false"
HELM_KUBEAPISERVER=""
HELM_KUBEASGROUPS=""
HELM_KUBEASUSER=""
HELM_KUBECAFILE=""
HELM_KUBECONTEXT=""
HELM_KUBEINSECURE_SKIP_TLS_VERIFY="false"
HELM_KUBETLS_SERVER_NAME=""
HELM_KUBETOKEN=""
HELM_MAX_HISTORY="10"
HELM_NAMESPACE="backend"
HELM_PLUGINS="C:\Users\v1023950\AppData\Roaming\helm\plugins"
HELM_QPS="0.00"
HELM_REGISTRY_CONFIG="C:\Users\v1023950\AppData\Roaming\helm\registry\config.json"
HELM_REPOSITORY_CACHE="C:\Users\v1023950\AppData\Local\Temp\helm\repository"
HELM_REPOSITORY_CONFIG="C:\Users\v1023950\AppData\Roaming\helm\repositories.yaml"

D:\pragati\HELM_LATEST_26082026>kubectl get secrets -n backend --no-headers | find /c /v ""
77
