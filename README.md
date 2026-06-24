Volumes:
  kube-api-access-9kbtc:
    Type:                     Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:   3607
    ConfigMapName:            kube-root-ca.crt
    ConfigMapOptional:        <nil>
    DownwardAPI:              true
QoS Class:                    Burstable
Node-Selectors:               <none>
Tolerations:                  node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                              node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Topology Spread Constraints:  kubernetes.io/hostname:ScheduleAnyway when max skew 1 is exceeded for selector app=common-master-backend
Events:
  Type     Reason   Age                     From     Message
  ----     ------   ----                    ----     -------
  Normal   BackOff  4m58s (x5126 over 19h)  kubelet  Back-off pulling image "artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6"
  Warning  Failed   4m58s (x5126 over 19h)  kubelet  Error: ImagePullBackOff
