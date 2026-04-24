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

4. If YAML contains:
   - Secrets ? map to secret.enabled block
   - ConfigMaps ? map to configMap.enabled block
   - DB credentials ? map to database.enabled block
   - Enterprise features ? preserve them exactly

5. Do NOT redesign the YAML.
6. Do NOT simplify it.
7. Do NOT restructure logic.
8. Only parameterize safely to fit springboot-service chart.

9. Provide:
   - values file for base
   - dev override file if needed
   - exact helm upgrade command

10. use the namespace: backend   

Here is the YAML:

# --------------------------------------------
# Service Account (security best practice)
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-master-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: common-master-deployment
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
      app: common-master-backend

  template:
    metadata:
      labels:
        app: common-master-backend
      annotations:
        prometheus.io/scrape: "true"
        prometheus.io/port: "2000"

    spec:
      serviceAccountName: common-master-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: common-master-backend

      containers:
        - name: common-master-container
          image: a2p05vksharbor.corp.ad.sbi/cbops/common-master-service:PR-02
          imagePullPolicy: Always

          envFrom:
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret

          ports:
            - containerPort: 2000

          resources:
            requests:
              cpu: "200m"
              memory: "256Mi"
            limits:
              cpu: "500m"
              memory: "512Mi"

          startupProbe:
            tcpSocket:
              port: 2000
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 2000
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 2000
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

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
  name: common-master-service
  namespace: backend

spec:
  selector:
    app: common-master-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 2000

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler (auto scaling)
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: common-master-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: common-master-deployment

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
  name: common-master-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: common-master-backend
