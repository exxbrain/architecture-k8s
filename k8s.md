## Kubectl
```shell script
minikube start
watch kubectl get all
kubectl get namespaces
kubectl create namespace arch
kubectl config set-context --current --namespace=arch
kubectl delete namespace arch
kubectl delete service/arch-service
kubectl apply -f .
```

## Run container
```shell script
kubectl run -it --rm busybox --image=busybox
kubectl run -it --rm postgresql-client postgresql://arch:passwd@postgres:5432/arch --image=jbergknoff/postgresql-client
env
wget -qO- http://myapp-arch-chart:8000/
```

## Update deployment
```shell script
kubectl set image deployment.apps/myapp-arch-chart 
kubectl rollout history deployment.apps/myapp-arch-chart
kubectl rollout undo deployment.apps/myapp-arch-chart
kubectl scale deployment.apps/myapp-arch-chart --replicas=4
```

## Services
```shell script
minikube service myapp-arch-chart --url -n arch
curl http://192.168.64.2:32758/health
kubectl port-forward svc/myapp-arch-chart 10000:8000
curl http://localhost:10000/health
```

## Pods
```shell script
kubectl get pods -A
kubectl logs arch-deployment-9b69586fc-d89wv
kubectl describe pod myapp-arch-chart-7bb569fc44-lpkzx
kubectl delete pod busybox-686489489-tdvp9
kubectl get pods --show-labels
# Debug pod
kubectl label pod myapp-arch-chart-7bb569fc44-xrfhk app.kubernetes.io/instance=myapp1 --overwrite
kubectl exec -it pod/postgres-0 bash
psql -U arch #passwd
```

## Helm
```shell script
helm install myapp ./arch-chart
helm upgrade myapp ./arch-chart
helm delete myapp ./arch-chart
```
## Ingress
```shell script
minikube addons enable ingress
kubectl describe ingress arch-skaffold-arch-chart

kubectl config set-context --current --namespace=kube-system
kubectl describe deployment.apps/ingress-nginx-controller
curl http://arch.homework/otusapp/dzakharov
```

## Inside cluster
```shell script
minikube ssh
wget -qO- http://10.111.156.222:8000/
logout

minikube docker-env

# To point your shell to minikube's docker-daemon, run:
eval $(minikube -p minikube docker-env)
docker ps
```

## Persistent volume
```shell script
kubectl get pv
kubectl get pvc
kubectl delete pvc data-postgres-0
kubectl delete pv --all
```