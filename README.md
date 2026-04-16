apiVersion: v2
name: notification-service
description: Notification Service Helm Chart
type: application
version: 0.1.0
appVersion: "1.0"



name: notification-backend
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

autoscaling:
  enabled: true
  minReplicas: 1
  maxReplicas: 5
  cpuUtilization: 70

pdb:
  enabled: true
  minAvailable: 1

resources:
  requests:
    cpu: "250m"
    memory: "512Mi"
  limits:
    cpu: "500m"
    memory: "1Gi"

envFrom:
  configMaps:
    - redis-config
    - kafka-config
    - postgres-config
  secrets:
    - postgres-secret

extraEnv:
  - name: SPRING_KAFKA_CONSUMER_GROUP_ID
    value: "notification-service-group"
  - name: SPRING_KAFKA_CONSUMER_AUTO_OFFSET_RESET
    value: "earliest"

secretEnv: []

volumes:
  - name: tmp-dir
    emptyDir:
      medium: Memory
      sizeLimit: 64Mi
  - name: logs-volume
    emptyDir: {}

volumeMounts:
  - name: tmp-dir
    mountPath: /tmp
  - name: logs-volume
    mountPath: /logs

hostAliases: []