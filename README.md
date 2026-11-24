
apiVersion: v1
kind: Pod
metadata:
  name: debezium-reset
  namespace: backend
spec:
  restartPolicy: Never
  securityContext:
    runAsUser: 0
    runAsGroup: 0
  containers:
    - name: reset
      image: h06vksharbor.corp.ad.sbi/cbops/debezium-server:oracle-v1
      command: ["/bin/sh", "-c", "sleep 3600"]
      securityContext:
        runAsUser: 0
        runAsGroup: 0
      volumeMounts:
        - name: data-volume
          mountPath: /debezium/data
  volumes:
    - name: data-volume
      persistentVolumeClaim:
        claimName: debezium-pvc
