# rca-env

### microservice

```shell
kubectll apply -k .
```

### prerequisite

```shell
helm repo add grafana https://grafana.github.io/helm-charts
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts
helm repo update
```

### grafana

```shell
cd grafana
helm install grafana grafana/grafana  --values values.yaml -n monitoring --create-namespace
```

### kube-prometheus-stack

```shell
cd kube-prometheus-stack
helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack  --values values.yaml -n monitoring --create-namespace
```

### loki

```shell
cd loki
helm install loki grafana/loki-distributed --values values.yaml -n monitoring --create-namespace
```

### tempo

```shell
cd tempo
helm install tempo grafana/tempo-distributed --values values.yaml -n monitoring --create-namespace
```

### open-telemetry

```shell
cd open-telemetry
helm install otel-collector open-telemetry/opentelemetry-collector --values values.yaml -n monitoring --create-namespace
```