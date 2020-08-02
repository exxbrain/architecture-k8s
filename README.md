# architecture-k8s

Install helm if not installed yet
```shell script
brew install helm
helm repo add bitnami https://charts.bitnami.com/bitnami
```

## Install using helm chart
```shell script
helm install myapp ./arch-chart
```

## Install without using helm chart

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

## Skaffold

```shell script
skaffold run -f tools/skaffold.yaml
```