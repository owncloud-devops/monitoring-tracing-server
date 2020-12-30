# Monitoring and tracing server

This monitoring and tracing server runs as part of our infrastructure for our internal oCIS testing instances.

Have a look at:

- Grafana: [grafana.infra.owncloud.works](https://grafana.infra.owncloud.works)
- Prometheus: [prometheus.infra.owncloud.works](https://prometheus.infra.owncloud.works)
- Jaeger Query: [jaeger.infra.owncloud.works](https://jaeger.infra.owncloud.works)

## Overview

For a wider overview on what we try to achieve, see [here](https://owncloud.github.io/ocis/deployment/monitoring-tracing/).

The following overview will mainly focus on the monitoring & tracing server.

## Monitoring

This deployments provides Prometheus, wich can be used for monitoring oCIS metrics and host metrics too. In order for Prometheus to scrape your oCIS deployment metrics, you need to run Telegraf (see [here](https://github.com/owncloud-devops/monitoring-tracing-client)) side by side with oCIS.

Prometheus graphing interface and by preference Grafana allows you to visualize the collected metrics.

## Tracing

This deployment provides functionality needed for tracing in oCIS with Jaeger. It exposes an Jaeger collector where the Jaeger agent run side by side with oCIS (see [here](https://github.com/owncloud-devops/monitoring-tracing-client-example)) can transmit collected traces to.

Jaeger query, which is provided by this deployment enables the user to visualize and follow Traces. This can also be done in Grafana.

## FAQ

### How do I change / contribute to the Grafana dasboards?

For that you will need an account on the Grafana instance. Then you can log in and create / edit dashboards. Please note that they will not be persisted. In order to persist them, copy the json source of the dashboard and update / create the corresponding dasboard file in `config/grafana/dashboards` and create a PR from that changes.

### How can I set up my oCIS deployment / server being scraped?

Add your host name to `config/prometheus/scrape_targets/ocis.yml` in a PR.

## Deployment
