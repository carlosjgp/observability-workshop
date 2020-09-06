# Agenda

## V1

#### Introduction

This workshop will help to understand how to install, configure and use an in house Observability stack while understanding how to operate all the components at the same time as connecting all of them together and how to use these components to get the most from metrics, traces and logs in your organization

[Slides](https://docs.google.com/presentation/d/1sNhssHQz2ci7_6b9IdSg-wxvA2qh3Ry84yPt4cePxQk/edit?usp=sharing)

Overview of operating observability components
- Prometheus
- Alertmanager
- Grafana

#### Prometheus

[Home](https://prometheus.io/)

##### Operations
- HA deployments
- Service discovery
- Relabeling
- Long term storage

##### Prometheus Operator
- Understanding its CRDs and how to use them - https://github.com/prometheus-operator/prometheus-operator/blob/master/Documentation
- Strategies for CI/CD

##### User
- PromQL
- [Alert unit testing](https://prometheus.io/docs/prometheus/latest/configuration/unit_testing_rules/)

#### Alertmanager

[Home](https://prometheus.io/docs/alerting/latest/overview/)

##### Operations
- HA deployments

##### User
- Routes
- Receivers
- [Receivers tree](https://www.prometheus.io/webtools/alerting/routing-tree-editor/) - [Test data](https://raw.githubusercontent.com/prometheus/alertmanager/master/config/testdata/conf.good.yml)
- Templates ([for Slack](https://juliusv.com/promslack/))

#### Grafana

[Home](https://grafana.com/oss/grafana/)

##### Operations
- Do I need a DB?
- HA deployments
- Authentication

##### User
- Understanding the different metrics and which panels we should use
- Creating a dashboard through the UI
- Creating dashboards programmatically
- Strategies for CI/CD

#### Distributed tracing
- Instrumentation
- Jaeger, Zipkin and OpenTelemetry
- Storage

#### Loki

[Home](https://grafana.com/loki)

##### Operations
- Components
- Storage
- Retention

##### User
- Grafana dashboards
- CLI

#### Thanos

[Home](https://thanos.io/)

##### Operations
- Components
- Storage
- Retention

##### Install

```shell
$ helm upgrade --install --wait \
    -n monitoring karma \
    -f ./helm/stable/karma/1.5.2/values.yaml \
    --version 1.5.2 \
    stable/karma
```

#### Karma

[Home](https://github.com/prymitive/karma)

##### Install

```shell
$ helm upgrade --install --wait \
    -n monitoring karma \
    -f ./helm/stable/karma/1.5.2/values.yaml \
    --version 1.5.2 \
    stable/karma
```

At the moment of writting this agenda Karma Helm chart does not support ingresses without `host` field.
Defining this breaks the other ingresses wihtout hostname when using KinD.
To fix this we just need to remove the field from the deployed ingress

```shell
$ KUBE_EDITOR=vi kubectl edit ingress -n monitoring karma
```

To make it work we need to remove the `host` field from the ingress rule
