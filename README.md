apiVersion: v1
kind: Pod
metadata:
  annotations:
    kubectl.kubernetes.io/restartedAt: "2026-06-23T14:54:10+05:30"
    prometheus.io/port: "2000"
    prometheus.io/scrape: "true"
  creationTimestamp: "2026-06-23T10:48:11Z"
  generateName: common-master-deployment-5cfd64f768-
  labels:
    app: common-master-backend
    pod-template-hash: 5cfd64f768
  name: common-master-deployment-5cfd64f768-lg499
  namespace: backend
  ownerReferences:
  - apiVersion: apps/v1
    blockOwnerDeletion: true
    controller: true
    kind: ReplicaSet
    name: common-master-deployment-5cfd64f768
    uid: 109e80c3-ae30-462f-b7df-56662f67a600
  resourceVersion: "129465855"
  uid: f93b0c97-79e1-4302-bf4a-c7a329c0c2d3
spec:
  containers:
  - env:
    - name: SPRING_PROFILES_ACTIVE
      value: dev
    envFrom:
    - configMapRef:
        name: redis-config
    - configMapRef:
        name: oracle-config
    - configMapRef:
        name: kafka-config
    - secretRef:
        name: oracle-secret
    image: artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6
    imagePullPolicy: Always
    lifecycle:
      preStop:
        exec:
          command:
          - /bin/sh
          - -c
          - sleep 10
    livenessProbe:
      failureThreshold: 5
      initialDelaySeconds: 90
      periodSeconds: 15
      successThreshold: 1
      tcpSocket:
        port: 2000
      timeoutSeconds: 5
    name: common-master-container
    ports:
    - containerPort: 2000
      protocol: TCP
    readinessProbe:
      failureThreshold: 5
      initialDelaySeconds: 30
      periodSeconds: 10
      successThreshold: 1
      tcpSocket:
        port: 2000
      timeoutSeconds: 5
    resources:
      limits:
        cpu: 500m
        memory: 512Mi
      requests:
        cpu: 200m
        memory: 256Mi
    startupProbe:
      failureThreshold: 60
      periodSeconds: 10
      successThreshold: 1
      tcpSocket:
        port: 2000
      timeoutSeconds: 1
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: kube-api-access-9kbtc
      readOnly: true
  dnsPolicy: ClusterFirst
  enableServiceLinks: false
  imagePullSecrets:
  - name: jfrog-secret
  nodeName: h06vksuatcbopscls-node-pool-1-xg7gx-fwplp-sk486
  preemptionPolicy: PreemptLowerPriority
  priority: 0
  restartPolicy: Always
  schedulerName: default-scheduler
  securityContext: {}
  serviceAccount: common-master-sa
  serviceAccountName: common-master-sa
  terminationGracePeriodSeconds: 30
  tolerations:
  - effect: NoExecute
    key: node.kubernetes.io/not-ready
    operator: Exists
    tolerationSeconds: 300
  - effect: NoExecute
    key: node.kubernetes.io/unreachable
    operator: Exists
    tolerationSeconds: 300
  topologySpreadConstraints:
  - labelSelector:
      matchLabels:
        app: common-master-backend
    maxSkew: 1
    topologyKey: kubernetes.io/hostname
    whenUnsatisfiable: ScheduleAnyway
  volumes:
  - name: kube-api-access-9kbtc
    projected:
      defaultMode: 420
      sources:
      - serviceAccountToken:
          expirationSeconds: 3607
          path: token
      - configMap:
          items:
          - key: ca.crt
            path: ca.crt
          name: kube-root-ca.crt
      - downwardAPI:
          items:
          - fieldRef:
              apiVersion: v1
              fieldPath: metadata.namespace
            path: namespace
status:
  conditions:
  - lastProbeTime: null
    lastTransitionTime: "2026-06-23T10:48:12Z"
    status: "True"
    type: PodReadyToStartContainers
  - lastProbeTime: null
    lastTransitionTime: "2026-06-23T10:48:11Z"
    status: "True"
    type: Initialized
  - lastProbeTime: null
    lastTransitionTime: "2026-06-23T10:48:11Z"
    message: 'containers with unready status: [common-master-container]'
    reason: ContainersNotReady
    status: "False"
    type: Ready
  - lastProbeTime: null
    lastTransitionTime: "2026-06-23T10:48:11Z"
    message: 'containers with unready status: [common-master-container]'
    reason: ContainersNotReady
    status: "False"
    type: ContainersReady
  - lastProbeTime: null
    lastTransitionTime: "2026-06-23T10:48:11Z"
    status: "True"
    type: PodScheduled
  containerStatuses:
  - image: artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6
    imageID: ""
    lastState: {}
    name: common-master-container
    ready: false
    restartCount: 0
    started: false
    state:
      waiting:
        message: 'failed to pull and unpack image "artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6":
          failed to resolve reference "artifactory.jfrog.sbi:443/cbops-docker-images/backend/fincore_common_master_service:feature_rahul_fincore_common_master_service_2026-06-23_f0af06a6":
          failed to authorize: failed to fetch anonymous token: unexpected status
          from GET request to https://artifactory.jfrog.sbi:443/artifactory/api/docker/cbops-docker-images/v2/token?scope=repository%3Abackend%2Ffincore_common_master_service%3Apull&scope=repository%3Acbops-docker-images%2Fbackend%2Ffincore_common_master_service%3Apull&service=artifactory.jfrog.sbi%3A443:
          401 '
        reason: ErrImagePull
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: kube-api-access-9kbtc
      readOnly: true
      recursiveReadOnly: Disabled
  hostIP: 10.244.5.100
  hostIPs:
  - ip: 10.244.5.100
  phase: Pending
  podIP: 192.168.13.43
  podIPs:
  - ip: 192.168.13.43
  qosClass: Burstable
  startTime: "2026-06-23T10:48:11Z"
