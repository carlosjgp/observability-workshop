# Agenda

## Links

- [Prometheus Operator docs](https://coreos.com/operators/prometheus/docs/latest/user-guides/getting-started.html)
- [Prometheus Operator Specs](https://github.com/prometheus-operator/prometheus-operator/blob/master/Documentation)
- [Prometheus configuration](https://prometheus.io/docs/prometheus/latest/configuration/configuration/)

## V1

#### Introduction

This workshop will help to understand how to install, configure and use an in house Observability stack while understanding how to operate all the components at the same time as connecting all of them together and how to use these components to get the most from metrics, traces and logs in your organization

Overview of operating observability components
- Prometheus
- Grafana
- Distributed tracing (if we have time)
- Loki (if we have time)
- Thanos (if we have time)

#### Prometheus

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
- Alert unit testing

#### Alertmanager

##### Operations
- HA deployments

##### User
- Routes
- Receivers
- Templates

#### Grafana

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

#### Loki

##### Operations
- Components
- Storage
- Retention

##### User
- Grafana dashboards
- CLI

#### Thanos

##### Operations
- Components
- Storage
- Retention