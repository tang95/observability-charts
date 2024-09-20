# rca-env

### prerequisites

install `helm` and `kubectl`

```shell
# install
kubectl apply -f microservice.yaml
helm upgrade observability observability -n monitoring --create-namespace --install
````

```shell
# uninstall
helm uninstall observability -n monitoring
```

### usage
```shell
kubectl port-forward svc/frontendproxy 8080
```
### loadgenerator
```shell
kubectl port-forward svc/loadgenerator 8089
```

### grafana
```shell
kubectl port-forward svc/observability-grafana -n monitoring 3000:80
```

