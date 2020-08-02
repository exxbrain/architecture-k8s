# architecture-k8s

Install helm if not installed yet
```shell script
brew install helm
helm repo add bitnami https://charts.bitnami.com/bitnami
```

## Install from helm charts
```shell script
helm install myapp ./arch-chart
```

## Install without helm charts

Install postgres
```shell script
helm install pg bitnami/postgresql -f tools/pg-values.yaml
```

Run
```shell script
kubectl apply -f .
```

## Test
Use Postman with `Users.postman_collection.json` from the `tools` folder