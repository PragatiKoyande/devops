## Diagnosis

Your Grafana is actually **running fine** — the UI loading issue is caused by two separate problems:

**Problem 1: External DNS failures (non-blocking)**
The errors about `github.com` and `grafana.com` are because your cluster has no internet access. These are cosmetic — Grafana can't check for updates or fetch plugin keys, but it still works.

**Problem 2: "identifier is not initialized" — this is your real blocker**
This means Grafana is receiving requests **before the session/auth is properly initialized**, almost always caused by a **missing `GF_SECURITY_ADMIN_PASSWORD`** or a **secret key not being set**.

---

## Fix

Add these missing environment variables to your Deployment:

```yaml
env:
  - name: GF_SECURITY_ADMIN_USER
    value: admin

  # ADD THIS — without it, session auth fails to initialize
  - name: GF_SECURITY_ADMIN_PASSWORD
    valueFrom:
      secretKeyRef:
        name: grafana-secret
        key: admin-password

  # ADD THIS — required for stable session encryption
  - name: GF_SECURITY_SECRET_KEY
    valueFrom:
      secretKeyRef:
        name: grafana-secret
        key: secret-key

  # ADD THIS — suppress the external update check entirely
  - name: GF_ANALYTICS_CHECK_FOR_UPDATES
    value: "false"

  # ADD THIS — suppress plugin key fetching (no internet)
  - name: GF_PLUGINS_ENABLE_ALPHA
    value: "false"

  - name: GF_SERVER_DOMAIN
    value: fincore-uat.sbi
  - name: GF_SERVER_HTTP_ADDR
    value: "0.0.0.0"
  - name: GF_SERVER_ROOT_URL
    value: https://fincore-uat.sbi/grafana/
  - name: GF_SERVER_SERVE_FROM_SUB_PATH
    value: "true"
```

**Create the secret first:**

```bash
kubectl create secret generic grafana-secret \
  --namespace uat-cbops1 \
  --from-literal=admin-password='YourStrongPassword123!' \
  --from-literal=secret-key='$(openssl rand -hex 32)'
```

---

## Also check your Ingress

The 302 redirect on `/` path suggests your ingress may not be stripping or forwarding the `/grafana` subpath correctly. Verify your ingress has:

```yaml
annotations:
  nginx.ingress.kubernetes.io/rewrite-target: /$2
  nginx.ingress.kubernetes.io/use-regex: "true"
spec:
  rules:
    - host: fincore-uat.sbi
      http:
        paths:
          - path: /grafana(/|$)(.*)
            pathType: Prefix
            backend:
              service:
                name: grafana
                port:
                  number: 3000
```

---

## Root Cause Summary

| Error | Cause | Impact |
|---|---|---|
| `no such host github.com` | No internet egress | Cosmetic only |
| `no such host grafana.com` | No internet egress | Cosmetic only |
| `identifier is not initialized` | Missing admin password / secret key | **Blocks UI login** |
| `status=302 path=/` | Subpath redirect misconfiguration | May block browser access |

Apply the secret + env vars first, then restart the pod with `kubectl rollout restart deployment/grafana -n uat-cbops1`.