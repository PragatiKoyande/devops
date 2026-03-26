
            - name: SPRING_LDAP_URLS
              value: "ldaps://corp.ad.sbi:636"
                          - name: LDAP_TRUSTSTORE_PATH
              value: "file:/etc/fincore/secrets/ad-truststore.jks"

            - name: SPRING_LDAP_USERNAME
              value: "fincorecbops@CORP.AD.SBI"

            - name: SPRING_LDAP_PASSWORD
              value: "F1C0re#16"

            - name: LDAP_TRUSTSTORE_PASSWORD
              value: "fincorecertprodcbops"


              I want to make secrets and configmap for thw above parameter kindly guide me making config map and screts and also how to refer in manisfest
