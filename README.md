# architecture-k8s

#### Install helm if not installed yet
```shell script
brew install helm
helm repo add bitnami https://charts.bitnami.com/bitnami
```

#### Install postgres
```shell script
helm install pg bitnami/postgresql -f tools/pg-values.yaml
```

#### Run
```shell script
kubectl apply -f .
```

#### Postman
Use `*.postman_collection.json` from the `tools` folder 