# rca-env

### prerequisites

install `helm` and `kubectl`
install `istio`

### microservices-demo

```shell
kubectl apply -k microservices-demo/
```

### observability

```shell
helm install observability observability -n monitoring --create-namespace
```