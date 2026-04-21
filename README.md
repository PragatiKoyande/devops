Can you please make templates folder for me I mean all files : serviceaccount.yaml, deployment.yaml, service.yaml, hpa.yaml, pdb.yaml ans send them back below i m pasting the main manifest 

# --------------------------------------------
# Service Account (security best practice)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: nwsa-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nwsa-variance-deployment
  namespace: backend

spec:
  replicas: 2

  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: nwsa-variance-backend

  template:
    metadata:
      labels:
        app: nwsa-variance-backend

      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "8093"

    spec:
      serviceAccountName: nwsa-sa
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

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: nwsa-variance-backend

      containers:
      - name: nwsa-variance-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/nwsa-variance-service:PR-03
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
          - name: HADOOP_FS_HA_NN1
            value: "hdfs://10.190.224.102:8022"
          - name: HADOOP_FS_HA_NN2
            value: "hdfs://10.190.224.103:8022"
          - name: HADOOP_FS_HA_NN3
            value: "hdfs://10.190.224.104:8022"
          - name: HADOOP_FS_HA_NN4
            value: "hdfs://10.190.224.105:8022"
          - name: HADOOP_FS_HA_NN5
            value: "hdfs://10.190.224.106:8022"
          - name: NWSA_GENERATED_REPORT_ROOT
            value: "/reports"
          - name: NWSA_REPORT_ROOT
            value: "/reports"            
          - name: HADOOP_FS_URI
            value: "hdfs://fincore:8022"
          - name: HADOOP_FS_USER
            value: "root"

        ports:
        - containerPort: 8093

        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        startupProbe:
          tcpSocket:
            port: 8093
          failureThreshold: 30
          periodSeconds: 10

        livenessProbe:
          tcpSocket:
            port: 8093
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3
          failureThreshold: 3

        readinessProbe:
          tcpSocket:
            port: 8093
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
# Service (internal cluster access)
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: nwsa-variance-service
  namespace: backend

spec:
  selector:
    app: nwsa-variance-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8093

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler (auto scaling)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: nwsa-variance-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: nwsa-variance-deployment

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
  name: nwsa-variance-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: nwsa-variance-backend
