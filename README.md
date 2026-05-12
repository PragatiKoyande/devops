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
  repository: h06vksharbor.corp.ad.sbi/cbops/transactions-service
  tag: DEV01
  imagePullPolicy: Always
  
------------------------------------------------------------------
Here is the YAML:

# =====================================================
# Service Account
# Dedicated identity for secure pod execution
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: enquiry-service-sa
  namespace: backend
automountServiceAccountToken: false

---
# =====================================================
# Pod Disruption Budget
# Ensures minimum pod availability during maintenance
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: enquiry-service-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: enquiry-service-backend

---
# =====================================================
# Deployment
# Enterprise-grade production deployment configuration
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: enquiry-service-deployment
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
      app: enquiry-service-backend

  template:
    metadata:
      labels:
        app: enquiry-service-backend
      serviceAccountName: enquiry-service-sa
      terminationGracePeriodSeconds: 60

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 1000
        seccompProfile:
          type: RuntimeDefault

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: enquiry-service-backend

      containers:
      - name: enquiry-service-container
        image: h06vksharbor.corp.ad.sbi/cbops/enquiry-service:DEV03
        imagePullPolicy: Always
		
        envFrom:
          - secretRef:
              name: oracle-secret

        ports:
        - containerPort: 4001
		
        resources:
          requests:
            cpu: "250m"
            memory: "512Mi"
          limits:
            cpu: "1000m"
            memory: "1Gi"

        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL

        livenessProbe:
          tcpSocket:
            port: 4001
          initialDelaySeconds: 60
          periodSeconds: 20
          timeoutSeconds: 5
          failureThreshold: 5

        readinessProbe:
          tcpSocket:
            port: 4001
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 3

        startupProbe:
          tcpSocket:
            port: 4001
          initialDelaySeconds: 20
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 30

        lifecycle:
          preStop:
            exec:
              command:
                - /bin/sh
                - -c
                - sleep 20

---
# =====================================================
# Service
# Internal ClusterIP service exposure
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: enquiry-service
  namespace: backend
spec:
  selector:
    app: enquiry-service-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 4001

  type: ClusterIP

---
# =====================================================
# Horizontal Pod Autoscaler
# CPU based autoscaling configuration
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: enquiry-service-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: enquiry-service-deployment

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
      policies:
        - type: Percent
          value: 100
          periodSeconds: 60

    scaleDown:
      stabilizationWindowSeconds: 300
      policies:
        - type: Percent
          value: 50
          periodSeconds: 60

also make the templates folder ready which includes deployment, service,hpa, pdb

and keep consistency in code like similar format how you kept for earlier microservice, i wnat same syntax format for all microservices
