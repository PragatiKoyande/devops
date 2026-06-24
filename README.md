Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       False
  ContainersReady             False
  PodScheduled                True
Volumes:
  kube-api-access-c298j:
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
  Type     Reason     Age                From               Message
  ----     ------     ----               ----               -------
  Normal   Scheduled  70s                default-scheduler  Successfully assigned backend/common-master-deployment-74b5c5689c-gh86w to h06vksuatcbopscls-node-pool-1-xg7gx-fwplp-w9fxd
  Normal   Pulling    34s (x3 over 70s)  kubelet            Pulling image "artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6"
  Warning  Failed     34s (x3 over 70s)  kubelet            Failed to pull image "artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6": failed to pull and unpack image "artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6": failed to resolve reference "artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6": failed to authorize: failed to fetch anonymous token: unexpected status from GET request to https://artifactory.jfrog.sbi:443/artifactory/api/docker/cbops-docker-images/v2/token?scope=repository%3Abackend%2Ffincore_common_master_service%3Apull&scope=repository%3Acbops-docker-images%2Fbackend%2Ffincore_common_master_service%3Apull&service=artifactory.jfrog.sbi%3A443: 401
  Warning  Failed     34s (x3 over 70s)  kubelet            Error: ErrImagePull
  Normal   BackOff    6s (x4 over 69s)   kubelet            Back-off pulling image "artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6"
  Warning  Failed     6s (x4 over 69s)   kubelet            Error: ImagePullBackOff
