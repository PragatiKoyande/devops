org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1788) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:600) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:205) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:952) ~[spring-context-6.1.8.jar!/:6.1.8]
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624) ~[spring-context-6.1.8.jar!/:6.1.8]
        at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:335) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352) ~[spring-boot-3.3.0.jar!/:3.3.0]
        at com.tcs.fincore.CommonRequestService.CommonRequestServiceApplication.main(CommonRequestServiceApplication.java:12) ~[!/:0.0.1]
        at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
        at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:91) ~[app.jar:0.0.1]
        at org.springframework.boot.loader.launch.Launcher.launch(Launcher.java:53) ~[app.jar:0.0.1]
        at org.springframework.boot.loader.launch.JarLauncher.main(JarLauncher.java:58) ~[app.jar:0.0.1]
Caused by: org.hibernate.service.spi.ServiceException: Unable to create requested service [org.hibernate.engine.jdbc.env.spi.JdbcEnvironment] due to: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:276) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.model.relational.Database.<init>(Database.java:45) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:221) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:189) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:171) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1431) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1502) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:390) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:366) ~[spring-orm-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1835) ~[spring-beans-6.1.8.jar!/:6.1.8]
        at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1784) ~[spring-beans-6.1.8.jar!/:6.1.8]
        ... 20 common frames omitted
Caused by: org.hibernate.HibernateException: Unable to determine Dialect without JDBC metadata (please set 'jakarta.persistence.jdbc.url' for common cases or 'hibernate.dialect' when a custom Dialect implementation must be provided)
        at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.determineDialect(DialectFactoryImpl.java:191) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.dialect.internal.DialectFactoryImpl.buildDialect(DialectFactoryImpl.java:87) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentWithDefaults(JdbcEnvironmentInitiator.java:152) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:362) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:123) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:77) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:130) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263) ~[hibernate-core-6.5.2.Final.jar!/:6.5.2.Final]
        ... 35 common frames omitted


here is my yaml ::

# ==============================================================
# SERVICE:     common-request-service
# ENVIRONMENT: dev
# CHART:       charts/backend-service/
# DEPLOY:      helm upgrade --install common-request charts/backend-service/ \
#                -f common-request-service-dev.yaml \
#                -n cbops-test \
#                --kubeconfig hpaa.conf
#
# DRY RUN:     helm upgrade --install common-request charts/backend-service/ \
#                -f common-request-service-dev.yaml \
#                -n cbops-test \
#                --dry-run --debug \
#                --kubeconfig hpaa.conf
# ==============================================================
#
# ⚠️  OBSERVATIONS & GAPS FROM SOURCE YAML (read before deploying):
#
# [GAP 1] — PROBE TYPE MISMATCH
#   Source uses: httpGet /actuator/health on port 9000
#   Chart uses:  tcpSocket on probes.port (hardcoded in deployment.yaml)
#   Impact:      Port connectivity is checked correctly (port 9000 is set).
#                But HTTP path /actuator/health check is NOT performed.
#   Action:      Upgrade chart deployment.yaml probe templates to support
#                httpGet if Spring Boot actuator health check is required.
#
# [GAP 2] — securityContext NOT SUPPORTED IN CHART SCHEMA
#   Source has pod-level securityContext:
#     runAsNonRoot: true
#     runAsUser: 10001
#     fsGroup: 10001
#   Source has container-level securityContext:
#     allowPrivilegeEscalation: false
#     readOnlyRootFilesystem: false
#     capabilities.drop: [ALL]
#   Impact:      These security hardening settings are DROPPED.
#                Pod will run without these constraints.
#   Action:      Add securityContext support to chart deployment.yaml
#                template and values schema for production-grade security.
#
# [GAP 3] — NETWORK POLICY RULES NOT TEMPLATED
#   Source has specific ingress/egress rules:
#     Ingress: allow TCP:9000 from namespace cbops-test only
#     Egress:  allow all namespaces
#   Impact:      networkPolicy.enabled: true creates the NetworkPolicy
#                resource by name only — ingress/egress rules are NOT applied.
#   Action:      Extend templates/networkpolicy.yaml to support
#                ingress/egress rule injection via values.
#
# [GAP 4] — automountServiceAccountToken: false NOT IN SCHEMA
#   Source sets automountServiceAccountToken: false on ServiceAccount.
#   The chart's serviceaccount.yaml does not template this field.
#   Impact:      Token is auto-mounted by default (minor security gap).
#   Action:      Add automountServiceAccountToken: false to
#                templates/serviceaccount.yaml for hardened deployments.
#
# NO DATABASE — This service has no DB credentials in source.
# NO CONFIGMAP — No ConfigMap found in source.
# NO SECRET    — No generic Secret found in source.
# ==============================================================


# ==============================================================
# === Namespace ===
# Always cbops-test per deployment standard.
# ==============================================================
namespace: cbops-test


