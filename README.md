# =====================================================
# Service Account (Dedicated identity for pod security)
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: report-builder-sa
  namespace: cbops
automountServiceAccountToken: false

---
# =====================================================
# Deployment (Enhanced with enterprise best practices)
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: report-builder-deployment
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
      app: report-builder-app

  template:
    metadata:
      labels:
        app: report-builder-app

    spec:
      # -----------------------------------------------
      # Attach service account
      # -----------------------------------------------
      serviceAccountName: report-builder-sa

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
      # High availability - spread pods across nodes
      # -----------------------------------------------
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway
          labelSelector:
            matchLabels:
              app: report-builder-app

      containers:
      - name: report-builder-container
        image: h06vksharbor.corp.ad.sbi/cbops/report-builder-service:A5

        # -----------------------------------------------
        # Resource management (mandatory)
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

        env:
          - name: SPRING_DATASOURCE_URL
            value: "jdbc:oracle:thin:@10.177.179.46:1523/fincorepdb1"
          - name: SPRING_DATASOURCE_USERNAME
            value: "fincore"
          - name: SPRING_DATASOURCE_PASSWORD
            value: "Password#1234"

        ports:
        - containerPort: 8091

        imagePullPolicy: Always

        # -----------------------------------------------
        # Health probes (Spring Boot safe defaults)
        # -----------------------------------------------
        readinessProbe:
          httpGet:
            path: /actuator/health
            port: 8091
          initialDelaySeconds: 20
          periodSeconds: 10

        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 8091
          initialDelaySeconds: 40
          periodSeconds: 20

        startupProbe:
          httpGet:
            path: /actuator/health
            port: 8091
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
  name: report-builder-service
  namespace: cbops
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
# =====================================================
# Horizontal Pod Autoscaler (CPU-based scaling)
# =====================================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: report-builder-hpa
  namespace: cbops
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: report-builder-deployment
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
  name: report-builder-pdb
  namespace: cbops
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: report-builder-app