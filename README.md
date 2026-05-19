D:\Pragati\HELM-2404\Deployment\umbrella-chart>helm template micro-services-at-one-go . --show-only charts/user-service/templates/deployment.yaml --debug 2>&1
level=DEBUG msg="Original chart version" version=""
level=DEBUG msg="Chart path" path=D:\Pragati\HELM-2404\Deployment\umbrella-chart
level=DEBUG msg="number of dependencies in the chart" dependencies=16
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
level=DEBUG msg="number of dependencies in the chart" dependencies=0
---
# Source: umbrella-chart/charts/user-service/templates/deployment.yaml
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
        null

      topologySpreadConstraints:
        - labelSelector:
            matchLabels:
              app: user-backend
          maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway

      volumes:
        - name: truststore-volume
          secret:
            items:
            - key: ad-truststore.jks
              path: ad-truststore.jks
            secretName: ldap-truststore-file

      containers:
        - name: user-container
          image: "h06vksharbor.corp.ad.sbi/cbops/user-service:DEV06"
          imagePullPolicy:

          volumeMounts:
            - mountPath: /etc/fincore/secrets
              name: truststore-volume
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
            null
            - name: LDAP_TRUSTSTORE_PASSWORD
              valueFrom:
                secretKeyRef:
                  key: truststore-password
                  name: ldap-creds

          ports:
            - containerPort: 8087

          resources:
            limits:
              cpu: 500m
              memory: 1Gi
            requests:
              cpu: 250m
              memory: 512Mi

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
                command:
                  - "/bin/sh"
                  - "-c"
                  - "sleep 10"
Error: YAML parse error on umbrella-chart/charts/user-service/templates/deployment.yaml: error converting YAML to JSON: yaml: line 81: mapping values are not allowed in this context
