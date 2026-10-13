/html>, api_key=5c00203f90d734255c4c60928f68010e, subject=Fincore Notification, toEmail=v1:LUW/lQZCq2GaJDZw:wbKgtTfQmG1GoL3O9O/e4fyu2wow04+0n2o16ZgluuVnnIo4Iw==, url=https://ebmsmg-pepiapi.sbiuat.bank.in:443/v5/mail/send}
2026-10-13T05:36:57.534Z  WARN 1 --- [CommunicationService] [   virtual-1998] org.hibernate.orm.jdbc.warn              : HHH000247: ErrorCode: 28002, SQLState: 99999
2026-10-13T05:36:57.534Z  WARN 1 --- [CommunicationService] [   virtual-1998] org.hibernate.orm.jdbc.warn              : ORA-28002: the password will expire within 2 days

https://docs.oracle.com/error-help/db/ora-28002/
2026-10-13T05:36:57.534Z  WARN 1 --- [CommunicationService] [   virtual-1998] org.hibernate.orm.jdbc.warn              : HHH000247: ErrorCode: 28002, SQLState: 99999
2026-10-13T05:36:57.534Z  WARN 1 --- [CommunicationService] [   virtual-1998] org.hibernate.orm.jdbc.warn              : ORA-28002: the password will expire within 2 days

