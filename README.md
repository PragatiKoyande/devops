apiVersion: v1
kind: Secret
metadata:
  name: oracle-secret
  namespace: backend

type: Opaque

data:
  SPRING_DATASOURCE_USERNAME: fincore
  SPRING_DATASOURCE_PASSWORD: Password#1234

  want to base encode the username and password kindly send me the command for the same 
