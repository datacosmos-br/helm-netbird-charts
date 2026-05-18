# helm-netbird-charts

Helm charts for the [NetBird](https://netbird.io) mesh-VPN platform, maintained
by Datacosmos and consumed by the GitOps stack (ArgoCD).

Fork of [jaconi-io/helm-charts](https://github.com/jaconi-io/helm-charts),
trimmed to the NetBird charts only.

## Charts

| Chart | Version | Description |
|---|---|---|
| [`netbird`](netbird/) | 0.16.2 | NetBird VPN management server |
| [`netbird-dashboard`](netbird-dashboard/) | 1.3.0 | Web UI for the NetBird management server |

## Usage

ArgoCD consumes each chart directly from this repository, pinned to a
per-chart git tag (`netbird-<version>`, `netbird-dashboard-<version>`).

Render a chart locally:

```shell
helm lint netbird
helm template netbird netbird -f my-values.yaml
```

## Releasing

1. Bump `version` in the chart's `Chart.yaml`.
2. Commit to `main`.
3. Tag the commit `<chart>-<version>` (e.g. `netbird-0.16.3`) and push the tag —
   ArgoCD `targetRevision` pins to these tags.
