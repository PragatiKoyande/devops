# =====================================================
# Service Account (Dedicated identity for pod security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: user-sa
  namespace: cbops
automountServiceAccountToken: false

---
# =====================================================
D:\Pragati\HELM-2404\Deployment\report-service>kubectl describe pod report-deployment-69447cdd4f-hn2tf -n backend  --kubeconfig h06vksuatcbopscls.conf
Name:             report-deployment-69447cdd4f-hn2tf
Namespace:        backend
Priority:         0
Service Account:  report-sa
Node:             <none>
Labels:           app=report-backend
                  pod-template-hash=69447cdd4f
Annotations:      <none>
Status:           Pending
IP:
IPs:              <none>
Controlled By:    ReplicaSet/report-deployment-69447cdd4f
Containers:
  report-container:
    Image:      h06vksharbor.corp.ad.sbi/cbops/report-service:DEV14
    Port:       9005/TCP
    Host Port:  0/TCP
    Limits:
      cpu:     1Gi
      memory:  500m
    Requests:
      cpu:      512Mi
      memory:   250m
    Liveness:   tcp-socket :9005 delay=90s timeout=5s period=15s #success=1 #failure=5
    Readiness:  tcp-socket :9005 delay=30s timeout=5s period=10s #success=1 #failure=5
    Startup:    tcp-socket :9005 delay=0s timeout=1s period=10s #success=1 #failure=60
    Environment Variables from:
      redis-config   ConfigMap  Optional: false
      kafka-config   ConfigMap  Optional: false
      oracle-config  ConfigMap  Optional: false
      oracle-secret  Secret     Optional: false
    Environment:
      SPRING_PROFILES_ACTIVE:  dev
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-h28p6 (ro)
Conditions:
  Type           Status
  PodScheduled   False
Volumes:
  kube-api-access-h28p6:
    Type:                     Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:   3607
    ConfigMapName:            kube-root-ca.crt
    ConfigMapOptional:        <nil>
    DownwardAPI:              true
QoS Class:                    Burstable
Node-Selectors:               <none>
Tolerations:                  node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                              node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Topology Spread Constraints:  kubernetes.io/hostname:ScheduleAnyway when max skew 1 is exceeded for selector app=report-backend
Events:
  Type     Reason            Age   From               Message
  ----     ------            ----  ----               -------
  Warning  FailedScheduling  45s   default-scheduler  0/6 nodes are available: 3 Insufficient cpu, 3 node(s) had untolerated taint {node-role.kubernetes.io/control-plane: }. preemption: 0/6 nodes are available: 3 No preemption victims found for incoming pod, 3 Preemption is not helpful for scheduling.# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-deployment
  namespace: cbops
spec:
  replicas: 1

  # -----------------------------------------------
  # Rolling update strategy (zero downtime)
  # -----------------------------------------------
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: user-backend

  template:
    metadata:
      labels:
        app: user-backend

    spec:
      # -----------------------------------------------
      # Attach service account
      # -----------------------------------------------
      serviceAccountName: user-sa

      # -----------------------------------------------
      # Graceful shutdown
      # -----------------------------------------------
      terminationGracePeriodSeconds: 30

      # -----------------------------------------------
      # Pod-level security context
      # -----------------------------------------------
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        fsGroup: 1000

      # -----------------------------------------------
      # High availability - spread pods
      # -----------------------------------------------
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: user-backend

      # -----------------------------------------------
      # Existing hostAliases (unchanged)
      # -----------------------------------------------
      hostAliases:
      - ip: "10.189.42.83"
        hostnames:
        - "uatrootdc1.uatad.sbi"

      # -----------------------------------------------
      # Existing volumes (unchanged)
      # -----------------------------------------------
      volumes:
      - name: truststore-volume
        secret:
          secretName: ldap-truststore-file
          items:
            - key: ad-truststore.jks
              path: ad-truststore.jks

      containers:
      - name: user-container
        image: h06vksharbor.corp.ad.sbi/cbops/user-service:SIT06

        # -----------------------------------------------
        # Resource management
        # -----------------------------------------------
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        # -----------------------------------------------
        # Container security hardening
        # -----------------------------------------------
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: true
          capabilities:
            drop:
              - ALL

        volumeMounts:
        - name: truststore-volume
          mountPath: "/etc/fincore/secrets"
          readOnly: true

        env:
            # ========= REQUIRED =========
            - name: SPRING_LDAP_URLS
              value: "ldaps://uatrootdc1.uatad.sbi:3269"
            - name: JAVA_TOOL_OPTIONS
              value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"
            - name: SPRING_KAFKA_CONSUMER_BOOTSTRAP_SERVERS
              value: "kafka-0.kafka.cbops.svc.cluster.local:9092"
            - name: SPRING_KAFKA_PRODUCER_BOOTSTRAP_SERVERS
              value: "kafka-0.kafka.cbops.svc.cluster.local:9092"
            - name: SPRING_KAFKA_CONSUMER_GROUP_ID
              value: "rbac-cache-group"
            - name: SPRING_DATA_REDIS_HOST
              value: "redis-service"
            - name: SPRING_DATA_REDIS_PORT
              value: "6379"
            - name: SPRING_DATA_REDIS_CLIENT_TYPE
              value: "lettuce"
            - name: SPRING_DATASOURCE_URL
              value: "jdbc:oracle:thin:@10.177.179.46:1523/fincorepdb1"
            - name: SPRING_DATASOURCE_USERNAME
              value: "fincore"
            - name: SPRING_DATASOURCE_PASSWORD
              value: "Password#1234"
            # LDAP TRUSTSTORE CONFIG
            - name: LDAP_TRUSTSTORE_PATH
              value: "file:/etc/fincore/secrets/ad-truststore.jks"
            - name: LDAP_TRUSTSTORE_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: ldap-creds
                  key: truststore-password

        ports:
        - containerPort: 8087

        imagePullPolicy: Always

        # -----------------------------------------------
        # Health probes (Spring Boot safe defaults)
        # -----------------------------------------------
        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 8087
          initialDelaySeconds: 20
          periodSeconds: 10

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 8087
          initialDelaySeconds: 40
          periodSeconds: 20

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 8087
          failureThreshold: 30
          periodSeconds: 10

        # -----------------------------------------------
        # Graceful shutdown hook
        # -----------------------------------------------
        lifecycle:
          preStop:
            exec:
              command: ["sh", "-c", "sleep 10"]

---
# =====================================================
# Service (unchanged)
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: user-service
  namespace: cbops
spec:
  selector:
    app: user-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8087
  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler (CPU-based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: user-hpa
  namespace: cbops
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: user-deployment
  minReplicas: 1
  maxReplicas: 5
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
# =====================================================
# Pod Disruption Budget (ensure availability)
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: user-pdb
  namespace: cbops
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: user-backend
