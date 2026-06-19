
2026-06-19 09:21:11.604 INFO  [parallel-3] c.f.g.u.LoginUtility: X-Forwarded-For ip : null
{"@timestamp":"2026-06-19T14:51:11.604265166+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.fincore.gateway.utility.LoginUtility","message":"X-Forwarded-For ip : null","stack_trace":""}
2026-06-19 09:21:11.604 INFO  [parallel-3] c.f.g.C.AuthController: Login request for user: v1013333 from IP: /10.0.26.124:50048
{"@timestamp":"2026-06-19T14:51:11.604695239+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.gateway.Controller.AuthController","message":"Login request for user: v1013333 from IP: /10.0.26.124:50048","stack_trace":""}
2026-06-19 09:21:11.620 INFO  [boundedElastic-5] c.f.g.S.LoginServiceImpl: Processing LDAP Login for user: v1013333
{"@timestamp":"2026-06-19T14:51:11.62024317+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.gateway.Service.LoginServiceImpl","message":"Processing LDAP Login for user: v1013333","stack_trace":""}
2026-06-19 09:21:11.620 INFO  [boundedElastic-5] c.f.g.S.AdAuthenticationService: Attempting LDAP Bind for principal: v1013333@UATAD.SBI
{"@timestamp":"2026-06-19T14:51:11.620638545+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.g.Service.AdAuthenticationService","message":"Attempting LDAP Bind for principal: v1013333@UATAD.SBI","stack_trace":""}
2026-06-19 09:21:16.623 ERROR [boundedElastic-5] c.f.g.S.AdAuthenticationService: LDAP CONNECTION ERROR: uatrootdc1.uatad.sbi:3269
{"@timestamp":"2026-06-19T14:51:16.623057706+05:30","level":"ERROR","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.g.Service.AdAuthenticationService","message":"LDAP CONNECTION ERROR: uatrootdc1.uatad.sbi:3269","stack_trace":""}
2026-06-19 09:21:16.623 ERROR [boundedElastic-5] c.f.g.S.LoginServiceImpl: LDAP Server Error for user v1013333: LDAP Server Down
{"@timestamp":"2026-06-19T14:51:16.623406994+05:30","level":"ERROR","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.gateway.Service.LoginServiceImpl","message":"LDAP Server Error for user v1013333: LDAP Server Down","stack_trace":""}
2026-06-19 09:21:16.624 WARN  [boundedElastic-5] c.f.g.C.AuthController: Login Failed for user: v1013333. Reason: System Error: Unable to connect to Authentication Server. Please try again later.
{"@timestamp":"2026-06-19T14:51:16.624109684+05:30","level":"WARN","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.gateway.Controller.AuthController","message":"Login Failed for user: v1013333. Reason: System Error: Unable to connect to Authentication Server. Please try again later.","stack_trace":""}