# ==============================================================
# === Replica Count ===
# ==============================================================
replicaCount: 1


# ==============================================================
# === Image ===
# Private Harbor registry — imagePullSecrets required (see below).
# ==============================================================
image:
  repository: h06vksharbor.corp.ad.sbi/cbops/common-request-service
  tag: DEV08
  pullPolicy: Always


# ==============================================================
# === Image Pull Secrets ===
# Required: image is on private registry h06vksharbor.corp.ad.sbi
#
# Run this ONCE per namespace to create the pull secret:
#   kubectl create secret docker-registry harbor-secret \
#     --docker-server=h06vksharbor.corp.ad.sbi \
#     --docker-username=YOUR_HARBOR_USERNAME \
#     --docker-password=YOUR_HARBOR_PASSWORD \
#     -n cbops-test --kubeconfig hpaa.conf
#
# Verify it exists before deploying:
#   kubectl get secret harbor-secret -n cbops-test --kubeconfig hpaa.conf
# ==============================================================
imagePullSecrets:
  - name: harbor-secret


# ==============================================================
# === Deployment ===
# revisionHistoryLimit: not in source — chart default (5) applied.
# terminationGracePeriodSeconds: 30 matches source exactly.
# ==============================================================
deployment:
  name: common-request-deployment
  revisionHistoryLimit: 5
  terminationGracePeriodSeconds: 30


# ==============================================================
# === Container Name ===
# Explicitly defined in source as "common-request-container".
# Preserved exactly — overrides the default (deployment.name).
# ==============================================================
container:
  name: common-request-container


# ==============================================================
# === Service Account ===
# ==============================================================
serviceAccount:
  name: common-request-sa


# ==============================================================
# === Service ===
# port 80 → targetPort 9000 — preserved exactly from source.
# Other services in the cluster call: http://common-request-service/...
# ==============================================================
service:
  name: common-request-service
  type: ClusterIP
  port: 80
  targetPort: 9000


# ==============================================================
# === Labels ===
# Matches the pod selector label in source Deployment and PDB.
# ==============================================================
labels:
  app: common-request-backend


# ==============================================================
# === Autoscaling (HPA) ===
# HPA found in source → autoscaling.enabled: true
# CPU target: 70% — preserved exactly from source.
# Memory scaling not defined in source → null (disabled).
#
# ⚠️  KEY NAME MUST BE: targetCPUUtilizationPercentage (EXACT)
#     Any other key name is silently ignored by the chart template.
# ==============================================================
autoscaling:
  enabled: true
  name: common-request-hpa
  minReplicas: 1
  maxReplicas: 3
  targetCPUUtilizationPercentage: 70
  targetMemoryUtilizationPercentage: null


# ==============================================================
# === Pod Disruption Budget ===
# PDB found in source → pdb.enabled: true
# Ensures 1 pod always stays running during node drains / upgrades.
# ==============================================================
pdb:
  enabled: true
  name: common-request-pdb
  minAvailable: 1


# ==============================================================
# === Network Policy ===
# NetworkPolicy found in source → networkPolicy.enabled: true
#
# ⚠️  See GAP 3 above — ingress/egress rules from source are not
#     applied by the current chart template. Only the resource
#     name is created. Extend networkpolicy.yaml for full support.
# ==============================================================
networkPolicy:
  enabled: false
  name: common-request-network-policy


# ==============================================================
# === Environment Variables ===
# Redis connection config — non-sensitive, plain key/value.
# Injected directly into the container as env vars.
# ==============================================================


# ==============================================================
# === ConfigMap ===
# No ConfigMap found in source YAML.
# ==============================================================
configMap:
  enabled: false
  data: {}


# ==============================================================
# === Generic Secret ===
# No generic Secret found in source YAML.
# ==============================================================
secret:
  enabled: false
  data: {}


# ==============================================================
# === Database ===
# No database credentials found in source YAML.
# This service does not use Oracle, PostgreSQL, or any other DB.
# ==============================================================
database:
  enabled: true
  existingSecret: ""
  url: "jdbc:oracle:thin:@10.177.103.192:1523/fincorepdb1"
  username: "fincore"
  password: "Password#1234"
  driverClassName: "oracle.jdbc.OracleDriver"


# ==============================================================
# === Resources ===
# Preserved exactly from source.
# JVM tip: if Spring Boot OOMKills occur, set -Xmx410m (~80% of 512Mi).
# ==============================================================
resources:
  requests:
    cpu: "200m"
    memory: "256Mi"
  limits:
    cpu: "500m"
    memory: "512Mi"


# ==============================================================
# === Probes Port ===
# Spring Boot app listens on port 9000 (server.port=9000).
# All probes check this port — see GAP 1 above re: httpGet vs tcpSocket.
# Named port "http" in deployment.yaml resolves to this value.
# Service targetPort "http" also resolves to this port.
# ==============================================================
probes:
  port: 9000


        
