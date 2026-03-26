[root@fcprodkubjump Microservices]# vim prod-common-request-deployment.yaml
[root@fcprodkubjump Microservices]# kubectl apply -f prod-common-request-deployment.yaml -n backend
serviceaccount/common-request-sa unchanged
poddisruptionbudget.policy/common-request-pdb configured
horizontalpodautoscaler.autoscaling/common-request-hpa unchanged
service/common-request-service unchanged
The request is invalid: patch: Invalid value: "map[metadata:map[annotations:map[kubectl.kubernetes.io/last-applied-configuration:{\"apiVersion\":\"apps/v1\",\"kind\":\"Deployment\",\"metadata\":{\"annotations\":{},\"name\":\"common-request-deployment\",\"namespace\":\"backend\"},\"spec\":{\"replicas\":1,\"selector\":{\"matchLabels\":{\"app\":\"common-request-backend\"}},\"strategy\":{\"rollingUpdate\":{\"maxSurge\":1,\"maxUnavailable\":0},\"type\":\"RollingUpdate\"},\"template\":{\"metadata\":{\"labels\":{\"app\":\"common-request-backend\"}},\"spec\":{\"containers\":[{\"envFrom\":[{\"configMapRef\":null,\"name\":\"redis-config\"},{\"configMapRef\":null,\"name\":\"kafka-config\"},{\"configMapRef\":null,\"name\":\"spring-datasource-config\"},{\"name\":\"spring-datasource-secret\",\"secretRef\":null}],\"image\":\"a2p05vksharbor.corp.ad.sbi/cbops/common-request-service:PR-01\",\"imagePullPolicy\":\"Always\",\"lifecycle\":{\"preStop\":{\"exec\":{\"command\":[\"/bin/sh\",\"-c\",\"sleep 10\"]}}},\"livenessProbe\":{\"failureThreshold\":5,\"initialDelaySeconds\":90,\"periodSeconds\":15,\"tcpSocket\":{\"port\":9000},\"timeoutSeconds\":5},\"name\":\"common-request-container\",\"ports\":[{\"containerPort\":9000}],\"readinessProbe\":{\"failureThreshold\":5,\"initialDelaySeconds\":30,\"periodSeconds\":10,\"tcpSocket\":{\"port\":9000},\"timeoutSeconds\":5},\"resources\":{\"limits\":{\"cpu\":\"500m\",\"memory\":\"512Mi\"},\"requests\":{\"cpu\":\"200m\",\"memory\":\"256Mi\"}},\"securityContext\":{\"allowPrivilegeEscalation\":false,\"capabilities\":{\"drop\":[\"ALL\"]},\"readOnlyRootFilesystem\":false},\"startupProbe\":{\"failureThreshold\":60,\"periodSeconds\":10,\"tcpSocket\":{\"port\":9000}}}],\"securityContext\":{\"fsGroup\":10001,\"runAsNonRoot\":true,\"runAsUser\":10001},\"serviceAccountName\":\"common-request-sa\",\"terminationGracePeriodSeconds\":30,\"topologySpreadConstraints\":[{\"labelSelector\":{\"matchLabels\":{\"app\":\"common-request-backend\"}},\"maxSkew\":1,\"topologyKey\":\"kubernetes.io/hostname\",\"whenUnsatisfiable\":\"ScheduleAnyway\"}]}}}}\n]] spec:map[template:map[spec:map[]]]]": strict decoding error: unknown field "spec.template.spec.containers[0].envFr



getting this issue and below is my manifest file

# =====================================================
# Service Account (Dedicated Identity for Pod Security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-request-sa
  namespace: backend
automountServiceAccountToken: false
---
# =====================================================
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: common-request-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: common-request-backend
---
# =====================================================
# Deployment (Enterprise Hardened)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: common-request-deployment
  namespace: backend
spec:
  replicas: 1

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: common-request-backend

  template:
    metadata:
      labels:
        app: common-request-backend
    spec:

      serviceAccountName: common-request-sa
      terminationGracePeriodSeconds: 30

      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: common-request-backend

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      containers:
      - name: common-request-container
        image: a2p05vksharbor.corp.ad.sbi/cbops/common-request-service:PR-01
        imagePullPolicy: Always

        envFrom:
         - configMapRef:
           name: redis-config
         - configMapRef:
           name: kafka-config
         - configMapRef:
           name: spring-datasource-config
         - secretRef:
           name: spring-datasource-secret

        ports:
        - containerPort: 9000

        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"

        startupProbe:
          tcpSocket:
            port: 9000
          failureThreshold: 60     # was 30 - doubled
          periodSeconds: 10        # total startup time = 10 min

        livenessProbe:
          tcpSocket:
            port: 9000
          initialDelaySeconds: 90   # was 30 - increased
          periodSeconds: 15
          timeoutSeconds: 5
          failureThreshold: 5

        readinessProbe:
          tcpSocket:
            port: 9000
          initialDelaySeconds: 30   # was 15
          periodSeconds: 10
          timeoutSeconds: 5
          failureThreshold: 5

        lifecycle:
          preStop:
            exec:
              command: ["/bin/sh", "-c", "sleep 10"]

        securityContext:
          allowPrivilegeEscalation: false
          readOnlyRootFilesystem: false
          capabilities:
            drop:
              - ALL
---
# =====================================================
# Horizontal Pod Autoscaler
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: common-request-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: common-request-deployment
  minReplicas: 1
  maxReplicas: 3
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
---
# =====================================================
# Service
# =====================================================
apiVersion: v1
kind: Service
metadata:
  name: common-request-service
  namespace: backend
spec:
  selector:
    app: common-request-backend
  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 9000
  type: ClusterIP



  please do the correction of this issue and send me back the entire mnifest file
