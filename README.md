Outline
Loki logo
loki-1

Split

Add to dashboard

Last 6 hours


Run query


Live


A
(loki-1)





Kick start your query

Label browser
Explain query



{job="fluentbit"}|json| pod_name="loki-58595d499c-hqtzg"

Options
Type: Range
Line limit: 1000
Get "http://loki.logging.svc.cluster.local:3100/loki/api/v1/query_range?direction=backward&end=1775113048951000000&limit=1000&query=%7Bjob%3D%22fluentbit%22%7D%7Cjson%7C+pod_name%3D%22loki-58595d499c-hqtzg%22&start=1775091448951000000&step=10000ms": dial tcp 10.101.135.219:3100: connect: connection refused

Add query

Query history

Query inspector




I am getting thio issue 

{job="fluentbit"}|json| pod_name="loki-58595d499c-hqtzg"

Options
Type: Range
Line limit: 1000
Get "http://loki.logging.svc.cluster.local:3100/loki/api/v1/query_range?direction=backward&end=1775113048951000000&limit=1000&query=%7Bjob%3D%22fluentbit%22%7D%7Cjson%7C+pod_name%3D%22loki-58595d499c-hqtzg%22&start=1775091448951000000&step=10000ms": dial tcp 10.101.135.219:3100: connect: connection refused
