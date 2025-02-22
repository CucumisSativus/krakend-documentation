---
lastmod: 2019-09-15
date: 2019-09-15
notoc: true
linktitle: Google Stackdriver
title: Exporting metrics, logs and events to Google Stackdriver
weight: 120
notoc: true
aliases: ["/docs/logging-metrics-tracing/stackdriver/"]
menu:
  community_current:
    parent: "080 Telemetry and Analytics"
meta:
  since: 0.7
  source: https://github.com/krakendio/krakend-opencensus
  namespace:
  - telemetry/opencensus
  log_prefix:
  - "[SERVICE: Opencensus]"
  scope:
  - service
  log_prefix:
  - "[SERVICE: Opencensus]"
---

[Google Stackdriver](https://cloud.google.com/stackdriver/) aggregates metrics, logs, and events from infrastructure, giving developers and operators a rich set of observable signals that speed root-cause analysis and reduce mean time to resolution (MTTR).

The Opencensus exporter allows you export data to Google Stackdriver. Enabling it only requires you to add the `stackdriver` exporter in the [opencensus module](/docs/telemetry/opencensus/).

The following configuration snippet sends the data:

{{< highlight json >}}
{
  "extra_config": {
    "telemetry/opencensus": {
      "exporters": {
        "stackdriver": {
          "project_id": "my-krakend-project",
          "metrics_prefix": "krakend",
          "default_labels": {
          "env": "production"
          }
        }
      }
    }
  }
}
{{< /highlight >}}

*   `project_id`: The identifier of your Google Cloud project.
*   `metrics_prefix`: A prefix that you can add to all your metrics for better organization.
*   `default_labels`: Enter here any label that will be assigned by default to the reported metric so you can filter later on Stack Driver. In the example we set a label `env` with the value `production`.

See also the [additional settings](/docs/telemetry/opencensus/) of the Opencensus module that can be declared.
