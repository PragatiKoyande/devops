I am providing a Kubernetes YAML file for one microservice.

STRICT RULES:

1. DO NOT change any existing values.
   - Do NOT modify names
   - Do NOT rename resources
   - Do NOT change image
   - Do NOT change ports
   - Do NOT change env variables
   - Do NOT change replicas
   - Do NOT change logic
   - Do NOT remove any production or enterprise features

2. Convert this plain YAML into Helm chart compatible structure
   based on my existing reusable Helm chart:
   charts/springboot-service/

3. The output must:
   - Generate environments/base/<service-name>.yaml
   - Generate environments/dev/<service-name>.yaml if needed
   - Map values correctly into:
       namespace
       deployment.name
       service.name
       hpa.name
       pdb.name
       labels.app
       image.repository
       image.tag
       probes.port
       env
       resources

5. Do NOT redesign the YAML.
6. Do NOT simplify it.
7. Do NOT restructure logic.
8. Only parameterize safely to fit springboot-service chart.

9. Provide:
   - values file for base
   - dev override file if needed
   - exact helm upgrade command

10. use the namespace: backend   
11. I am having 4 different envrionmnets and I want to parameterize the code according to image and imagetag values make proper directory structure of charts values file and templates as I am having 3 different environments which are dev,sit,uat and prod so accordingly you make values. yaml  and send me back all the code snippets
12.  Please maintain consistency and keep these below values separate for 4 different environments.
image:
  repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: DEV14
------------------------------------------------------------------
hostAliases:
- ip: "10.190.224.102"
  hostnames:
  - "fincore"
- ip: "10.190.224.103"
  hostnames:
  - "fincore"
- ip: "10.190.224.104"
  hostnames:
  - "fincore"
- ip: "10.190.224.105"
  hostnames:
  - "fincore"
- ip: "10.190.224.106"
  hostnames:
  - "fincore"
-------------------------------------------------------------------  
env:
  - name: SPRING_PROFILES_ACTIVE
    value: "prod"        
  - name: REPORT_BATCH_HDFS_BASE_PATH
    value: "/reports"
  - name: HADOOP_FS_URI
    value: "hdfs://10.190.224.102:8022"
  - name: HADOOP_FS_USER
    value: "root"
  - name: SPRING_KAFKA_BOOTSTRAP_SERVERS
    value: "kafka.backend.svc.cluster.local:9092"


Here is the YAML:

# --------------------------------------------
# Service Account (security baseline)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: report-builder-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: report-builder-deployment
  namespace: backend

spec:
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: report-builder-app

  template:
    metadata:
      labels:
        app: report-builder-app

    spec:
      serviceAccountName: report-builder-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      hostAliases:
      - ip: "10.190.224.102"
        hostnames:
        - "fincore"
      - ip: "10.190.224.103"
        hostnames:
        - "fincore"
      - ip: "10.190.224.104"
        hostnames:
        - "fincore"
      - ip: "10.190.224.105"
        hostnames:
        - "fincore"
      - ip: "10.190.224.106"
        hostnames:
        - "fincore"

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: report-builder-app

      containers:
      - name: report-builder-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/report-builder-service:PR-01
        imagePullPolicy: Always
        envFrom:
          - configMapRef:
              name: redis-config
          - configMapRef:
              name: kafka-config
          - configMapRef:
              name: oracle-config
          - secretRef:
              name: oracle-secret

        env:
          - name: SPRING_PROFILES_ACTIVE
            value: "prod"        
          - name: REPORT_BATCH_HDFS_BASE_PATH
            value: "/reports"
          - name: HADOOP_FS_URI
            value: "hdfs://10.190.224.102:8022"
          - name: HADOOP_FS_USER
            value: "root"
          - name: SPRING_KAFKA_BOOTSTRAP_SERVERS
            value: "kafka.backend.svc.cluster.local:9092"

        ports:
        - containerPort: 8091

        resources:
          requests:
            cpu: "3000m"
            memory: "4Gi"
          limits:
            cpu: "5000m"
            memory: "8Gi"

        startupProbe:
          tcpSocket:
            port: 8091
          failureThreshold: 30
          periodSeconds: 10

        livenessProbe:
          tcpSocket:
            port: 8091
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        readinessProbe:
          tcpSocket:
            port: 8091
          initialDelaySeconds: 15
          periodSeconds: 5
          timeoutSeconds: 3
          failureThreshold: 3

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]
---
# --------------------------------------------
# Service (internal communication)
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: report-builder-service
  namespace: backend

spec:
  selector:
    app: report-builder-app

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8091

  type: ClusterIP
---
# --------------------------------------------
# Horizontal Pod Autoscaler (CPU-based)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: report-builder-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: report-builder-deployment

  minReplicas: 1
  maxReplicas: 5

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

---
# --------------------------------------------
# Pod Disruption Budget
# --------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: report-builder-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: report-builder-app


also make the templates folder ready which includes deployment, service,hpa, pdb,
