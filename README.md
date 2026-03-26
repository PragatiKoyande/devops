apiVersion: v1
kind: ConfigMap
metadata:
  name: ldap-config
  namespace: backend
data:
  SPRING_LDAP_URLS: "ldaps://corp.ad.sbi:636"
  LDAP_TRUSTSTORE_PATH: "file:/etc/fincore/secrets/ad-truststore.jks"
  SPRING_LDAP_USERNAME: "fincorecbops@CORP.AD.SBI"


echo -n "F1C0re#16" | base64
echo -n "fincorecertprodcbops" | base64

apiVersion: v1
kind: Secret
metadata:
  name: ldap-secret
  namespace: backend
type: Opaque
data:
  SPRING_LDAP_PASSWORD: RjFDMHJlIzE2
  LDAP_TRUSTSTORE_PASSWORD: ZmluY29yZWNlcnRwcm9kY2JvcHM=



envFrom:
  - configMapRef:
      name: ldap-config
  - secretRef:
      name: ldap-secret