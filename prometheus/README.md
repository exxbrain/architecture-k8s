## Prometheus

https://github.com/helm/charts/tree/master/stable/prometheus-operator

user/password: `admin/prom-operator`

```shell script
kubectl create namespace monitoring
kubectl config set-context --current --namespace=monitoring

helm repo add stable https://kubernetes-charts.storage.googleapis.com
helm repo update

helm install prom stable/prometheus-operator -f prometheus/prometheus.yaml --atomic
helm uninstall prom

kubectl port-forward service/prom-grafana 9000:80
```

```shell script
kubectl get servicemonitors.monitoring.coreos.com
kubectl port-forward service/prom-prometheus-operator-prometheus 9000:9090
http://localhost:9000/service-discovery
```