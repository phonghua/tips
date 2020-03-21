## delete evicted pods
kubectl get pods -n ch-web | grep 'Evicted' | awk '{print $1}' | xargs kubectl delete pod -n ch-web
