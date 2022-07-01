# MetaFlow Helm Charts


This repository contains [Helm](https://helm.sh/) charts for MetaFlow project.

## Usage

[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs/) to get started.

Once Helm is set up properly, add the repo as follows:

```console
helm repo add metaflow https://metaflowys.github.io/metaflow
helm repo udpate metaflow
```

## Helm Charts

You can then run `helm search repo metaflow` to see the charts.

_See [helm repo](https://helm.sh/docs/helm/helm_repo/) for command documentation._

## Installing the Chart

To install the chart with the release name `metaflow`:

```console
helm install metaflow -n metaflow metaflow/metaflow --create-namespace
```

## Uninstalling the Chart

To uninstall/delete the my-release deployment:

```console
helm delete metaflow -n metaflow
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Requirements

| Repository | Name | Version |
|------------|------|---------|
|  | clickhouse | *.*.* |
|  | metaflow-agent | *.*.* |
|  | mysql | *.*.* |
| https://grafana.github.io/helm-charts | grafana | 6.31.1 |

