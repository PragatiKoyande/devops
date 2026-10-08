[root@fcuatgateway ENV-Changes]# k get secret kafka-aes-secret -o jsonpath='{.data}' | jq 'keys'
[
  "KAFKA_AES_SECRET"
]
