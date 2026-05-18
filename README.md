apiVersion: v2
name: umbrella-chart
description: Enterprise Umbrella Chart for CBOPS Platform
type: application
version: 0.1.0
appVersion: "1.0"

dependencies:
  - name: dashboard
    version: 0.1.0
    repository: "file://../dashboard"

  - name: journal
    version: 0.1.0
    repository: "file://../journal"

  - name: transactions
    version: 0.1.0
    repository: "file://../transactions"

  - name: user-service
    version: 0.1.0
    repository: "file://../user-service"

  - name: process-status
    version: 0.1.0
    repository: "file://../process-status"

  - name: enqiry-service
    version: 0.1.0
    repository: "file://../enqiry-service"

  - name: notification
    version: 0.1.0
    repository: "file://../notification"

  - name: nwsa-service
    version: 0.1.0
    repository: "file://../nwsa-service"

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

  - name: common-master
    version: 0.1.0
    repository: "file://../common-master"

  - name: common-request
    version: 0.1.0
    repository: "file://../common-request"

  - name: login
    version: 0.1.0
    repository: "file://../login"