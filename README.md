Now I am sharing with you another microservice manifest files and details kilndly make proper congiuartion and send me backk all files:

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

-----------------------------------------------------------------
redis-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: redis-config
  namespace: backend

data:
  SPRING_DATA_REDIS_HOST: "redis-service"
  SPRING_DATA_REDIS_PORT: "6379"
  SPRING_DATA_REDIS_CLIENT_TYPE: "lettuce"


  oracle-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: oracle-config
  namespace: backend

data:
  SPRING_DATASOURCE_URL: "jdbc:oracle:thin:@10.177.179.85:1523/fincorepdb1"
  SPRING_DATASOURCE_DRIVER_CLASS_NAME: "oracle.jdbc.OracleDriver"
  
oracle-secret:
apiVersion: v1
kind: Secret
metadata:
  name: oracle-secret
  namespace: backend

type: Opaque

data:
  SPRING_DATASOURCE_USERNAME: ZmluY29yZQ==
  SPRING_DATASOURCE_PASSWORD: UGFzc3dvcmQjMTIzNA==

  ldap-config:
apiVersion: v1
kind: ConfigMap
metadata:
  name: ldap-config
  namespace: backend
data:
  SPRING_LDAP_URLS: "ldaps://uatrootdc1.uatad.sbi:3269"
  LDAP_TRUSTSTORE_PATH: "file:/etc/fincore/secrets/ad-truststore.jks"
  SPRING_LDAP_USERNAME: "fincorecbops@UATAD.SBI"

  

  
