# architecture-k8s

Install helm if not installed yet
```shell script
brew install helm
helm repo add bitnami https://charts.bitnami.com/bitnami
```

## Helm chart
Install
```shell script
helm install myapp ./arch-chart
```
Upgrade/Delete
```shell script
helm upgrade myapp ./arch-chart
helm uninstall myapp ./arch-chart
```


## Without using helm chart

Install postgres
```shell script
helm install pg bitnami/postgresql -f tools/pg-values.yaml
```

Run
```shell script
kubectl apply -f .
```

Stop
```shell script
kubectl apply -f .
```

## Test
Use Postman with `Users.postman_collection.json` from the `tools` folder

## Skaffold (Not working yet)

```shell script
skaffold run -f tools/skaffold.yaml
```