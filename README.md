{
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "grafana",
          "uid": "-- Grafana --"
        },
        "enable": true,
        "hide": true,
        "iconColor": "rgba(0, 211, 255, 1)",
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "description": "Logs for all Backend services",
  "editable": true,
  "fiscalYearStartMonth": 0,
  "graphTooltip": 0,
  "id": 2,
  "links": [],
  "liveNow": false,
  "panels": [
    {
      "datasource": {},
      "description": "Deployment name = user-deployment\nContainer name = user-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 0,
        "y": 0
      },
      "id": 14,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"user-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "user-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = report-deployment\nContainer name = report-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 8,
        "y": 0
      },
      "id": 11,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\",\r\ncontainer=\"report-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "report-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment Name = common-request-deployment\nContainer Name = common-request-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 16,
        "y": 0
      },
      "id": 3,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"common-request-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "common-request-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = template-config-deployment\nContainer name = template-config-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 14
      },
      "id": 12,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"template-config-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "template-config-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = transactions-deployment\nContainer name = transactions-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 14
      },
      "id": 13,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"transactions-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "transactions-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = redis-deployment\nContainer name = redis-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 14
      },
      "id": 9,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"redis-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "redis-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = report-builder-deployment\nContainer name = report-builder-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 29
      },
      "id": 10,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"report-builder-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "report-builder-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = notification-deployment\nContainer name = notification-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 29
      },
      "id": 7,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"notification-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "notification-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = process-status-deployment\nContainer name = process-status-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 29
      },
      "id": 8,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"process-status-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "process-status-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = login-deployment\nContainer name = login-backend-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 44
      },
      "id": 6,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"login-backend-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "login-backend-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = journal-deployment\nContainer name = journal-app-container ",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 44
      },
      "id": 5,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"journal-app-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "journal-app-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment Name = dashboard-deployment\nContainer Name = dashboard-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 44
      },
      "id": 4,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"dashboard-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "dashboard-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = common-master-deployment\nContainer name = common-master-container",
      "gridPos": {
        "h": 14,
        "w": 24,
        "x": 0,
        "y": 59
      },
      "id": 2,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"common-master-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "common-master-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    }
  ],
  "refresh": "5s",
  "schemaVersion": 39,
  "tags": [],
  "templating": {
    "list": []
  },
  "time": {
    "from": "now-5m",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "",
  "title": "BACKEND-SERVICES",
  "uid": "aa93f363-13da-48e4-8ade-a3f2f89468f5",
  "version": 40,
  "weekStart": ""
}{
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "grafana",
          "uid": "-- Grafana --"
        },
        "enable": true,
        "hide": true,
        "iconColor": "rgba(0, 211, 255, 1)",
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "description": "Logs for all Backend services",
  "editable": true,
  "fiscalYearStartMonth": 0,
  "graphTooltip": 0,
  "id": 2,
  "links": [],
  "liveNow": false,
  "panels": [
    {
      "datasource": {},
      "description": "Deployment name = user-deployment\nContainer name = user-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 0,
        "y": 0
      },
      "id": 14,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"user-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "user-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = report-deployment\nContainer name = report-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 8,
        "y": 0
      },
      "id": 11,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\",\r\ncontainer=\"report-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "report-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment Name = common-request-deployment\nContainer Name = common-request-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 16,
        "y": 0
      },
      "id": 3,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"common-request-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "common-request-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = template-config-deployment\nContainer name = template-config-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 14
      },
      "id": 12,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"template-config-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "template-config-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = transactions-deployment\nContainer name = transactions-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 14
      },
      "id": 13,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"transactions-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "transactions-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = redis-deployment\nContainer name = redis-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 14
      },
      "id": 9,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"redis-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "redis-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = report-builder-deployment\nContainer name = report-builder-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 29
      },
      "id": 10,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"report-builder-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "report-builder-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = notification-deployment\nContainer name = notification-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 29
      },
      "id": 7,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"notification-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "notification-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = process-status-deployment\nContainer name = process-status-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 29
      },
      "id": 8,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"process-status-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "process-status-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = login-deployment\nContainer name = login-backend-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 44
      },
      "id": 6,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"login-backend-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "login-backend-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = journal-deployment\nContainer name = journal-app-container ",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 44
      },
      "id": 5,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"journal-app-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "journal-app-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment Name = dashboard-deployment\nContainer Name = dashboard-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 44
      },
      "id": 4,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"dashboard-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "dashboard-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = common-master-deployment\nContainer name = common-master-container",
      "gridPos": {
        "h": 14,
        "w": 24,
        "x": 0,
        "y": 59
      },
      "id": 2,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"common-master-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "common-master-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    }
  ],
  "refresh": "5s",
  "schemaVersion": 39,
  "tags": [],
  "templating": {
    "list": []
  },
  "time": {
    "from": "now-5m",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "",
  "title": "BACKEND-SERVICES",
  "uid": "aa93f363-13da-48e4-8ade-a3f2f89468f5",
  "version": 40,
  "weekStart": ""
}{
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "grafana",
          "uid": "-- Grafana --"
        },
        "enable": true,
        "hide": true,
        "iconColor": "rgba(0, 211, 255, 1)",
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "description": "Logs for all Backend services",
  "editable": true,
  "fiscalYearStartMonth": 0,
  "graphTooltip": 0,
  "id": 2,
  "links": [],
  "liveNow": false,
  "panels": [
    {
      "datasource": {},
      "description": "Deployment name = user-deployment\nContainer name = user-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 0,
        "y": 0
      },
      "id": 14,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"user-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "user-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = report-deployment\nContainer name = report-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 8,
        "y": 0
      },
      "id": 11,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\",\r\ncontainer=\"report-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "report-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment Name = common-request-deployment\nContainer Name = common-request-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 16,
        "y": 0
      },
      "id": 3,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"common-request-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "common-request-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = template-config-deployment\nContainer name = template-config-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 14
      },
      "id": 12,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"template-config-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "template-config-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = transactions-deployment\nContainer name = transactions-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 14
      },
      "id": 13,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"transactions-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "transactions-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = redis-deployment\nContainer name = redis-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 14
      },
      "id": 9,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"redis-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "redis-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = report-builder-deployment\nContainer name = report-builder-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 29
      },
      "id": 10,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"report-builder-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "report-builder-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = notification-deployment\nContainer name = notification-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 29
      },
      "id": 7,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"notification-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "notification-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = process-status-deployment\nContainer name = process-status-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 29
      },
      "id": 8,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"process-status-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "process-status-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = login-deployment\nContainer name = login-backend-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 44
      },
      "id": 6,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"login-backend-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "login-backend-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = journal-deployment\nContainer name = journal-app-container ",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 44
      },
      "id": 5,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"journal-app-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "journal-app-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment Name = dashboard-deployment\nContainer Name = dashboard-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 44
      },
      "id": 4,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"dashboard-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "dashboard-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = common-master-deployment\nContainer name = common-master-container",
      "gridPos": {
        "h": 14,
        "w": 24,
        "x": 0,
        "y": 59
      },
      "id": 2,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"common-master-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "common-master-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    }
  ],
  "refresh": "5s",
  "schemaVersion": 39,
  "tags": [],
  "templating": {
    "list": []
  },
  "time": {
    "from": "now-5m",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "",
  "title": "BACKEND-SERVICES",
  "uid": "aa93f363-13da-48e4-8ade-a3f2f89468f5",
  "version": 40,
  "weekStart": ""
}{
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "grafana",
          "uid": "-- Grafana --"
        },
        "enable": true,
        "hide": true,
        "iconColor": "rgba(0, 211, 255, 1)",
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "description": "Logs for all Backend services",
  "editable": true,
  "fiscalYearStartMonth": 0,
  "graphTooltip": 0,
  "id": 2,
  "links": [],
  "liveNow": false,
  "panels": [
    {
      "datasource": {},
      "description": "Deployment name = user-deployment\nContainer name = user-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 0,
        "y": 0
      },
      "id": 14,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"user-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "user-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = report-deployment\nContainer name = report-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 8,
        "y": 0
      },
      "id": 11,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\",\r\ncontainer=\"report-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "report-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment Name = common-request-deployment\nContainer Name = common-request-container",
      "gridPos": {
        "h": 14,
        "w": 8,
        "x": 16,
        "y": 0
      },
      "id": 3,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"common-request-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "common-request-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = template-config-deployment\nContainer name = template-config-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 14
      },
      "id": 12,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"template-config-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "template-config-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = transactions-deployment\nContainer name = transactions-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 14
      },
      "id": 13,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"transactions-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "transactions-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = redis-deployment\nContainer name = redis-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 14
      },
      "id": 9,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"redis-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "redis-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = report-builder-deployment\nContainer name = report-builder-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 29
      },
      "id": 10,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "code",
          "expr": "{namespace=\"be-test\", container=\"report-builder-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "report-builder-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = notification-deployment\nContainer name = notification-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 29
      },
      "id": 7,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"notification-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "notification-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {
        "type": "loki",
        "uid": "c4b0305c-d8d5-44c9-98ae-cca6f7b7f6d4"
      },
      "description": "Deployment name = process-status-deployment\nContainer name = process-status-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 29
      },
      "id": 8,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"process-status-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "process-status-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = login-deployment\nContainer name = login-backend-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 0,
        "y": 44
      },
      "id": 6,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"login-backend-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "login-backend-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = journal-deployment\nContainer name = journal-app-container ",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 8,
        "y": 44
      },
      "id": 5,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"journal-app-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "journal-app-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment Name = dashboard-deployment\nContainer Name = dashboard-container",
      "gridPos": {
        "h": 15,
        "w": 8,
        "x": 16,
        "y": 44
      },
      "id": 4,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"dashboard-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "dashboard-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    },
    {
      "datasource": {},
      "description": "Deployment name = common-master-deployment\nContainer name = common-master-container",
      "gridPos": {
        "h": 14,
        "w": 24,
        "x": 0,
        "y": 59
      },
      "id": 2,
      "options": {
        "dedupStrategy": "exact",
        "enableLogDetails": true,
        "prettifyLogMessage": false,
        "showCommonLabels": false,
        "showLabels": false,
        "showTime": true,
        "sortOrder": "Ascending",
        "wrapLogMessage": true
      },
      "targets": [
        {
          "datasource": {
            "type": "loki",
            "uid": "c334504e-7a20-499f-9eab-fe02b6fb7026"
          },
          "editorMode": "builder",
          "expr": "{namespace=\"be-test\", container=\"common-master-container\"} | json | line_format \"{{.level}} {{.log}}\"",
          "queryType": "range",
          "refId": "A"
        }
      ],
      "title": "common-master-service",
      "transformations": [],
      "transparent": true,
      "type": "logs"
    }
  ],
  "refresh": "5s",
  "schemaVersion": 39,
  "tags": [],
  "templating": {
    "list": []
  },
  "time": {
    "from": "now-5m",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "",
  "title": "BACKEND-SERVICES",
  "uid": "aa93f363-13da-48e4-8ade-a3f2f89468f5",
  "version": 40,
  "weekStart": ""
}

please correct this file I m getting this issue: Import failed
JSON -> JS Serialization failed: Unexpected non-whitespace character after JSON at position 15247 (line 536 column 2)
