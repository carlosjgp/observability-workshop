# observability-workshop

## Requirements

- [KinD](https://kind.sigs.k8s.io/)
- [Helm](https://helm.sh/docs/intro/install/)
- [Prometheus Operator - Metrics](https://hub.helm.sh/charts/stable/prometheus-operator)
- [Jaeger Operator - Distributed tracing](https://hub.helm.sh/charts/jaegertracing/jaeger-operator)
- [Loki - Logs](https://hub.helm.sh/charts/loki/loki)
- [Grafana - Dashboarding](https://hub.helm.sh/charts/stable/grafana)
- [Mattermost - Slack like instant messaging application](https://hub.helm.sh/charts/mattermost/mattermost-team-edition)

### Create Kuberneste cluster for testing

You can skip this step if you have a cluster already.

Cet a Kubernetes cluster ready to deploy applications on it.

#### Kind

```shell
$ kind create cluster --name obs-wshop --config ./kind/kind.yaml
```

##### Nginx Ingress

To be able to access our deployed applications in our custom local domain

https://kind.sigs.k8s.io/docs/user/ingress/#setting-up-an-ingress-controller

```shell
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/kind/deploy.yaml
```

#### Minikube (optional)

Another implementation to run Kubernetes locally
https://kubernetes.io/docs/tasks/tools/install-minikube/

#### AWS eksctl (optional)

If you have an AWS account you can create an EKS cluster using [AWS guide](https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html)


### Add Helm repositories

Helm Stable (will be depreated on Nov 2020)

```shell
$ helm repo add stable https://kubernetes-charts.storage.googleapis.com
"stable" has been added to your repositories
```

Jaeger charts

```shell
$ helm repo add jaegertracing https://jaegertracing.github.io/helm-charts
"jaegertracing" has been added to your repositories
```

Grafana Loki charts

```shell
$ helm repo add loki https://grafana.github.io/loki/charts
"loki" has been added to your repositories
```

Mattermost

```shell
$ helm repo add mattermost https://helm.mattermost.com
"mattermost" has been added to your repositories
```

Update all repos just adding them doesn't make the charts on the repostiries available

```shell
$ helm repo up
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "jaegertracing" chart repository
...Successfully got an update from the "mattermost" chart repository
...Successfully got an update from the "loki" chart repository
...Successfully got an update from the "stable" chart repository
Update Complete. ⎈ Happy Helming!⎈
```

### Workshop

[Instructions](./WORKSHOP.md)