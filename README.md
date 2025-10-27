# k8s-observe-prometheus-grafana

![Prometheus](https://img.shields.io/badge/Prometheus-Monitoring-brightgreen)
![Grafana](https://img.shields.io/badge/Grafana-Visualization-orange)
![Kubernetes](https://img.shields.io/badge/Kubernetes-EKS-blue)
![Status](https://img.shields.io/badge/Status-Ready-success)

## Overview
Deploy a Kubernetes monitoring stack using Prometheus, Grafana and Alertmanager.
Includes a small Python exporter (example) and Helm/manifest snippets to install the stack.

**Region:** us-east-1
**Author:** devopsbydhairyashil

## Architecture (ASCII)
```
+------------+     +----------------+     +-----------+
|  K8s Apps  | --> | Prometheus     | --> | Grafana   |
|  (pods)    |     | (scrape targets)|    | (dashboards)|
+------------+     +----------------+     +-----------+
                            |
                            v
                      +-------------+
                      | Alertmanager|
                      +-------------+
```

## What is included
- `helm-values/` - sample Helm values for Prometheus & Grafana
- `manifests/` - simple ServiceMonitor and exporter manifest
- `exporter/` - tiny Python exporter app (Flask) exposing a metrics endpoint
- `README.md`, `LICENSE`, `.env.example`

## Quick start (local/hypothetical)
1. Install Prometheus & Grafana via Helm (example values in helm-values/).
2. Apply manifests in `manifests/` to create ServiceMonitor for exporter.
3. Import dashboards from `grafana-dashboards/` folder.

## Notes
- This repo provides configuration examples and is meant for demo/testing.
- Use Helm stable/community charts in production and secure access to Grafana.
