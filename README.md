### prerequisites

install `helm`、`istio` and `kubectl`

#### install

```shell
istioctl install -y -f istio-config/mesh-config.yaml
kubectl label namespace default istio-injection=enabled
kubectl apply -k microservices-demo
helm upgrade observability observability -n monitoring --create-namespace --install
````

### uninstall

```shell
kubectl delete -k istio-config
kubectl delete -k microservices-demo
helm uninstall observability -n monitoring
kubectl delete namespace monitoring
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
kubectl get secret --namespace monitoring observability-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
kubectl port-forward svc/observability-grafana -n monitoring 3000:80
# open http://127.0.0.1:3000
```

