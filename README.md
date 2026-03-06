kubectl patch pvc kafka-data-kafka-0 \
-n backend \
-p '{"metadata":{"finalizers":[]}}' \
--type=merge \
--kubeconfig h06vksuatcbopscls.conf