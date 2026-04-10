name: notification
namespace: backend

replicaCount: 1

image:
  repository: h06vksharbor.corp.ad.sbi/cbops/notification-service
  tag: TEST-1
  pullPolicy: Always

serviceAccount:
  name: notification-sa

service:
  name: notification-service
  port: 80
  targetPort: 9010
  type: ClusterIP

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

configMaps:
  - redis-config
  - kafka-config
  - postgres-config

secretRefs:
  - postgres-secret

env:
  SPRING_KAFKA_CONSUMER_GROUP_ID: "notification-service-group"
  SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET: "earliest"

volumes:
  tmp:
    sizeLimit: 64Mi
    mountPath: /tmp
  logs:
    mountPath: /logs

securityContext:
  runAsUser: 1000
  runAsGroup: 1000
  fsGroup: 2000
  readOnlyRootFilesystem: true

hpa:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

pdb:
  minAvailable: 1