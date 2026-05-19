namespace: backend

serviceAccount:
  name: user-sa

deployment:
  name: user-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: user-backend

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

  serviceAccountName: user-sa
  terminationGracePeriodSeconds: 30
  enableServiceLinks: false

  volumes:
    - name: truststore-volume
      secret:
        secretName: ldap-truststore-file
        items:
          - key: ad-truststore.jks
            path: ad-truststore.jks

  volumeMounts:
    - name: truststore-volume
      mountPath: /etc/fincore/secrets
      readOnly: true

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: user-backend

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/user-service
  tag: DEV06
  imagePullPolicy: Always        # ← ADDED (was missing, rendered as empty)

container:
  name: user-container
  port: 8087

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

probes:
  port: 8087

  startup:
    failureThreshold: 60
    periodSeconds: 10

  liveness:
    initialDelaySeconds: 90
    periodSeconds: 15
    timeoutSeconds: 5
    failureThreshold: 5

  readiness:
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 5

envCommon:
  - name: LDAP_TRUSTSTORE_PASSWORD
    valueFrom:
      secretKeyRef:
        name: ldap-creds
        key: truststore-password

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

env: []                          # ← ADDED (was missing entirely)

hostAliases: []                  # ← ADDED (was missing entirely)

lifecycle: {}                    # ← ADDED (was missing entirely)

containerSecurityContext: {}     # ← ADDED (was missing entirely)

service:
  name: user-service
  port: 80
  targetPort: 8087
  type: ClusterIP

hpa:
  name: user-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

pdb:
  name: user-pdb
  minAvailable: 1