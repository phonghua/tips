## delete evicted pods in 1 namespace
```sh
kubectl get pods -n your-namespace | grep 'Evicted' | awk '{print $1}' | xargs kubectl delete pod -n your-namesapce
```

## delete all evicted pods in all namespaces
```sh
kubectl get pods --all-namespaces | grep Evicted | awk '{print $2 " --namespace=" $1}' | xargs kubectl delete pod
```
##
```sh
k exec -it `k get pods -l tier=app,env=production --field-selector=status.phase=Running -o jsobpath="{.items[0].metadata.name}"` -- bash
```

