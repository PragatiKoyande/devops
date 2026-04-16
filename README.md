Similar to login service now I want to do the helm deployment with different 3 environments for another service which is notification service and I am sharing the manifest with you for the same.


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
  replicas: 1
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

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      volumes:
        - name: tmp-dir
          emptyDir:
            medium: Memory
            sizeLimit: 64Mi
        - name: logs-volume
          emptyDir: {}


      containers:
        - name: notification-container
          image: h06vksharbor.corp.ad.sbi/cbops/notification-service:TEST-1
          imagePullPolicy: Always

          volumeMounts:
            - name: tmp-dir
              mountPath: /tmp
            - name: logs-volume
              mountPath: /logs

          ports:
            - containerPort: 9010

          envFrom:
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: kafka-config
            - configMapRef:
                name: postgres-config
            - secretRef:
                name: postgres-secret

          env:
            - name: SPRING_KAFKA_CONSUMER_GROUP_ID
              value: "notification-service-group"

            - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
              value: "earliest"

          resources:
            requests:
              cpu: "250m"
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
                command: ["/bin/sh", "-c", "sleep 10"]

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
