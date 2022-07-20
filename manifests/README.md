# DeepFlow Helm Charts


This repository contains [Helm](https://helm.sh/) charts for DeepFlow project.

## Usage

[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs/) to get started.

Once Helm is set up properly, add the repo as follows:

```console
helm repo add deepflow https://deepflowys.github.io/deepflow
helm repo udpate deepflow
```

## Helm Charts

You can then run `helm search repo deepflow` to see the charts.

_See [helm repo](https://helm.sh/docs/helm/helm_repo/) for command documentation._

## Installing the Chart

To install the chart with the release name `deepflow`:

```console
helm install deepflow -n deepflow deepflow/deepflow --create-namespace
```

## Uninstalling the Chart

To uninstall/delete the my-release deployment:

```console
helm delete deepflow -n deepflow
```

The command removes all the Kubernetes components associated with the chart and deletes the release.


## License

[Apache 2.0 License](./LICENSE).



## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.image.repository | string | `"deepflowys"` |image repository of deepflow component, optional ghcr Image repository address: ghcr.io/deepflowys, Dockerhub Image repository address: deepflowys, AliyunYun Image repository address: registry.cn-beijing.aliyuncs.com/deepflowys |
| global.image.pullPolicy | string | `"Always"` | Image Pull Policy for All Components |
| global.hostNetwork | bool | `false` | Network mode for some components of deepflow-server, deepflow-app, click house, and mysql |
| global.dnsPolicy | string | `"ClusterFirst"` | dns policies for some components of deepflow-server, deepflow-app, click house, and mysql |
| global.password.grafana | string | `"deepflow"` | grafana login password |
| global.password.mysql | string | `"deepflow"` | mysql database login password |
| global.podManagementPolicy | string | `"OrderedReady"` | deepflow-server, clickhouse podManagementPolicy |
| global.replicas | int | `1` | The number of copies of deepflow-server and clickhouse. It is worth noting that the expansion of deepflow must be done through helm because of the static configuration file of the clickhosue cluster. |
| global.podAffinityLabelSelector | list | `[]` | The pod hard affinity of deepflow-server, deepflow-app, clickhouse, mysql and each component's own pod hard affinity are or |
| global.podAffinityTermLabelSelector | list | `[]` | The pod soft affinity of deepflow-server, deepflow-app, clickhouse, and mysql, and the pod soft affinity of each component is or |
| global.podAntiAffinityLabelSelector | list | `[]` | The pod hard anti-affinity of deepflow-server, deepflow-app, clickhouse, mysql and each component's own pod hard anti-affinity relationship is or |
| global.podAntiAffinityTermLabelSelector | list | `[]` | The pod soft anti-affinity of deepflow-server, deepflow-app, clickhouse, mysql and each component's own pod anti-soft affinity are or |
| global.nodeAffinityLabelSelector | list | `[]` | The node hard affinity of deepflow-server, deepflow-app, clickhouse, mysql and each component's own node hard affinity are or |
| global.nodeAffinityTermLabelSelector | list | `[]` | The node soft affinity of deepflow-server, deepflow-app, clickhouse, and mysql, and the node soft affinity of each component is or |
| global.timezone | string | `"Asia/Shanghai"` | your time zone |
| global.nodePort.clickhous | int | `30900` | NodePort exposed by clickhouse, if the default value is not available, please modify it to an available one |
| global.nodePort.deepflowServerGrpc | int | `30035` | NodePort exposed by deepflow-server, if the default value is not available, please modify it to an available one |
| global.nodePort.deepflowServerIngester | int | `30033` | NodePort exposed by deepflow-server, if the default value is not available, please modify it to an available one |
| global.nodePort.deepflowServerSslGrpc | int | `30135` | NodePort exposed by deepflow-server, if the default value is not available, please modify it to an available one |
| global.nodePort.deepflowServerhealthCheck | int | `30417` | NodePort exposed by deepflow-server, if the default value is not available, please modify it to an available one |
| global.ntpServer | string | `"ntp1.aliyun.com"` | ntp time synchronization server address, please modify it to an available address, you need to access udp 123 port |
| image.server.repository | string | `"{{ .Values.global.image.repository }}/deepflow-server"` | The image warehouse address of deepflow-server, supports tpl |
| image.server.tag | string | `"latest"` | image tag of deepflow-server, supports tpl |
| image.server.pullPolicy | string | `"{{ .Values.global.image.pullPolicy }}"` | The image pull strategy of deepflow-server supports tpl |
| image.elector.repository | string | `"{{ .Values.global.image.repository }}/elector"` | The image warehouse address of elector, supports tpl |
| image.elector.tag | string | `"latest"` | image tag of elector, supports tpl |
| image.elector.pullPolicy | string | `"{{ .Values.global.image.pullPolicy }}"` | The image pull strategy of elector supports tpl |
| image.app.repository | string | `"dfcloud-image-registry.cn-beijing.cr.aliyuncs.com/dev/statistics"` | The image warehouse address of deepflow-app, supports tpl |
| image.app.tag | string | `"latest"` | image tag of deepflow-app, supports tpl |
| image.app.pullPolicy | string | `"{{ .Values.global.image.pullPolicy }}"` | The image pull strategy of deepflow-app supports tpl |
| imagePullSecrets | list | `[]` | Pull the key of the image |
| fullnameOverride | string | `""` |  |
| nameOverride | string | `""` |  |
| timezone | string | `"{{ .Values.global.timezone }}"` | Time zone |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| securityContext | object | `{}` |  |
| server.replicas | string | `"{{ .Values.global.replicas }}"` | The replicas of deepflow-server need to be the same as clickhouse |
| server.dnsPolicy | string | `"{{ .Values.global.dnsPolicy }}"` | DNS policy of deepflow-server |
| server.hostNetwork | string | `"{{ .Values.global.hostNetwork }}"` | Network mode of deepflow-server |
| server.nodeAffinityLabelSelector | list | `[]` | The node hard affinity of deepflow-server and Gloabl is or |
| server.nodeAffinityTermLabelSelector | list | `[]` | The node soft affinity of deepflow-server and Gloabl is or |
| server.nodeSelector | object | `{}` |  |
| server.podAffinityLabelSelector | list |  | The pod hard affinity of deepflow-server and Gloabl is or |
| server.podAffinityTermLabelSelector | list | `[]` | The pod sort antiaffinity of deepflow-server and Gloabl is or |
| server.podAntiAffinityLabelSelector | list |  | he pod hard untiaffinity of deepflow-server and Gloabl is or |
| server.podAntiAffinityTermLabelSelector | list | `[]` | he pod sort affinity of deepflow-server and Gloabl is or |
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
| clickhouse.storageConfig.hostPath | string | `"/opt/deepflow-clickhouse"` | The hostPath directory for Clickhosue, This parameter takes effect when storageConfig. Type =hostPath. Node affinity must be configured to use hostPath |
| clickhouse.storageConfig.persistence | map |  |  |
| clickhouse.storageConfig.s3StorageEnabled | bool | `false` |  |
| clickhouse.storageConfig.type | string | `"persistentVolumeClaim"` |  |
| clickhouse.timezone | string | `"{{ .Values.global.timezone }}"` |  |
| clickhouse.tolerations | list | `[]` |  |
| grafana | map |  | [documentation for grafana](https://github.com/grafana/helm-charts/blob/main/charts/grafana/README.md) |
| deepflow-agent.enabled | bool | `true` |  |
| deepflow-agent.fullnameOverride | string | `"deepflow-agent"` |  |
| deepflow-agent.hostNetwork | string | `"true"` |  |
| deepflow-agent.image.pullPolicy | string | `"{{ .Values.global.image.pullPolicy }}"` |  |
| deepflow-agent.image.repository | string | `"{{ .Values.global.image.repository }}/deepflow-agent"` |  |
| deepflow-agent.image.tag | string | `"latest"` |  |
| deepflow-agent.imagePullSecrets | list | `[]` |  |
| deepflow-agent.deepflowAgentConfig| string | | config for metalfow-agent |
| deepflow-agent.podSecurityContext | object | `{}` |  |
| deepflow-agent.resources | object | `{}` |  |
| deepflow-agent.securityContext.privileged | bool | `true` |  |
| deepflow-agent.service | map | |  |
| deepflow-agent.tolerations | list | `[]` |  |
| mysql.service | map |  |  |
| mysql.storageConfig | map |  | Refer to the clickhouse |
| mysql.timezone | string | `"{{ .Values.global.timezone }}"` |  |
| mysql.tolerations | list | `[]` |  |
