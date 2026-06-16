kubectl describe nodes | grep -A5 "Allocated resources"
kubectl top nodes
kubectl get nodes -o custom-columns=NAME:.metadata.name,CPU:.status.allocatable.cpu,MEMORY:.status.allocatable.memory