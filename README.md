# Fortem Helm Charts

Helm chart repository for [Fortem](https://github.com/cybrixcc/fortem) — Kubernetes-native Internal Developer Platform.

## Quick Start

```bash
helm repo add fortem https://cybrixcc.github.io/fortem-helm-charts
helm repo update
```

## Charts

| Chart | Version | Description |
|-------|---------|-------------|
| `fortem/fortem` | 0.1.0 | Full platform — API, Frontend, Operator, PostgreSQL, Dex |
| `fortem/fortem-agent` | 0.1.0 | Lightweight agent for connecting additional clusters |

---

## Install Fortem (full platform)

```bash
helm install fortem fortem/fortem \
  --namespace fortem-system \
  --create-namespace \
  --set ingress.host=fortem.yourdomain.com \
  --set dex.connectors.github.enabled=true \
  --set dex.connectors.github.clientID=YOUR_GITHUB_CLIENT_ID \
  --set dex.connectors.github.clientSecret=YOUR_GITHUB_CLIENT_SECRET
```

Open `https://fortem.yourdomain.com` — done.

## Add a managed cluster (Team+ tier)

1. Go to `https://fortem.yourdomain.com` → Clusters → **Register Cluster**
2. Enter cluster name → **Generate install command**
3. Copy and run in your target cluster:

```bash
helm install fortem-agent fortem/fortem-agent \
  --namespace fortem-agent \
  --create-namespace \
  --set controlPlane.endpoint=https://fortem.yourdomain.com \
  --set controlPlane.clusterName=my-cluster \
  --set controlPlane.token=fat-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

The cluster appears as **Connected** within 30 seconds.

## Source

Chart source: [cybrixcc/fortem](https://github.com/cybrixcc/fortem/tree/master/helm).
New versions are published automatically on release tags.
