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
11. I am having 4 different environments and I want to parameterize the code according to image and imagetag values make proper directory structure of charts values file and templates as I am having 3 different environments which are dev,sit,uat and prod so accordingly you make values. yaml  and send me back all the code snippets
12.  Please maintain consistency and keep these below values separate for 4 different environments.
image:
  repository: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service
  tag: DEV-01
  imagePullPolicy: Always
  
------------------------------------------------------------------
Here is the YAML:

# =========================================================
# SERVICE ACCOUNT
# Dedicated service account for workload identity and RBAC
# =========================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: ascii-generation-sa
  namespace: backend

---
# =========================================================
# DEPLOYMENT
# =========================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ascii-generation-deployment
  namespace: backend

spec:
  replicas: 1

  # Rolling update strategy for zero/minimal downtime deployments
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: ascii-generation-backend

  template:
    metadata:
      labels:
        app: ascii-generation-backend

    spec:

      # Graceful shutdown period
      terminationGracePeriodSeconds: 60

      # Dedicated Service Account
      serviceAccountName: ascii-generation-sa

      # Pod level security context
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      # Spread pods across nodes when replicas increase
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: ascii-generation-backend

      containers:
      - name: ascii-generation-container
        image: h06vksharbor.corp.ad.sbi/cbops/ascii-generation-service:DEV-01

        envFrom:
          - configMapRef:
              name: kafka-config
          - configMapRef:
              name: redis-config
          - configMapRef:
              name: oracle-config
          - secretRef:
              name: oracle-secret
          - configMapRef:
              name: hadoop-config

        ports:
        - containerPort: 8084

        imagePullPolicy: Always

        # Container level security hardening
        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL

        # Resource management
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "1000m"
            memory: "1Gi"

        # Graceful shutdown hook
        lifecycle:
          preStop:
            exec:
              command:
                - /bin/sh
                - -c
                - sleep 20

        # Startup probe
        startupProbe:
          tcpSocket:
            port: 8084
          failureThreshold: 30
          periodSeconds: 10

        # Readiness probe
        readinessProbe:
          tcpSocket:
            port: 8084
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 3

        # Liveness probe
        livenessProbe:
          tcpSocket:
            port: 8084
          initialDelaySeconds: 60
          periodSeconds: 20
          timeoutSeconds: 5
          failureThreshold: 3

---
# =========================================================
# SERVICE
# =========================================================
apiVersion: v1
kind: Service
metadata:
  name: ascii-generation-service
  namespace: backend

spec:
  selector:
    app: ascii-generation-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8084

  type: ClusterIP

---
# =========================================================
# HORIZONTAL POD AUTOSCALER
# CPU Based Autoscaling
# =========================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: ascii-generation-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: ascii-generation-deployment

  minReplicas: 1
  maxReplicas: 5

  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
    scaleDown:
      stabilizationWindowSeconds: 300

---
# =========================================================
# POD DISRUPTION BUDGET
# Prevents voluntary disruptions
# =========================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: ascii-generation-pdb
  namespace: backend

spec:
  minAvailable: 1

  selector:
    matchLabels:
      app: ascii-generation-backend

also make the templates folder ready which includes deployment, service,hpa, pdb, serviceaccount

and keep consistency in code like similar format how you kept for earlier microservice, i wnat same syntax format for all microservices