https://docs.oracle.com/error-help/db/ora-28002/
2026-10-13T05:36:57.568Z ERROR 1 --- [CommunicationService] [   virtual-1996] c.f.C.client.EmailGatewayClient          : Network I/O Exception calling Email Vendor API: 400 Bad Request: "{"error":"Payload validation error","info":"invalid character '-' in numeric literal"}"
2026-10-13T05:36:57.569Z ERROR 1 --- [CommunicationService] [   virtual-1996] c.f.C.service.EmailServiceImpl           : CRITICAL: Bank Email API unreachable for v1:LUW/lQZCq2GaJDZw:wbKgtTfQmG1GoL3O9O/e4fyu2wow04+0n2o16ZgluuVnnIo4Iw==. Error: Network communication with Email Vendor failed
2026-10-13T05:37:01.571Z  INFO 1 --- [CommunicationService] [ntainer#0-0-C-1] c.f.C.o.CommunicationOrchestrator        : Event evt-XmFjrNx4Q3mkMWCrGlTEGg== processed successfully across all chunks.
2026-10-13T05:37:01.578Z  INFO 1 --- [CommunicationService] [ntainer#0-0-C-1] c.f.C.c.GenericCommunicationConsumer     : Successfully processed Generic Communication Event : evt-XmFjrNx4Q3mkMWCrGlTEGg==
2026-10-13T08:32:01.715Z  INFO 1 --- [CommunicationService] [ntainer#1-0-C-1] c.f.C.consumer.PriorityOtpConsumer       : Received raw Kafka message: {"txId":"77dff58a-6b67-46e6-a2a2-57bb67265d65","recipient":{"mobile":"8096858329","email":"rehman.cbstcs@sbi.co.in"},"templateId":"AUTH_LOGIN_OTP_V1","payload":"QQj8rucc4JRASPxJ:BYZ+Ba2wQ+QoDJxbqCeSA0220vjXPT5tgKu1w05bfMBYjkNLn9PmcWDhS+5SAzZusOheSy485JYGCh7fTQabO9n43+nxA3qxnh1koU4=","priority":"CRITICAL","eventId":"evt-3f698432-d369-4624-a464-0b2dd6c321b1","eventType":"LOGIN_OTP","channel":["SMS","EMAIL"],"createdAt":"2026-10-13T08:32:01.044882632Z"}
2026-10-13T08:32:01.724Z ERROR 1 --- [CommunicationService] [ntainer#1-0-C-1] c.f.C.consumer.PriorityOtpConsumer       : SECURITY ALERT: Decryption failed for eventId=evt-3f698432-d369-4624-a464-0b2dd6c321b1. Data tampered or key mismatch.

javax.crypto.AEADBadTagException: Tag mismatch
        at java.base/com.sun.crypto.provider.GaloisCounterMode$GCMDecrypt.doFinal(GaloisCounterMode.java:1518) ~[na:na]
        at java.base/com.sun.crypto.provider.GaloisCounterMode.engineDoFinal(GaloisCounterMode.java:415) ~[na:na]
        at java.base/javax.crypto.Cipher.doFinal(Cipher.java:2252) ~[na:na]
        at com.fincore.commonutilities.util.AesEncryptionUtil.decrypt(AesEncryptionUtil.java:70) ~[common-utilities-2.0.0.jar!/:2.0.0]
        at com.fincore.CommunicationService.consumer.PriorityOtpConsumer.consumeOtpEvent(PriorityOtpConsumer.java:141) ~[!/:0.0.1-SNAPSHOT]
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
        at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
        at org.springframework.messaging.handler.invocation.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:168) ~[spring-messaging-7.0.9.jar!/:7.0.9]
        at org.springframework.kafka.listener.adapter.KotlinAwareInvocableHandlerMethod.doInvoke(KotlinAwareInvocableHandlerMethod.java:48) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.messaging.handler.invocation.InvocableHandlerMethod.invoke(InvocableHandlerMethod.java:119) ~[spring-messaging-7.0.9.jar!/:7.0.9]
        at org.springframework.kafka.listener.adapter.HandlerAdapter.invoke(HandlerAdapter.java:80) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.MessagingMessageListenerAdapter.invokeHandler(MessagingMessageListenerAdapter.java:489) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.MessagingMessageListenerAdapter.invoke(MessagingMessageListenerAdapter.java:426) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.RecordMessagingMessageListenerAdapter.onMessage(RecordMessagingMessageListenerAdapter.java:92) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.RecordMessagingMessageListenerAdapter.onMessage(RecordMessagingMessageListenerAdapter.java:52) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.KafkaBackoffAwareMessageListenerAdapter.invokeDelegateOnMessage(KafkaBackoffAwareMessageListenerAdapter.java:110) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.KafkaBackoffAwareMessageListenerAdapter.onMessage(KafkaBackoffAwareMessageListenerAdapter.java:101) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.KafkaBackoffAwareMessageListenerAdapter.onMessage(KafkaBackoffAwareMessageListenerAdapter.java:51) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeOnMessage(KafkaMessageListenerContainer.java:3099) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeOnMessage(KafkaMessageListenerContainer.java:3078) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeRecordListener(KafkaMessageListenerContainer.java:2988) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeWithRecords(KafkaMessageListenerContainer.java:2806) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeRecordListener(KafkaMessageListenerContainer.java:2692) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeListener(KafkaMessageListenerContainer.java:2323) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeIfHaveRecords(KafkaMessageListenerContainer.java:1621) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.pollAndInvoke(KafkaMessageListenerContainer.java:1523) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.run(KafkaMessageListenerContainer.java:1384) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at java.base/java.util.concurrent.CompletableFuture$AsyncRun.run(CompletableFuture.java:1804) ~[na:na]
        at java.base/java.lang.Thread.run(Thread.java:1570) ~[na:na]

2026-10-13T08:32:01.725Z ERROR 1 --- [CommunicationService] [ntainer#1-0-C-1] c.f.C.consumer.PriorityOtpConsumer       : Fatal deterministic error processing txId=77dff58a-6b67-46e6-a2a2-57bb67265d65. Routing to DLQ. Reason: AES Decryption Failed: Invalid Padding
2026-10-13T08:32:01.726Z ERROR 1 --- [CommunicationService] [ntainer#1-0-C-1] k.r.DeadLetterPublishingRecovererFactory : Record: topic = fincore.auth.otp.priority, partition = 0, offset = 147, main topic = fincore.auth.otp.priority threw an error at topic fincore.auth.otp.priority and won't be retried. Sending to DLT with name fincore.auth.otp.priority-dlq.

org.springframework.kafka.listener.ListenerExecutionFailedException: Listener failed
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.decorateException(KafkaMessageListenerContainer.java:3245) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeOnMessage(KafkaMessageListenerContainer.java:3112) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeOnMessage(KafkaMessageListenerContainer.java:3078) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeRecordListener(KafkaMessageListenerContainer.java:2988) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeWithRecords(KafkaMessageListenerContainer.java:2806) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeRecordListener(KafkaMessageListenerContainer.java:2692) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeListener(KafkaMessageListenerContainer.java:2323) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.invokeIfHaveRecords(KafkaMessageListenerContainer.java:1621) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.pollAndInvoke(KafkaMessageListenerContainer.java:1523) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.run(KafkaMessageListenerContainer.java:1384) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at java.base/java.util.concurrent.CompletableFuture$AsyncRun.run(CompletableFuture.java:1804) ~[na:na]
        at java.base/java.lang.Thread.run(Thread.java:1570) ~[na:na]
Caused by: org.springframework.kafka.listener.TimestampedException: Exception thrown at 2026-10-13T08:32:01.726111421Z
        at org.springframework.kafka.listener.adapter.KafkaBackoffAwareMessageListenerAdapter.onMessage(KafkaBackoffAwareMessageListenerAdapter.java:104) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.KafkaBackoffAwareMessageListenerAdapter.onMessage(KafkaBackoffAwareMessageListenerAdapter.java:51) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.KafkaMessageListenerContainer$ListenerConsumer.doInvokeOnMessage(KafkaMessageListenerContainer.java:3099) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        ... 10 common frames omitted
Caused by: org.springframework.kafka.listener.ListenerExecutionFailedException: Listener method 'public void com.fincore.CommunicationService.consumer.PriorityOtpConsumer.consumeOtpEvent(java.lang.String,org.springframework.kafka.support.Acknowledgment) throws com.fasterxml.jackson.core.JsonProcessingException' threw exception
        at org.springframework.kafka.listener.adapter.MessagingMessageListenerAdapter.invokeHandler(MessagingMessageListenerAdapter.java:514) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.MessagingMessageListenerAdapter.invoke(MessagingMessageListenerAdapter.java:426) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.RecordMessagingMessageListenerAdapter.onMessage(RecordMessagingMessageListenerAdapter.java:92) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.RecordMessagingMessageListenerAdapter.onMessage(RecordMessagingMessageListenerAdapter.java:52) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.KafkaBackoffAwareMessageListenerAdapter.invokeDelegateOnMessage(KafkaBackoffAwareMessageListenerAdapter.java:110) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.KafkaBackoffAwareMessageListenerAdapter.onMessage(KafkaBackoffAwareMessageListenerAdapter.java:101) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        ... 12 common frames omitted
Caused by: com.fincore.CommunicationService.exception.CommunicationExceptions$DecryptionFailureException: AES Decryption Failed: Invalid Padding
        at com.fincore.CommunicationService.consumer.PriorityOtpConsumer.consumeOtpEvent(PriorityOtpConsumer.java:144) ~[!/:0.0.1-SNAPSHOT]
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
        at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
        at org.springframework.messaging.handler.invocation.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:168) ~[spring-messaging-7.0.9.jar!/:7.0.9]
        at org.springframework.kafka.listener.adapter.KotlinAwareInvocableHandlerMethod.doInvoke(KotlinAwareInvocableHandlerMethod.java:48) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.messaging.handler.invocation.InvocableHandlerMethod.invoke(InvocableHandlerMethod.java:119) ~[spring-messaging-7.0.9.jar!/:7.0.9]
        at org.springframework.kafka.listener.adapter.HandlerAdapter.invoke(HandlerAdapter.java:80) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        at org.springframework.kafka.listener.adapter.MessagingMessageListenerAdapter.invokeHandler(MessagingMessageListenerAdapter.java:489) ~[spring-kafka-4.1.1.jar!/:4.1.1]
        ... 17 common frames omitted
Caused by: javax.crypto.AEADBadTagException: Tag mismatch
        at java.base/com.sun.crypto.provider.GaloisCounterMode$GCMDecrypt.doFinal(GaloisCounterMode.java:1518) ~[na:na]
        at java.base/com.sun.crypto.provider.GaloisCounterMode.engineDoFinal(GaloisCounterMode.java:415) ~[na:na]
        at java.base/javax.crypto.Cipher.doFinal(Cipher.java:2252) ~[na:na]
        at com.fincore.commonutilities.util.AesEncryptionUtil.decrypt(AesEncryptionUtil.java:70) ~[common-utilities-2.0.0.jar!/:2.0.0]
        at com.fincore.CommunicationService.consumer.PriorityOtpConsumer.consumeOtpEvent(PriorityOtpConsumer.java:141) ~[!/:0.0.1-SNAPSHOT]
        ... 24 common frames omitted

