# =====================================================
# Service Account
# =====================================================
apiVersion: v1
kind: ServiceAccount
metadata:
  name: login-sa
  namespace: backend
automountServiceAccountToken: false

---
# =====================================================
# Pod Disruption Budget
# =====================================================
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: login-pdb
  namespace: backend
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: login-backend

---
# =====================================================
# Deployment
# =====================================================
apiVersion: apps/v1
kind: Deployment
metadata:
  name: login-deployment
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
      app: login-backend

  template:
    metadata:
      labels:
        app: login-backend

    spec:
      serviceAccountName: login-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001

      hostAliases:
        - ip: "10.189.42.83"
          hostnames:
            - "uatrootdc1.uatad.sbi"

      # =================================================
      # Volumes
      # =================================================
      volumes:
        - name: truststore-volume
          secret:
            secretName: ldap-truststore-file
            items:
              - key: ad-truststore.jks
                path: ad-truststore.jks

        - name: logs-volume
          emptyDir: {}

      containers:
        - name: login-backend-container
          image: h06vksharbor.corp.ad.sbi/cbops/login-service:DEV13
          imagePullPolicy: Always

          ports:
            - containerPort: 8085

          # =================================================
          # Volume Mounts
          # =================================================
          volumeMounts:
            - name: truststore-volume
              mountPath: /etc/fincore/secrets
              readOnly: true
            - name: logs-volume
              mountPath: /logs

          envFrom:
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret
            - configMapRef:
                name: ldap-config

          env:
            - name: SPRING_PROFILES_ACTIVE
              value: "dev"

            - name: JAVA_TOOL_OPTIONS
              value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"

            - name: LDAP_TRUSTSTORE_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: ldap-creds
                  key: truststore-password

          # =================================================
          # Resources
          # =================================================
          resources:
            requests:
              cpu: "250m"
              memory: "512Mi"
            limits:
              cpu: "500m"
              memory: "1Gi"

          # =================================================
          # Probes
          # =================================================
          readinessProbe:
            tcpSocket:
              port: 8085
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

          livenessProbe:
            tcpSocket:
              port: 8085
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          startupProbe:
            tcpSocket:
              port: 8085
            failureThreshold: 60
            periodSeconds: 10

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
  name: login-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: login-deployment

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
  name: login-service
  namespace: backend

spec:
  selector:
    app: login-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8085

  type: ClusterIP
