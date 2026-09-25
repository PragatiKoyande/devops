D:\pragati\HELM_LATEST_26082026\Grafana-Deployment>kubectl get pv -n cbops --kubeconfig h06vksuatcbopscls.conf
NAME                                       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS        CLAIM                                       STORAGECLASS   VOLUMEATTRIBUTESCLASS   REASON   AGE
airflow-new-pv                             5Gi        RWX            Delete           Terminating   cbops/airflow-dags                          h06-vks-sp-6   <unset>                          197d
pvc-34360a99-be86-4953-9d7d-00d5f54947e6   50Gi       RWO            Delete           Bound         backend/kafka-data-kafka-0                  h06-vks-sp-6   <unset>                          8d
pvc-34aa3481-3d35-4ca7-8243-5d6edb028deb   100Gi      RWO            Delete           Terminating   cbops/logs-airflow-triggerer-0              h06-vks-sp-3   <unset>                          156d
pvc-53ff550d-28bd-4f90-a1b3-eb329f59fab3   150Gi      RWO            Delete           Terminating   tanzu-system-monitoring/prometheus-server   h06-vks-sp-3   <unset>                          199d
pvc-56358765-3836-47b5-82d6-40aa179e9b55   100Gi      RWO            Delete           Terminating   cbops/logs-airflow-worker-2                 h06-vks-sp-3   <unset>                          156d
pvc-72040709-8d9f-4456-8207-16ac6a09245c   2Gi        RWO            Delete           Terminating   tanzu-system-monitoring/alertmanager        h06-vks-sp-3   <unset>                          199d
pvc-8fc62353-980d-433a-901f-0303b72eb857   100Gi      RWO            Delete           Terminating   cbops/logs-airflow-worker-1                 h06-vks-sp-3   <unset>                          156d
pvc-9b9144b3-0ee8-4d61-aa77-8f5606217d20   5Gi        RWO            Delete           Terminating   cbops/grafana-pvc                           h06-vks-sp-3   <unset>                          212d
pvc-a91822ec-97b8-43e5-b61a-ad9a92aa9e9f   100Gi      RWO            Delete           Terminating   cbops/logs-airflow-worker-0                 h06-vks-sp-3   <unset>                          156d
pvc-b6a2575d-a8d7-4f5f-8f93-a294e56117ec   50Gi       RWO            Delete           Bound         backend/debezium-pvc                        h06-vks-sp-6   <unset>                          8d
redis-airflow-pv                           10Gi       RWX            Delete           Bound         cbops/redis-airflow-pvc                     h06-vks-sp-6   <unset>                          51d

D:\pragati\HELM_LATEST_26082026\Grafana-Deployment>kubectl get pvc -n cbops --kubeconfig h06vksuatcbopscls.conf
NAME                       STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
airflow-dags               Bound    airflow-new-pv                             5Gi        RWX            h06-vks-sp-6   <unset>                 197d
logs-airflow-triggerer-0   Bound    pvc-34aa3481-3d35-4ca7-8243-5d6edb028deb   100Gi      RWO            h06-vks-sp-3   <unset>                 156d
logs-airflow-worker-0      Bound    pvc-a91822ec-97b8-43e5-b61a-ad9a92aa9e9f   100Gi      RWO            h06-vks-sp-3   <unset>                 156d
logs-airflow-worker-1      Bound    pvc-8fc62353-980d-433a-901f-0303b72eb857   100Gi      RWO            h06-vks-sp-3   <unset>                 156d
logs-airflow-worker-2      Bound    pvc-56358765-3836-47b5-82d6-40aa179e9b55   100Gi      RWO            h06-vks-sp-3   <unset>                 156d
redis-airflow-pvc          Bound    redis-airflow-pv                           10Gi       RWX            h06-vks-sp-6   <unset>                 51d
