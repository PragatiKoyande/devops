curl -k -X POST https://<broker>:8283/druid/v2/sql \
-H "Content-Type: application/json" \
-d '{"query":"SELECT 1"}'

find /media/production-setup/apache-druid-34.0.0/log -type f -mmin -2


grep -R "SELECT 1" /media/production-setup/apache-druid-34.0.0/log