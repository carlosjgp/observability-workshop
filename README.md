# observability-workshop

## Requirements

- [KinD](https://kind.sigs.k8s.io/)
- [Helm](https://helm.sh/docs/intro/install/)
- [Prometheus Operator - Metrics](https://hub.helm.sh/charts/stable/prometheus-operator)
- [Jaeger Operator - Distributed tracing](https://hub.helm.sh/charts/jaegertracing/jaeger-operator)
- [Loki - Logs](https://hub.helm.sh/charts/loki/loki)
- [Grafana - Dashboarding](https://hub.helm.sh/charts/stable/grafana)

### Create Kuberneste cluster for testing

You can skip this step if you have a cluster already.

Cet a Kubernetes cluster ready to deploy applications on it.

#### Kind

```shell
$ kind create cluster --name obs-wshop

```

#### Minikube (optional)

Adjust memory accordingly to your computer specs.
All the components we are using here are writting in GoLang which makes them very efficient

```shell
$ minikube start --memory 4096m

```

#### AWS eksctl (optional)

If you have an AWS account you can create an EKS cluster using [AWS guide](https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html)


### Add Helm repositories

Helm Stable (will be depreated on Nov 2020)

```shell
$ helm repo add stable https://kubernetes-charts.storage.googleapis.com
```

Jaeger charts

```shell
$ helm repo add jaegertracing https://jaegertracing.github.io/helm-charts
```
