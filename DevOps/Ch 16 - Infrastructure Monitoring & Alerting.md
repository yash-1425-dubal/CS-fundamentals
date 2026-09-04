# Chapter 16: Infrastructure Monitoring & Alerting

## Goals of Monitoring in DevOps
- **Visibility**: Know the health of services, servers, and pipelines.
- **Reliability**: Detect failures before they impact users.
- **Performance Optimization**: Identify bottlenecks and capacity limits.
- **Business Insight**: Correlate technical metrics with business KPIs.

## Core Observability Pillars
| Pillar | What it captures | Typical Tools |
|--------|------------------|---------------|
| Logs   | Immutable, time‑ordered event records | Elastic Stack, Loki, Splunk |
| Metrics| Numeric time‑series (CPU, latency, error rates) | Prometheus, Grafana, Datadog |
| Traces | End‑to‑end request flow across services | Jaeger, OpenTelemetry, Zipkin |

## Designing Effective Alerts
1. **Signal‑to‑Noise Ratio** – Alert only on actionable conditions.
2. **Severity Levels** – `Critical`, `Warning`, `Info` to prioritize response.
3. **Runbooks** – Attach remediation steps directly to the alert definition.
4. **Routing** – Send alerts to on‑call rotation via PagerDuty, Opsgenie, or Slack.

### Example Alert Rule (Prometheus)
```yaml
# High CPU usage > 80% for 5 minutes
- alert: HighCPUUsage
  expr: avg(rate(node_cpu_seconds_total{mode="system"}[1m])) by (instance) > 0.8
  for: 5m
  labels:
    severity: critical
  annotations:
    summary: "CPU usage high on {{ $labels.instance }}"
    description: "CPU usage has exceeded 80% for the last 5 minutes."
    runbook: "https://example.com/runbooks/cpu-high"
```

## Monitoring Architecture
```mermaid
flowchart LR
    A[Applications] --> B[Instrumentation (OpenTelemetry)] --> C[Metrics Store (Prometheus)]
    A --> D[Log Exporter] --> E[Log Store (Loki)]
    A --> F[Trace Exporter] --> G[Trace Store (Jaeger)]
    C --> H[Grafana Dashboard]
    E --> H
    G --> H
    H --> I[Alertmanager]
    I --> J[On‑Call (PagerDuty)]
```

## Best Practices
- **SLO‑Driven Alerting** – Define Service Level Objectives (e.g., 99.9% uptime) and alert when error‑budget consumption exceeds a threshold.
- **Tagging & Metadata** – Include environment (`prod`, `staging`) and service name in all metrics/logs for easy filtering.
- **Retention Policies** – Store high‑resolution metrics for a short period (e.g., 15 days) and down‑sample for long‑term analysis.
- **Dashboards as Code** – Version‑control Grafana dashboards (JSON) alongside application code.
- **Chaos‑Testing Integration** – Verify alerts fire correctly during simulated failures.

## Common Pitfalls
- Alert fatigue from noisy or duplicated alerts.
- Over‑collecting metrics leading to high storage costs.
- Missing correlation between logs and metrics, making root‑cause analysis harder.

## Summary
Effective monitoring and alerting are essential for maintaining reliability in a DevOps environment. By instrumenting applications, storing observability data centrally, and defining clear, actionable alerts tied to SLOs, teams can respond quickly to incidents and continuously improve system performance.
