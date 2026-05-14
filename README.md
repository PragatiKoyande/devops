apiVersion: v2
name: platform
description: Enterprise Platform Deployment
type: application
version: 1.0.0

dependencies:

  - name: common-master
    version: 0.1.0
    repository: "file://../common-master"

  - name: common-request
    version: 0.1.0
    repository: "file://../common-request"

  - name: dashboard
    version: 0.1.0
    repository: "file://../dashboard"

  - name: enqiry-service
    version: 0.1.0
    repository: "file://../enqiry-service"

  - name: journal
    version: 0.1.0
    repository: "file://../journal"

  - name: login
    version: 0.1.0
    repository: "file://../login"

  - name: notification
    version: 0.1.0
    repository: "file://../notification"

  - name: nwsa-service
    version: 0.1.0
    repository: "file://../nwsa-service"

  - name: process-status
    version: 0.1.0
    repository: "file://../process-status"

  - name: react-service
    version: 0.1.0
    repository: "file://../react-service"

  - name: redis-service
    version: 0.1.0
    repository: "file://../redis-service"

  - name: report-builder
    version: 0.1.0
    repository: "file://../report-builder"

  - name: report-service
    version: 0.1.0
    repository: "file://../report-service"

  - name: template-config
    version: 0.1.0
    repository: "file://../template-config"

  - name: transactions
    version: 0.1.0
    repository: "file://../transactions"

  - name: user-service
    version: 0.1.0
    repository: "file://../user-service"




global:
  environment: dev

common-master:
  image:
    tag: dev

dashboard:
  image:
    tag: dev




global:
  environment: uat

common-master:
  image:
    tag: uat

dashboard:
  image:
    tag: uat




global:
  environment: prod

common-master:
  image:
    tag: prod

dashboard:
  image:
    tag: prod