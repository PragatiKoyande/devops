kubectl get deployments -n be-test \
-o custom-columns=DEPLOYMENT:.metadata.name,IMAGE:.spec.template.spec.containers[*].image



kubectl get deploy -n be-test -o jsonpath='{range .items[*]}{.metadata.name}{"|"}{.spec.template.spec.containers[*].image}{"\n"}{end}'