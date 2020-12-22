# Monitoring and tracing server

## Tracing

This deployment provides functionality needed for tracing in oCIS. It exposes an Jaeger collector where the Jaeger agent run side by side with oCIS (see [example](https://github.com/owncloud-devops/monitoring-tracing-client-example)) can transmit collected traces to.

Jaeger query, which is also started by this deployment enables the user to visualize and follow Traces. This can also be done in Grafana, which is also part of this deployment.

## Monitoring

This deployments provides Prometheus, wich can be used for monitoring oCIS metrics and host metrics too. In order for Prometheus to scrape your oCIS deployment metrics, you need to run Telegraf (see [example](https://github.com/owncloud-devops/monitoring-tracing-client-example)) side by side with oCIS.

Prometheus graphing interface or better Grafana will allow you to visualize the collected metrics.

## FAQ

### How do I change / contribute to the Grafana dasboards?
For that you will need a Grafana account. Then you can log in and create / edit dashboards. Please not that they will not be persisted. In order to persist them, copy the json source of the dashboard and update / create the corresponding dasboard file in `config/grafana/dashboards` and create a PR from that changes.

### How can I set up my oCIS deployment / server being scraped?
Add your host name to `config/prometheus/scrape_targets/ocis.yml` in a PR.
