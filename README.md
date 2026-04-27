# Fortem Helm Charts

Helm chart repository for [Fortem](https://github.com/cybrixcc/fortem) — Kubernetes-native Internal Developer Platform.

## Usage

```bash
helm repo add fortem https://cybrixcc.github.io/fortem-helm-charts
helm repo update
helm install fortem fortem/fortem \
  --namespace fortem-system \
  --create-namespace \
  --set ingress.host=fortem.yourdomain.com \
  --set dex.connectors.google.clientID=xxx \
  --set dex.connectors.google.clientSecret=xxx
```

## Charts

| Chart | Version | Description |
|-------|---------|-------------|
| fortem | 0.1.0 | Kubernetes-native Internal Developer Platform |

## Source

Chart source lives in [cybrixcc/fortem](https://github.com/cybrixcc/fortem/tree/master/helm/fortem).
New versions are published automatically on release tags.
