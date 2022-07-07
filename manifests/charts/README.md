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


## License

[Apache 2.0 License](./LICENSE).



## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.image.repository | string | `"metaflowys"` |image repository of metaflow component, optional ghcr Image repository address: ghcr.io/metaflowys, Dockerhub Image repository address: metaflowys, AliyunYun Image repository address: registry.cn-beijing.aliyuncs.com/metaflowys |
| global.image.pullPolicy | string | `"Always"` | Image Pull Policy for All Components |
| global.hostNetwork | bool | `false` | Network mode for some components of metaflow-server, metaflow-app, click house, and mysql |
| global.dnsPolicy | string | `"ClusterFirst"` | dns policies for some components of metaflow-server, metaflow-app, click house, and mysql |
| global.password.grafana | string | `"metaflow"` | grafana login password |
| global.password.mysql | string | `"metaflow"` | mysql database login password |
| global.podManagementPolicy | string | `"OrderedReady"` | metaflow-server, clickhouse podManagementPolicy |
| global.replicas | int | `1` | The number of copies of metaflow-server and clickhouse. It is worth noting that the expansion of metaflow must be done through helm because of the static configuration file of the clickhosue cluster. |
| global.podAffinityLabelSelector | list | `[]` | The pod hard affinity of metaflow-server, metaflow-app, clickhouse, mysql and each component's own pod hard affinity are or |
| global.podAffinityTermLabelSelector | list | `[]` | The pod soft affinity of metaflow-server, metaflow-app, clickhouse, and mysql, and the pod soft affinity of each component is or |
| global.podAntiAffinityLabelSelector | list | `[]` | The pod hard anti-affinity of metaflow-server, metaflow-app, clickhouse, mysql and each component's own pod hard anti-affinity relationship is or |
| global.podAntiAffinityTermLabelSelector | list | `[]` | The pod soft anti-affinity of metaflow-server, metaflow-app, clickhouse, mysql and each component's own pod anti-soft affinity are or |
| global.nodeAffinityLabelSelector | list | `[]` | The node hard affinity of metaflow-server, metaflow-app, clickhouse, mysql and each component's own node hard affinity are or |
| global.nodeAffinityTermLabelSelector | list | `[]` | The node soft affinity of metaflow-server, metaflow-app, clickhouse, and mysql, and the node soft affinity of each component is or |
| global.timezone | string | `"Asia/Shanghai"` | your time zone |
| global.nodePort.clickhous | int | `30900` | NodePort exposed by clickhouse, if the default value is not available, please modify it to an available one |
| global.nodePort.metaflowServerGrpc | int | `30035` | NodePort exposed by metaflow-server, if the default value is not available, please modify it to an available one |
| global.nodePort.metaflowServerIngester | int | `30033` | NodePort exposed by metaflow-server, if the default value is not available, please modify it to an available one |
| global.nodePort.metaflowServerSslGrpc | int | `30135` | NodePort exposed by metaflow-server, if the default value is not available, please modify it to an available one |
| global.nodePort.metaflowServerhealthCheck | int | `30417` | NodePort exposed by metaflow-server, if the default value is not available, please modify it to an available one |
| global.ntpServer | string | `"ntp1.aliyun.com"` | ntp time synchronization server address, please modify it to an available address, you need to access udp 123 port |
| image.server.repository | string | `"{{ .Values.global.image.repository }}/metaflow-server"` | The image warehouse address of metaflow-server, supports tpl |
| image.server.tag | string | `"latest"` | image tag of metaflow-server, supports tpl |
| image.server.pullPolicy | string | `"{{ .Values.global.image.pullPolicy }}"` | The image pull strategy of metaflow-server supports tpl |
| image.elector.repository | string | `"{{ .Values.global.image.repository }}/elector"` | The image warehouse address of elector, supports tpl |
| image.elector.tag | string | `"latest"` | image tag of elector, supports tpl |
| image.elector.pullPolicy | string | `"{{ .Values.global.image.pullPolicy }}"` | The image pull strategy of elector supports tpl |
| image.app.repository | string | `"dfcloud-image-registry.cn-beijing.cr.aliyuncs.com/dev/statistics"` | The image warehouse address of metaflow-app, supports tpl |
| image.app.tag | string | `"latest"` | image tag of metaflow-app, supports tpl |
| image.app.pullPolicy | string | `"{{ .Values.global.image.pullPolicy }}"` | The image pull strategy of metaflow-app supports tpl |
| imagePullSecrets | list | `[]` | Pull the key of the image |
| fullnameOverride | string | `""` |  |
| nameOverride | string | `""` |  |
| timezone | string | `"{{ .Values.global.timezone }}"` | Time zone |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| securityContext | object | `{}` |  |
| server.replicas | string | `"{{ .Values.global.replicas }}"` | The replicas of metaflow-server need to be the same as clickhouse |
| server.dnsPolicy | string | `"{{ .Values.global.dnsPolicy }}"` | DNS policy of metaflow-server |
| server.hostNetwork | string | `"{{ .Values.global.hostNetwork }}"` | Network mode of metaflow-server |
| server.nodeAffinityLabelSelector | list | `[]` | The node hard affinity of Metaflow-server and Gloabl is or |
| server.nodeAffinityTermLabelSelector | list | `[]` | The node soft affinity of Metaflow-server and Gloabl is or |
| server.nodeSelector | object | `{}` |  |
| server.podAffinityLabelSelector | list |  | The pod hard affinity of Metaflow-server and Gloabl is or |
| server.podAffinityTermLabelSelector | list | `[]` | The pod sort antiaffinity of Metaflow-server and Gloabl is or |
| server.podAntiAffinityLabelSelector | list |  | he pod hard untiaffinity of Metaflow-server and Gloabl is or |
| server.podAntiAffinityTermLabelSelector | list | `[]` | he pod sort affinity of Metaflow-server and Gloabl is or |
| server.podManagementPolicy | string | `"{{ .Values.global.podManagementPolicy }}"`|  
| server.resources | object | `{}` |  |
| server.service | map |  |  |
| app | map |  | Refer to the server |
| config."server.yaml" | string | `` |  |
| tolerations | list | `[]` |  |
| clickhouse.clickhouse.backgroudPoolSize | int | `32` |  |
| clickhouse.clickhouse.connectTimeout | int | `500` |  |
| clickhouse.clickhouse.interserverHttpPort | int | `9009` |  |
| clickhouse.clickhouse.maxAstElements | int | `2000000` |  |
| clickhouse.clickhouse.maxConcurrentQueries | int | `2000` |  |
| clickhouse.clickhouse.maxExpandedAstElements | int | `2000000` |  |
| clickhouse.clickhouse.maxMemoryUsage | int | `10000000000` |  |
| clickhouse.clickhouse.maxQuerySize | int | `10737418240` |  |
| clickhouse.service | map |  |  |
| clickhouse.storageConfig.hostPath | string | `"/opt/metaflow-clickhouse"` | The hostPath directory for Clickhosue, This parameter takes effect when storageConfig. Type =hostPath. Node affinity must be configured to use hostPath |
| clickhouse.storageConfig.persistence | map |  |  |
| clickhouse.storageConfig.s3StorageEnabled | bool | `false` |  |
| clickhouse.storageConfig.type | string | `"persistentVolumeClaim"` |  |
| clickhouse.timezone | string | `"{{ .Values.global.timezone }}"` |  |
| clickhouse.tolerations | list | `[]` |  |
| grafana | map |  | [documentation for grafana](https://github.com/grafana/helm-charts/blob/main/charts/grafana/README.md) |
| metaflow-agent.enabled | bool | `true` |  |
| metaflow-agent.fullnameOverride | string | `"metaflow-agent"` |  |
| metaflow-agent.hostNetwork | string | `"true"` |  |
| metaflow-agent.image.pullPolicy | string | `"{{ .Values.global.image.pullPolicy }}"` |  |
| metaflow-agent.image.repository | string | `"{{ .Values.global.image.repository }}/metaflow-agent"` |  |
| metaflow-agent.image.tag | string | `"latest"` |  |
| metaflow-agent.imagePullSecrets | list | `[]` |  |
| metaflow-agent.metaflowAgentConfig| string | | config for metalfow-agent |
| metaflow-agent.podSecurityContext | object | `{}` |  |
| metaflow-agent.resources | object | `{}` |  |
| metaflow-agent.securityContext.privileged | bool | `true` |  |
| metaflow-agent.service | map | |  |
| metaflow-agent.tolerations | list | `[]` |  |
| mysql.service | map |  |  |
| mysql.storageConfig | map |  | Refer to the clickhouse |
| mysql.timezone | string | `"{{ .Values.global.timezone }}"` |  |
| mysql.tolerations | list | `[]` |  |
