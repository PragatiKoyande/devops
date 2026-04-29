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
12.  Please maintain consistency and keep these below values separate for 4 different environments.
image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service:DEV06
  tag: DEV14
------------------------------------------------------------------
env:
- name: SPRING_PROFILES_ACTIVE
  value: "dev"

- name: JAVA_TOOL_OPTIONS
  value: "-Djava.net.preferIPv4Stack=true"

- name: SPRING_KAFKA_CONSUMER_GROUP_ID
  value: "rbac-cache-group"
-----------------------------------------------------------------
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
----------------------------------------------------------------

Here is the YAML:

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
          image: h06vksharbor.corp.ad.sbi/cbops/user-service:DEV06
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


          env:
            - name: SPRING_PROFILES_ACTIVE
              value: "dev"

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


also make the templates folder ready which includes deployment, service,hpa, pdb

and keep consistency in code like similar format how you kept for earlier microservice, i wnat same syntax format for all microservices
