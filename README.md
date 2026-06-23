kubectl delete secret jfrog-secret -n backend

kubectl create secret docker-registry jfrog-secret \
  --docker-server=artifactory.jfrog.sbi:443 \
  --docker-username=<username> \
  --docker-password=<password> \
  --docker-email=<email> \
  -n backend