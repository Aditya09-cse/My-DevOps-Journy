# Day 74 -- Node Exporter, cAdvisor, and Grafana Dashboards

## Task
Prometheus is running and you can query metrics. But right now it is only monitoring itself. In production, you need to monitor two critical things: the **host machine** (CPU, memory, disk, network) and the **Docker containers** running on it.

Today you add Node Exporter for host metrics, cAdvisor for container metrics, and set up Grafana to visualize everything in dashboards instead of raw PromQL.

---

## Expected Output
- Node Exporter running and scraped by Prometheus
- cAdvisor running and scraped by Prometheus
- Grafana running with Prometheus configured as a datasource
- At least one custom Grafana dashboard with CPU, memory, and container panels
- A markdown file: `day-74-exporters-grafana.md`

---
