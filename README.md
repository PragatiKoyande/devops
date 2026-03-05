# ============================================
# Service Account
# ============================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: journal-sa
  namespace: backend

---
# ============================================
# Deployment
# ============================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: journal-deployment
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
      app: journal-app

  template:
    metadata:
      labels:
        app: journal-app

    spec:
      serviceAccountName: journal-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      volumes:
        - name: logs-volume
          emptyDir: {}
        - name: tmp-volume
          emptyDir: {}

      containers:
        - name: journal-container
          image: h06vksharbor.corp.ad.sbi/cbops/journal-service:SV04
          imagePullPolicy: Always

          ports:
            - containerPort: 9999

          volumeMounts:
            - name: logs-volume
              mountPath: /logs
            - name: tmp-volume
              mountPath: /tmp

          resources:
            requests:
              cpu: "200m"
              memory: "256Mi"
            limits:
              cpu: "500m"
              memory: "512Mi"

          # =========================
          # PROBES (Actuator Based)
          # =========================
          startupProbe:
            httpGet:
              path: /actuator/health
              port: 9999
            failureThreshold: 30
            periodSeconds: 10

          readinessProbe:
            httpGet:
              path: /actuator/health/readiness
              port: 9999
            initialDelaySeconds: 20
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 3

          livenessProbe:
            httpGet:
              path: /actuator/health/liveness
              port: 9999
            initialDelaySeconds: 40
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 3

          lifecycle:
            preStop:
              exec:
                command: ["/bin/sh", "-c", "sleep 10"]

          securityContext:
            allowPrivilegeEscalation: false
            readOnlyRootFilesystem: true
            capabilities:
              drop:
                - ALL

---
# ============================================
# Service
# ============================================
apiVersion: v1
kind: Service
metadata:
  name: journal-service
  namespace: backend
spec:
  selector:
    app: journal-app
  ports:
    - name: http
      port: 80
      targetPort: 9999
  type: ClusterIP

---
# ============================================
# Horizontal Pod Autoscaler
# ============================================
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: journal-hpa
  namespace: backend
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: journal-deployment
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
# ============================================
# Pod Disruption Budget
# ============================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: journal-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: journal-app