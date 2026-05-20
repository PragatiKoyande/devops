apiVersion: v2
name: umbrella-chart
description: Umbrella Chart
type: application
version: 0.1.0
appVersion: "1.0"

dependencies:
  - name: dashboard
    version: 0.1.0
    repository: "file://../dashboard"
    condition: dashboard.enabled

  - name: journal
    version: 0.1.0
    repository: "file://../journal"
    condition: journal.enabled

  - name: transactions
    version: 0.1.0
    repository: "file://../transactions"
    condition: transactions.enabled

  - name: user-service
    version: 0.1.0
    repository: "file://../user-service"
    condition: user-service.enabled

  - name: process-status
    version: 0.1.0
    repository: "file://../process-status"
    condition: process-status.enabled

  - name: enqiry-service
    version: 0.1.0
    repository: "file://../enqiry-service"
    condition: enqiry-service.enabled

  - name: notification
    version: 0.1.0
    repository: "file://../notification"
    condition: notification.enabled

  - name: nwsa-service
    version: 0.1.0
    repository: "file://../nwsa-service"
    condition: nwsa-service.enabled

  - name: react-service
    version: 0.1.0
    repository: "file://../react-service"
    condition: react-service.enabled

  - name: redis-service
    version: 0.1.0
    repository: "file://../redis-service"
    condition: redis-service.enabled

  - name: report-builder
    version: 0.1.0
    repository: "file://../report-builder"
    condition: report-builder.enabled

  - name: report-service
    version: 0.1.0
    repository: "file://../report-service"
    condition: report-service.enabled

  - name: template-config
    version: 0.1.0
    repository: "file://../template-config"
    condition: template-config.enabled

  - name: common-master
    version: 0.1.0
    repository: "file://../common-master"
    condition: common-master.enabled

  - name: common-request
    version: 0.1.0
    repository: "file://../common-request"
    condition: common-request.enabled

  - name: login
    version: 0.1.0
    repository: "file://../login"
    condition: login.enabled