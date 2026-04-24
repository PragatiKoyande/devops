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

hostAliases:
  - ip: "10.189.42.83"
     hostnames:
       - "uatrootdc1.uatad.sbi"
         
Here is the YAML:


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
        - ip: "10.176.53.145"
          hostnames:
            - "corp.ad.sbi"
            - "corpdcmdgbl01.corp.ad.sbi"
        - ip: "10.176.54.30"
          hostnames:
            - "corpdcmdgbl02.corp.ad.sbi"
        - ip: "10.176.54.31"
          hostnames:
            - "corpdcmdgbl03.corp.ad.sbi"
        - ip: "10.176.54.32"
          hostnames:
            - "corpdcmdgbl04.corp.ad.sbi"
        - ip: "10.189.37.135"
          hostnames:
            - "corpdcmdrbl01.corp.ad.sbi"
        - ip: "10.189.37.136"
          hostnames:
            - "corpdcmdrbl02.corp.ad.sbi"
        - ip: "10.189.37.137"
          hostnames:
            - "corpdcmdrbl03.corp.ad.sbi"
        - ip: "10.189.37.138"
          hostnames:
            - "corpdcmdrbl04.corp.ad.sbi"

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
          image: a2p05vksharbor.corp.ad.sbi/cbops/login-service:PR-03
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
            - secretRef:
                name: ldap-secret

          env:
            - name: SPRING_PROFILES_ACTIVE
              value: "prod"
            - name: JAVA_TOOL_OPTIONS
              value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"

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


