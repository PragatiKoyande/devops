I wanted to setup helm for my entire setup so let me start from giving you brief about my application, I have having total 4 environments: dev, st, uat and prod. Having 1 react microservice application as my frontend and backned i have spring boot applications total 13 or 14 microservices. In which also I have kafka and few minor things related to applications like db and ladp services. Now I want to make all this or convert it into helm, right now I am having normal deployment I go in every file and edit file and use kubectl to apply. Now my requirement is I want automation between all environments and also I want to make use of environmnet variables and not the hard coded values as I am referring lots of secrtes and configmaps which are different for different environments and also some are common for all 4 environments. and also I want proper directory structure for all the microservices and environmnets I wanted so smooth that i can only change at one place and it will get apply.

I am not having that much knowlegde on helm i m completely new lets go step by step if you want before deploying things you make me understand the working of helm and give me more knowldege and later we can start with the deployment part below I m keeping my application details: 

Microservices - frontend and backend
common-master-deployment
common-request-deployment
dashboard-deployment
journal-deployment
login-deployment
notification-deployment
process-status-deployment
react-deployment -- frontend
redis-server-deployment 
report-builder-deployment
report-deployment
template-config-deployment
transactions-deployment
user-deployment

Kafka related things -
Kafka-connect-server
sit-apache-kafka 
sit-kafka-connect
sit-kafka-ui

These are configmaps and secrtes required for my applications-
hadoop-config
kafka-config
ldap-config
ldap-secret
oracle-config
oracle-secret
postgres-config
postgres-secret
redis-config
