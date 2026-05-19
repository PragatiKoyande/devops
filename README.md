            tcpSocket:
              port: 4001
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 3

          startupProbe:
            tcpSocket:
              port: 4001
            initialDelaySeconds: 20
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 30

          lifecycle:
            preStop:
              exec:
                command:
                - /bin/sh
                - -c
                - sleep 20
---
# Source: umbrella-chart/charts/common-master/templates/serviceaccount.yaml

apiVersion: v1
kind: ServiceAccount
metadata:
  name: common-master-sa
  namespace: backend
---
# Source: umbrella-chart/charts/transactions/templates/deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: transactions-deployment
  namespace: backend

spec:
  replicas: 1

  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1

  selector:
    matchLabels:
      app: transactions-backend

  template:
    metadata:
      labels:
        app: transactions-backend

    spec:
      serviceAccountName: transactions-sa
      automountServiceAccountToken: false
      terminationGracePeriodSeconds: 30

      topologySpreadConstraints:
        - labelSelector:
            matchLabels:
              app: transactions-backend
          maxSkew: 1
          topologyKey: kubernetes.io/hostname
          whenUnsatisfiable: ScheduleAnyway

      securityContext:
        fsGroup: 10001
        runAsNonRoot: true
        runAsUser: 10001

      containers:
        - name: transactions-container
          image: h06vksharbor.corp.ad.sbi/cbops/transactions-service:DEV01
          imagePullPolicy: Always

          envFrom:
            - configMapRef:
                name: redis-config
            - configMapRef:
                name: oracle-config
            - secretRef:
                name: oracle-secret

          env:
            null

          ports:
            - containerPort: 4000

          resources:
            limits:
              cpu: 500m
              memory: 1Gi
            requests:
              cpu: 250m
              memory: 512Mi

          startupProbe:
            tcpSocket:
              port: 4000
            failureThreshold: 60
            periodSeconds: 10

          livenessProbe:
            tcpSocket:
              port: 4000
            initialDelaySeconds: 90
            periodSeconds: 15
            timeoutSeconds: 5
            failureThreshold: 5

          readinessProbe:
            tcpSocket:
              port: 4000
            initialDelaySeconds: 30
            periodSeconds: 10
            timeoutSeconds: 5
            failureThreshold: 5

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
Error: YAML parse error on umbrella-chart/charts/user-service/templates/deployment.yaml: error converting YAML to JSON: yaml: line 81: mapping values are not allowed in this context
