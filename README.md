I am providing a Kubernetes YAML file.

IMPORTANT RULES — FOLLOW STRICTLY:

1. DO NOT change any existing values.
   - Do NOT modify names
   - Do NOT change image, ports, env, replicas
   - Do NOT rename resources
   - Do NOT alter existing logic

2. ONLY add enterprise-grade / production-grade Kubernetes features on top of the existing YAML.

3. Add all REQUIRED production and enterprise best practices EXCEPT Prometheus or monitoring annotations.
   Add things like:
   - resources requests & limits
   - liveness/readiness/startup probes (safe defaults)
   - rolling update strategy
   - security context
   - service account
   - HPA (CPU based)
   - PodDisruptionBudget
   - lifecycle preStop hook
   - topology spread constraints
   - network policy
   - graceful shutdown settings
   - any other MUST-HAVE enterprise features

4. Do NOT add Prometheus annotations or monitoring-related configs.

5. Keep YAML structure clean and production-ready.

6. Do not ask for permission before adding missing enterprise features — just add them.

7. After YAML, explain briefly what new things were added and why.
8. add also comments in yaml file for better understanding 
Here is the YAML:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: login-deployment
  namespace: be-test
spec:
  replicas: 1
  selector:
    matchLabels:
      app: login-backend
  template:
    metadata:
      labels:
        app: login-backend
    spec:
      hostAliases:
      - ip: "10.189.42.83"
        hostnames:
        - "uatrootdc1.uatad.sbi"
      volumes:
      - name: truststore-volume
        secret:
          secretName: ldap-truststore-file
          items:
            - key: ad-truststore.jks        # Ensure this matches the key you created
              path: ad-truststore.jks       # Forces the filename inside /etc/fincore/secrets/
      containers:
      - name: login-backend-container
        image: h06vksharbor.corp.ad.sbi/cbops/login-service:DEV09

        volumeMounts:
        - name: truststore-volume
          mountPath: "/etc/fincore/secrets"
          readOnly: true

        env:
        - name: SPRING_LDAP_URLS
          value: "ldaps://uatrootdc1.uatad.sbi:3269"        
        - name: JAVA_TOOL_OPTIONS
          value: "-Djava.net.preferIPv4Stack=true -Djavax.net.debug=ssl:handshake"        
        - name: SPRING_DATA_REDIS_HOST
          value: "redis-service.be-test.svc.cluster.local"
        - name: SPRING_DATA_REDIS_PORT
          value: "6379"
        - name: SPRING_DATA_REDIS_CLIENT_TYPE
          value: "lettuce"
        - name: SPRING_PROFILES_ACTIVE
          value: "dev"

        # LDAP TRUSTSTORE CONFIG
        - name: LDAP_TRUSTSTORE_PATH
          value: "file:/etc/fincore/secrets/ad-truststore.jks"

        - name: LDAP_TRUSTSTORE_PASSWORD
          valueFrom:
            secretKeyRef:
              name: ldap-creds
              key: truststore-password

        ports:
        - containerPort: 8085
        imagePullPolicy: Always

---
apiVersion: v1
kind: Service
metadata:
  name: login-service
  namespace: be-test
spec:
  selector:
    app: login-backend
  ports:
  - name: http
    protocol: TCP
    port: 80
    targetPort: 8085
  type: ClusterIP
