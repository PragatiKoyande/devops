
2026-06-19 06:54:20.142 INFO  [parallel-4] c.f.g.u.LoginUtility: X-Forwarded-For ip : null
{"@timestamp":"2026-06-19T12:24:20.142470205+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.fincore.gateway.utility.LoginUtility","message":"X-Forwarded-For ip : null","stack_trace":""}
2026-06-19 06:54:20.143 INFO  [parallel-4] c.f.g.C.AuthController: Check-User info user id: v1023950 , ip : /10.0.19.45:23025
{"@timestamp":"2026-06-19T12:24:20.143074448+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.gateway.Controller.AuthController","message":"Check-User info user id: v1023950 , ip : /10.0.19.45:23025","stack_trace":""}
2026-06-19 06:54:28.637 INFO  [parallel-5] c.f.g.u.LoginUtility: X-Forwarded-For ip : null
{"@timestamp":"2026-06-19T12:24:28.637789671+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.fincore.gateway.utility.LoginUtility","message":"X-Forwarded-For ip : null","stack_trace":""}
2026-06-19 06:54:28.638 INFO  [parallel-5] c.f.g.C.AuthController: Login request for user: v1023950 from IP: /10.0.19.45:23025
{"@timestamp":"2026-06-19T12:24:28.638350137+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.gateway.Controller.AuthController","message":"Login request for user: v1023950 from IP: /10.0.19.45:23025","stack_trace":""}
2026-06-19 06:54:28.694 INFO  [boundedElastic-1] c.f.g.S.LoginServiceImpl: Processing LDAP Login for user: v1023950
{"@timestamp":"2026-06-19T12:24:28.694050987+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.gateway.Service.LoginServiceImpl","message":"Processing LDAP Login for user: v1023950","stack_trace":""}
2026-06-19 06:54:28.694 INFO  [boundedElastic-1] c.f.g.S.AdAuthenticationService: Attempting LDAP Bind for principal: v1023950@UATAD.SBI
{"@timestamp":"2026-06-19T12:24:28.694780836+05:30","level":"INFO","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.g.Service.AdAuthenticationService","message":"Attempting LDAP Bind for principal: v1023950@UATAD.SBI","stack_trace":""}
2026-06-19 06:54:33.704 ERROR [boundedElastic-1] c.f.g.S.AdAuthenticationService: LDAP CONNECTION ERROR: uatrootdc1.uatad.sbi:3269
{"@timestamp":"2026-06-19T12:24:33.704218587+05:30","level":"ERROR","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.g.Service.AdAuthenticationService","message":"LDAP CONNECTION ERROR: uatrootdc1.uatad.sbi:3269","stack_trace":""}
2026-06-19 06:54:33.704 ERROR [boundedElastic-1] c.f.g.S.LoginServiceImpl: LDAP Server Error for user v1023950: LDAP Server Down
{"@timestamp":"2026-06-19T12:24:33.704665232+05:30","level":"ERROR","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.gateway.Service.LoginServiceImpl","message":"LDAP Server Error for user v1023950: LDAP Server Down","stack_trace":""}
2026-06-19 06:54:33.710 WARN  [boundedElastic-1] c.f.g.C.AuthController: Login Failed for user: v1023950. Reason: System Error: Unable to connect to Authentication Server. Please try again later.
{"@timestamp":"2026-06-19T12:24:33.71091837+05:30","level":"WARN","service":"LoginService","traceId":"","userId":"","clientIp":"","apiPath":"","class":"c.f.gateway.Controller.AuthController","message":"Login Failed for user: v1023950. Reason: System Error: Unable to connect to Authentication Server. Please try again later.","stack_trace":""}
