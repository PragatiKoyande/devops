1) umbrella-chart/values.yaml

dashboard:
  enabled: true

journal:
  enabled: true

transactions:
  enabled: true

user-service:
  enabled: true

process-status:
  enabled: true

enqiry-service:
  enabled: true

notification:
  enabled: true

nwsa-service:
  enabled: true

react-service:
  enabled: true

redis-service:
  enabled: true

report-builder:
  enabled: true

report-service:
  enabled: true

template-config:
  enabled: true

common-master:
  enabled: true

common-request:
  enabled: true

login:
  enabled: true



2) the output
D:\Pragati\HELM-2404\Deployment\umbrella-chart>helm template micro-services-at-one-go . --show-only charts/user-service/templates/deployment.yaml --debug 2>&1 | findstr /n "."
1:level=DEBUG msg="Original chart version" version=""
2:level=DEBUG msg="Chart path" path=D:\Pragati\HELM-2404\Deployment\umbrella-chart
3:level=DEBUG msg="number of dependencies in the chart" dependencies=16
4:level=DEBUG msg="number of dependencies in the chart" dependencies=0
5:level=DEBUG msg="number of dependencies in the chart" dependencies=0
6:level=DEBUG msg="number of dependencies in the chart" dependencies=0
7:level=DEBUG msg="number of dependencies in the chart" dependencies=0
8:level=DEBUG msg="number of dependencies in the chart" dependencies=0
9:level=DEBUG msg="number of dependencies in the chart" dependencies=0
10:level=DEBUG msg="number of dependencies in the chart" dependencies=0
11:level=DEBUG msg="number of dependencies in the chart" dependencies=0
12:level=DEBUG msg="number of dependencies in the chart" dependencies=0
13:level=DEBUG msg="number of dependencies in the chart" dependencies=0
14:level=DEBUG msg="number of dependencies in the chart" dependencies=0
15:level=DEBUG msg="number of dependencies in the chart" dependencies=0
16:level=DEBUG msg="number of dependencies in the chart" dependencies=0
17:level=DEBUG msg="number of dependencies in the chart" dependencies=0
18:level=DEBUG msg="number of dependencies in the chart" dependencies=0
19:level=DEBUG msg="number of dependencies in the chart" dependencies=0
20:---
21:# Source: umbrella-chart/charts/user-service/templates/deployment.yaml
22:apiVersion: apps/v1
23:kind: Deployment
25:metadata:
26:  name: user-deployment
27:  namespace: backend
29:spec:
30:  replicas: 1
31:  revisionHistoryLimit: 5
33:  strategy:
34:    type: RollingUpdate
35:    rollingUpdate:
36:      maxUnavailable: 0
37:      maxSurge: 1
39:  selector:
40:    matchLabels:
41:      app: user-backend
43:  template:
44:    metadata:
45:      labels:
46:        app: user-backend
48:    spec:
49:      serviceAccountName: user-sa
50:      terminationGracePeriodSeconds: 30
51:      enableServiceLinks: false
53:      securityContext:
54:        runAsNonRoot: true
55:        runAsUser: 1000
56:        runAsGroup: 1000
57:        fsGroup: 2000
59:      hostAliases:
60:        null
62:      topologySpreadConstraints:
63:        - labelSelector:
64:            matchLabels:
65:              app: user-backend
66:          maxSkew: 1
67:          topologyKey: kubernetes.io/hostname
68:          whenUnsatisfiable: ScheduleAnyway
70:      volumes:
71:        - name: truststore-volume
72:          secret:
73:            items:
74:            - key: ad-truststore.jks
75:              path: ad-truststore.jks
76:            secretName: ldap-truststore-file
78:      containers:
79:        - name: user-container
80:          image: "h06vksharbor.corp.ad.sbi/cbops/user-service:DEV06"
81:          imagePullPolicy:
83:          volumeMounts:
84:            - mountPath: /etc/fincore/secrets
85:              name: truststore-volume
86:              readOnly: true
88:          envFrom:
89:            - configMapRef:
90:                name: oracle-config
91:            - secretRef:
92:                name: oracle-secret
93:            - configMapRef:
94:                name: kafka-config
95:            - configMapRef:
96:                name: redis-config
97:            - configMapRef:
98:                name: ldap-config
100:          env:
101:            null
102:            - name: LDAP_TRUSTSTORE_PASSWORD
103:              valueFrom:
104:                secretKeyRef:
105:                  key: truststore-password
106:                  name: ldap-creds
108:          ports:
109:            - containerPort: 8087
111:          resources:
112:            limits:
113:              cpu: 500m
114:              memory: 1Gi
115:            requests:
116:              cpu: 250m
117:              memory: 512Mi
119:          startupProbe:
120:            tcpSocket:
121:              port: 8087
122:            failureThreshold: 60
123:            periodSeconds: 10
125:          livenessProbe:
126:            tcpSocket:
127:              port: 8087
128:            initialDelaySeconds: 90
129:            periodSeconds: 15
130:            timeoutSeconds: 5
131:            failureThreshold: 5
133:          readinessProbe:
134:            tcpSocket:
135:              port: 8087
136:            initialDelaySeconds: 30
137:            periodSeconds: 10
138:            timeoutSeconds: 5
139:            failureThreshold: 5
141:          lifecycle:
142:            preStop:
143:              exec:
144:                command:
145:                  - "/bin/sh"
146:                  - "-c"
147:                  - "sleep 10"
148:Error: YAML parse error on umbrella-chart/charts/user-service/templates/deployment.yaml: error converting YAML to JSON: yaml: line 81: mapping values are not allowed in this context
