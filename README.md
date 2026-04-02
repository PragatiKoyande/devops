Get "http://loki.logging.svc.cluster.local:3100/loki/api/v1/query_range?direction=backward&end=1775134146318000000&limit=1000&query=%7Bjob%3D%22fluentbit%22%7D+%7C+json+%7C+container_name%3D%22transactions-container%22+%7C+json+%7C+line_format+%22%7B%7B.message%7D%7D%22&start=1775047746318000000&step=1800000ms": dial tcp 10.100.231.250:3100: connect: connection refused

this issue coming on grafana
