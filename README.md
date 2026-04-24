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
12.  Please maintain consistency and keep these values separate for 4 different environments as you kept earlier for common-master and common-request in which you mentioned 
image:
  repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: DEV14


Here is the YAML:


# ------------------------------------------------
# Service Account
# ------------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: notification-sa
  namespace: backend

---
# ------------------------------------------------
# Deployment
# ------------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: notification-deployment
  namespace: backend
  labels:
    app: notification-backend

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
      app: notification-backend

  template:
    metadata:
      labels:
        app: notification-backend

    spec:
      serviceAccountName: notification-sa
      enableServiceLinks: false
      terminationGracePeriodSeconds: 30

      volumes:
      - name: tmp-dir
        emptyDir:
          medium: Memory
          sizeLimit: 64Mi

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000  

      containers:
      - name: notification-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/notification-service:PR-01
        imagePullPolicy: Always

        volumeMounts:
        - name: tmp-dir
          mountPath: /tmp        

        ports:
        - containerPort: 9010

        envFrom:
          - configMapRef:
              name: postgres-config
          - secretRef:
              name: postgres-secret
          - configMapRef:
              name: redis-config
          - configMapRef:
              name: kafka-config     

        env:
          - name: SPRING_KAFKA_CONSUMER_GROUP_ID
            value: "notification-service-group"
          - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
            value: "earliest"
          - name: SPRING_PROFILES_ACTIVE
            value: "prod"

        resources:
          requests:
            cpu: "200m"
            memory: "512Mi"
          limits:
            cpu: "500m"
            memory: "1Gi"

        startupProbe:
          tcpSocket:
            port: 9010
          failureThreshold: 30
          periodSeconds: 10

        livenessProbe:
          tcpSocket:
            port: 9010
          initialDelaySeconds: 30
          periodSeconds: 10
          timeoutSeconds: 3

        readinessProbe:
          tcpSocket:
            port: 9010
          initialDelaySeconds: 15
          periodSeconds: 5

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh","-c","sleep 10"]

        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: true
          capabilities:
            drop:
            - ALL
---
# ------------------------------------------------
# Service
# ------------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: notification-service
  namespace: backend

spec:
  type: ClusterIP

  selector:
    app: notification-backend

  ports:
  - port: 80
    targetPort: 9010
    protocol: TCP

---
# ------------------------------------------------
# Horizontal Pod Autoscaler
# ------------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: notification-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: notification-deployment

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
# ------------------------------------------------
# Pod Disruption Budget
# ------------------------------------------------
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: notification-pdb
  namespace: backend

spec:
  minAvailable: 1

  selector:
    matchLabels:
      app: notification-backend

