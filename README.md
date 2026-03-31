# --------------------------------------------
# Service Account
# --------------------------------------------
apiVersion: v1
kind: ServiceAccount
metadata:
  name: user-sa
  namespace: backend

---
# --------------------------------------------
# Deployment
# --------------------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-deployment
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
      app: user-backend

  template:
    metadata:
      labels:
        app: user-backend

    spec:
      serviceAccountName: user-sa
      terminationGracePeriodSeconds: 30
      enableServiceLinks: false

      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
        runAsGroup: 1000
        fsGroup: 2000

      hostAliases:
        - ip: "10.189.42.83"
          hostnames:
            - "uatrootdc1.uatad.sbi"

      volumes:
        - name: truststore-volume
          secret:
            secretName: ldap-truststore-file
            items:
              - key: ad-truststore.jks
                path: ad-truststore.jks

      containers:
        - name: user-container
          image: h06vksharbor.corp.ad.sbi/cbops/user-service:UAT10
          imagePullPolicy: Always

          volumeMounts:
            - name: truststore-volume
              mountPath: /etc/fincore/secrets
              readOnly: true

          envFrom:
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret
            - configMapRef:
                name: kafka-config
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: ldap-config
            - secretRef:
                name: ldap-secret

          env:
            - name: SPRING_PROFILES_ACTIVE
              value: "uat"

            - name: JAVA_TOOL_OPTIONS
              value: "-Djava.net.preferIPv4Stack=true"

            - name: SPRING_KAFKA_CONSUMER_GROUP_ID
              value: "rbac-cache-group"

            - name: LDAP_TRUSTSTORE_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: ldap-creds
                  key: truststore-password

          ports:
            - containerPort: 8087

          resources:
            requests:
              cpu: "250m"
              memory: "512Mi"
            limits:
              cpu: "500m"
              memory: "1Gi"

          startupProbe:
            tcpSocket:
              port: 8087
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 8087
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 8087
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
# Service
# --------------------------------------------
apiVersion: v1
kind: Service
metadata:
  name: user-service
  namespace: backend

spec:
  selector:
    app: user-backend

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8087

  type: ClusterIP

---
# --------------------------------------------
# Horizontal Pod Autoscaler
# --------------------------------------------
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: user-hpa
  namespace: backend

spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: user-deployment

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
  name: user-pdb
  namespace: backend

spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: user-backend