# rca-env

### prerequisites

install `helm`、`istio` and `kubectl`

#### install

```shell
istioctl install -y -f istio-config/mesh-config.yaml
kubectl apply -f istio-config/otel-tracing.yaml
kubectl label namespace default istio-injection=enabled
kubectl apply -k microservices-demo
helm upgrade observability observability -n monitoring --create-namespace --install
````

### uninstall

```shell
helm uninstall observability -n monitoring
kubectl delete namespace monitoring
kubectl delete -k microservices-demo
kubectl delete -f istio-config/otel-tracing.yaml
istioctl uninstall -y --purge
kubectl delete namespace istio-system
kubectl label namespace default istio-injection-
```

### usage

```shell
sudo kubectl port-forward svc/istio-ingressgateway -n istio-system 80
# open http://127.0.0.1
```

### grafana

```shell
kubectl port-forward svc/observability-grafana -n monitoring 3000:80
# open http://127.0.0.1:3000
```

