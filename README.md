{{- if .Values.pdb.enabled }}
apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ .Values.name }}-pdb
  namespace: {{ .Values.namespace }}
spec:
  minAvailable: {{ .Values.pdb.minAvailable }}
  selector:
    matchLabels:
      app: {{ .Values.name }}-backend
{{- end }}

also tell me whether this file is aligned with my values.yaml?? below is my values.yaml file:

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

  container:
    name: user-container
    image: a2p05vksharbor.corp.ad.sbi/cbops/user-service:PR-04
    imagePullPolicy: Always

    port: 8087

    env:
      - name: SPRING_PROFILES_ACTIVE
        value: "prod"
      - name: JAVA_TOOL_OPTIONS
        value: "-Djava.net.preferIPv4Stack=true"
      - name: SPRING_KAFKA_CONSUMER_GROUP_ID
        value: "rbac-cache-group"

    envFrom:
      configMaps:
        - oracle-config
        - kafka-config
        - redis-config
        - ldap-config
      secrets:
        - oracle-secret
        - ldap-secret

    volumeMounts:
      - name: truststore-volume
        mountPath: /etc/fincore/secrets
        readOnly: true

    resources:
      requests:
        cpu: "200m"
        memory: "256Mi"
      limits:
        cpu: "500m"
        memory: "512Mi"

    probes:
      startup:
        port: 8087
        failureThreshold: 60
        periodSeconds: 10

      liveness:
        port: 8087
        initialDelaySeconds: 90
        periodSeconds: 15
        timeoutSeconds: 5
        failureThreshold: 5

      readiness:
        port: 8087
        initialDelaySeconds: 30
        periodSeconds: 10
        timeoutSeconds: 5
        failureThreshold: 5

    lifecycle:
      preStopSleep: 10

  volumes:
    - name: truststore-volume
      secret:
        secretName: ldap-truststore-file
        items:
          - key: ad-truststore.jks
            path: ad-truststore.jks

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 2000

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

service:
  name: user-service
  type: ClusterIP
  port: 80
  targetPort: 8087

hpa:
  name: user-hpa
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70
  behavior:
    scaleUpStabilization: 60
    scaleDownStabilization: 300

pdb:
  name: user-pdb
  minAvailable: 1
