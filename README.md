apiVersion: v2
name: umbrella-chart
description: Umbrella Chart
type: application
version: 0.1.0
appVersion: "1.0"

dependencies:
  - name: dashboard-service
    version: 0.1.0
    repository: "file://../dashboard-service"
    condition: dashboard-service.enabled

  - name: journal-service
    version: 0.1.0
    repository: "file://../journal-service"
    condition: journal-service.enabled

  - name: transactions-service
    version: 0.1.0
    repository: "file://../transactions-service"
    condition: transactions-service.enabled

  - name: user-service
    version: 0.1.0
    repository: "file://../user-service"
    condition: user-service.enabled

  - name: process-status-service
    version: 0.1.0
    repository: "file://../process-status-service"
    condition: process-status-service.enabled

  - name: enquiry-service
    version: 0.1.0
    repository: "file://../enquiry-service"
    condition: enquiry-service.enabled

  - name: notification-service
    version: 0.1.0
    repository: "file://../notification-service"
    condition: notification-service.enabled

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

  - name: report-builder-service
    version: 0.1.0
    repository: "file://../report-builder-service"
    condition: report-builder-service.enabled

  - name: report-service
    version: 0.1.0
    repository: "file://../report-service"
    condition: report-service.enabled

  - name: template-config-service
    version: 0.1.0
    repository: "file://../template-config-service"
    condition: template-config-service.enabled

  - name: common-master-service
    version: 0.1.0
    repository: "file://../common-master-service"
    condition: common-master-service.enabled

  - name: common-request-service
    version: 0.1.0
    repository: "file://../common-request-service"
    condition: common-request-service.enabled

  - name: login-service
    version: 0.1.0
    repository: "file://../login-service"
    condition: login-service.enabled
	
  - name: help-service
    version: 0.1.0
    repository: "file://../help-service"
    condition: help-service.enabled
	
  - name: ascii-generation-service
    version: 0.1.0
    repository: "file://../ascii-generation-service"
    condition: ascii-generation-service.enabled
	
  - name: voucher-enquiry-service
    version: 0.1.0
    repository: "file://../voucher-enquiry-service"
    condition: voucher-enquiry-service.enabled



    this is my chart.yaml


    and i m getting this error:

    
D:\Pragati\HELM-2404\Deployment\umbrella-chart>helm dependency update
Error: cannot load Chart.yaml: error converting YAML to JSON: yaml: line 88: found a tab character that violates indentation


kindly resolve the issue and send me back entire chart.yaml file
