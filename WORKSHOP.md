# WORKSHOP

## Install Helm charts

### Prometheus Operator

Install the CRDs separately since there is an issue with Helm installing Webhooks and CRDs on the same chart

```shell
kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.38/example/prometheus-operator-crd/monitoring.coreos.com_alertmanagers.yaml
kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.38/example/prometheus-operator-crd/monitoring.coreos.com_podmonitors.yaml
kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.38/example/prometheus-operator-crd/monitoring.coreos.com_prometheuses.yaml
kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.38/example/prometheus-operator-crd/monitoring.coreos.com_prometheusrules.yaml
kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.38/example/prometheus-operator-crd/monitoring.coreos.com_servicemonitors.yaml
kubectl apply -f https://raw.githubusercontent.com/coreos/prometheus-operator/release-0.38/example/prometheus-operator-crd/monitoring.coreos.com_thanosrulers.yaml
```

We are going to deploy Prometheus Operator on on the `monitoring` namespace 
```shell
$ kubectl create ns monitoring
```

Create user and password for Grafana, otherwhise it will create a random password
```shell
$ kubectl create secret generic \
    -n monitoring grafana-admin \
    --from-literal admin-user=admin \
    --from-literal admin-password=pass
```

Install Prometheus Operator
```shell
$ helm upgrade --install --wait \
    -n monitoring prom-op \
    -f ./helm/stable/prometheus-operator/9.3.1/values.yaml \
    --version 9.3.1 \
    stable/prometheus-operator
```

### Jaeger Operator

```shell
$ kubectl create ns tracing
```

```shell
$ kubectl apply -f https://raw.githubusercontent.com/jaegertracing/jaeger-operator/master/deploy/crds/jaegertracing.io_jaegers_crd.yaml
```

```shell
$ helm upgrade --install --wait \
    -n tracing jaeger-op \
    -f ./helm/jaegertracing/jaeger-operator/2.15.1/values.yaml \
    --version 2.15.1 \
    jaegertracing/jaeger-operator
```

### Loki and Promtail

```shell
$ kubectl create ns logging
```

```shell
$ helm upgrade --install --wait \
    --namespace logging \
    -f ./helm/loki/loki/0.31.0/values.yaml \
    --version 0.31.0 \
    loki loki/loki
```

```shell
$ helm upgrade --install --wait \
    --namespace logging \
    -f ./helm/loki/promtail/0.24.0/values.yaml \
    --version 0.24.0 \
    promtail loki/promtail
```

### Demo application

```shell
kubectl apply -f ./deployments/demo-app.yaml
```