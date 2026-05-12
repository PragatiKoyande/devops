D:\Pragati\HELM-2404\Deployment\enqiry-service>helm install enquiry-service-dev . -f values-dev.yaml -n backend --kubeconfig h06vksuatcbopscls.conf
Error: INSTALLATION FAILED: enquiry-service/templates/pdb.yaml:4:18
  executing "enquiry-service/templates/pdb.yaml" at <.Values.pdb.name>:
    nil pointer evaluating interface {}.name


    I m getting this issue as you have not mentioned details of pdb configuartion in values.yaml I m sending you the both files pdb and values .yaml please  take information from pdb file and add values in values . yaml and send me back entire values.yaml correct one 



    pdb.yaml:

    apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: {{ .Values.pdb.name }}
  namespace: {{ .Values.namespace }}

spec:
  minAvailable: {{ .Values.pdb.minAvailable }}

  selector:
    matchLabels:
      app: {{ .Values.deployment.labels.app }}



      values.yaml:

      namespace: backend

serviceAccount:
  name: enquiry-service-sa
  automountServiceAccountToken: false

deployment:
  name: enquiry-service-deployment
  replicas: 1
  revisionHistoryLimit: 5

  strategy:
    type: RollingUpdate
    maxUnavailable: 0
    maxSurge: 1

  labels:
    app: enquiry-service-backend

  terminationGracePeriodSeconds: 60

  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    runAsGroup: 1000
    fsGroup: 1000
    seccompProfile:
      type: RuntimeDefault

  topologySpreadConstraints:
    - maxSkew: 1
      topologyKey: kubernetes.io/hostname
      whenUnsatisfiable: ScheduleAnyway
      labelSelector:
        matchLabels:
          app: enquiry-service-backend

container:
  name: enquiry-service-container

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/enquiry-service
  tag: DEV03
  imagePullPolicy: Always

envFrom:
  - secretRef:
      name: oracle-secret

service:
  name: enquiry-service
  port: 80
  targetPort: 4001

probes:
  port: 4001

  startup:
    port: 4001
    initialDelaySeconds: 20
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 30

  liveness:
    port: 4001
    initialDelaySeconds: 60
    periodSeconds: 20
    timeoutSeconds: 5
    failureThreshold: 5

  readiness:
    port: 4001
    initialDelaySeconds: 30
    periodSeconds: 10
    timeoutSeconds: 5
    failureThreshold: 3

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"

  limits:
    cpu: "1000m"
    memory: "1Gi"

containerSecurityContext:
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: false
  capabilities:
    drop:
      - ALL

lifecycle:
  preStop:
    exec:
      command:
        - /bin/sh
        - -c
        - sleep 20

hpa:
  name: enquiry-service-hpa
  minReplicas: 1
  maxReplicas: 5
  cpu: 70

  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
      policies:
        - type: Percent
          value: 100
          periodSeconds: 60

    scaleDown:
      stabilizationWindowSeconds: 300
      policies:
        - type: Percent
          value: 50
          periodSeconds: 60
