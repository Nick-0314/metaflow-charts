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
| server.dnsPolicy | string | `"{{ .Values.global.dnsPolicy }}"` |  |
| server.hostNetwork | string | `"{{ .Values.global.hostNetwork }}"` |  |
| server.nodeAffinityLabelSelector | list | `[]` |  |
| server.nodeAffinityTermLabelSelector | list | `[]` |  |
| server.nodeSelector | object | `{}` |  |
| server.podAffinityLabelSelector[0].labelSelector[0].key | string | `"app"` |  |
| server.podAffinityLabelSelector[0].labelSelector[0].operator | string | `"In"` |  |
| server.podAffinityLabelSelector[0].labelSelector[0].values | string | `"metaflow"` |  |
| server.podAffinityLabelSelector[0].labelSelector[1].key | string | `"component"` |  |
| server.podAffinityLabelSelector[0].labelSelector[1].operator | string | `"In"` |  |
| server.podAffinityLabelSelector[0].labelSelector[1].values | string | `"clickhouse"` |  |
| server.podAffinityLabelSelector[0].topologyKey | string | `"kubernetes.io/hostname"` |  |
| server.podAffinityTermLabelSelector | list | `[]` |  |
| server.podAntiAffinityLabelSelector[0].labelSelector[0].key | string | `"app"` |  |
| server.podAntiAffinityLabelSelector[0].labelSelector[0].operator | string | `"In"` |  |
| server.podAntiAffinityLabelSelector[0].labelSelector[0].values | string | `"metaflow"` |  |
| server.podAntiAffinityLabelSelector[0].labelSelector[1].key | string | `"component"` |  |
| server.podAntiAffinityLabelSelector[0].labelSelector[1].operator | string | `"In"` |  |
| server.podAntiAffinityLabelSelector[0].labelSelector[1].values | string | `"metaflow-server"` |  |
| server.podAntiAffinityLabelSelector[0].topologyKey | string | `"kubernetes.io/hostname"` |  |
| server.podAntiAffinityTermLabelSelector | list | `[]` |  |
| server.podManagementPolicy | string | `"{{ .Values.global.podManagementPolicy }}"`|  
| server.resources | object | `{}` |  |
| server.service.additionalPorts | list | `[]` |  |
| server.service.annotations | object | `{}` |  |
| server.service.clusterIP | string | `""` |  |
| server.service.externalIPs | list | `[]` |  |
| server.service.externalTrafficPolicy | string | `"Local"` |  |
| server.service.labels | object | `{}` |  |
| server.service.loadBalancerIP | string | `""` |  |
| server.service.loadBalancerSourceRanges | list | `[]` |  |
| server.service.ports[0].name | string | `"querier"` |  |
| server.service.ports[0].nodePort | string | `nil` |  |
| server.service.ports[0].port | int | `20416` |  |
| server.service.ports[0].protocol | string | `"TCP"` |  |
| server.service.ports[0].targetPort | int | `20416` |  |
| server.service.ports[1].name | string | `"health-check"` |  |
| server.service.ports[1].nodePort | string | `"{{ .Values.global.nodePort.metaflowServerhealthCheck }}"` |  |
| server.service.ports[1].port | int | `20417` |  |
| server.service.ports[1].protocol | string | `"TCP"` |  |
| server.service.ports[1].targetPort | int | `20417` |  |
| server.service.ports[2].name | string | `"grpc"` |  |
| server.service.ports[2].nodePort | string | `"{{ .Values.global.nodePort.metaflowServerGrpc }}"` |  |
| server.service.ports[2].port | int | `20035` |  |
| server.service.ports[2].protocol | string | `"TCP"` |  |
| server.service.ports[2].targetPort | int | `20035` |  |
| server.service.ports[3].name | string | `"ssl-grpc"` |  |
| server.service.ports[3].nodePort | string | `"{{ .Values.global.nodePort.metaflowServerSslGrpc }}"` |  |
| server.service.ports[3].port | int | `20135` |  |
| server.service.ports[3].protocol | string | `"TCP"` |  |
| server.service.ports[3].targetPort | int | `20135` |  |
| server.service.ports[4].name | string | `"ingester"` |  |
| server.service.ports[4].nodePort | string | `"{{ .Values.global.nodePort.metaflowServerIngester }}"` |  |
| server.service.ports[4].port | int | `20033` |  |
| server.service.ports[4].protocol | string | `"TCP"` |  |
| server.service.ports[4].targetPort | int | `20033` |  |
| server.service.type | string | `"NodePort"` |  |

| tolerations | list | `[]` |  |




| app.dnsPolicy | string | `"{{ .Values.global.dnsPolicy }}"` |  |
| app.hostNetwork | string | `"{{ .Values.global.hostNetwork }}"` |  |
| app.nodeAffinityLabelSelector | list | `[]` |  |
| app.nodeAffinityTermLabelSelector | list | `[]` |  |
| app.nodeSelector | object | `{}` |  |
| app.podAffinityLabelSelector | list | `[]` |  |
| app.podAffinityTermLabelSelector | list | `[]` |  |
| app.podAntiAffinityLabelSelector | list | `[]` |  |
| app.podAntiAffinityTermLabelSelector | list | `[]` |  |
| app.replicas | string | `"1"` |  |
| app.resources | object | `{}` |  |
| app.service.additionalPorts | list | `[]` |  |
| app.service.annotations | object | `{}` |  |
| app.service.clusterIP | string | `""` |  |
| app.service.externalIPs | list | `[]` |  |
| app.service.externalTrafficPolicy | string | `"Cluster"` |  |
| app.service.labels | object | `{}` |  |
| app.service.loadBalancerIP | string | `""` |  |
| app.service.loadBalancerSourceRanges | list | `[]` |  |
| app.service.ports[0].name | string | `"app"` |  |
| app.service.ports[0].nodePort | string | `nil` |  |
| app.service.ports[0].port | int | `20404` |  |
| app.service.ports[0].protocol | string | `"TCP"` |  |
| app.service.ports[0].targetPort | int | `20404` |  |
| app.service.type | string | `"ClusterIP"` |  |
| clickhouse.clickhouse.backgroudPoolSize | int | `32` |  |
| clickhouse.clickhouse.connectTimeout | int | `500` |  |
| clickhouse.clickhouse.interserverHttpPort | int | `9009` |  |
| clickhouse.clickhouse.maxAstElements | int | `2000000` |  |
| clickhouse.clickhouse.maxConcurrentQueries | int | `2000` |  |
| clickhouse.clickhouse.maxExpandedAstElements | int | `2000000` |  |
| clickhouse.clickhouse.maxMemoryUsage | int | `10000000000` |  |
| clickhouse.clickhouse.maxQuerySize | int | `10737418240` |  |
| clickhouse.dnsPolicy | string | `"{{ .Values.global.dnsPolicy }}"` |  |
| clickhouse.fullnameOverride | string | `""` |  |
| clickhouse.hostNetwork | string | `"{{ .Values.global.hostNetwork }}"` |  |
| clickhouse.image.pullPolicy | string | `"IfNotPresent"` |  |
| clickhouse.image.repository | string | `"clickhouse/clickhouse-server"` |  |
| clickhouse.image.tag | string | `"21.8.15.7"` |  |
| clickhouse.imagePullSecrets | list | `[]` |  |
| clickhouse.nameOverride | string | `""` |  |
| clickhouse.nodeAffinityLabelSelector | list | `[]` |  |
| clickhouse.nodeAffinityTermLabelSelector | list | `[]` |  |
| clickhouse.nodeSelector | object | `{}` |  |
| clickhouse.podAffinityLabelSelector | list | `[]` |  |
| clickhouse.podAffinityTermLabelSelector | list | `[]` |  |
| clickhouse.podAnnotations | object | `{}` |  |
| clickhouse.podAntiAffinityLabelSelector[0].labelSelector[0].key | string | `"app"` |  |
| clickhouse.podAntiAffinityLabelSelector[0].labelSelector[0].operator | string | `"In"` |  |
| clickhouse.podAntiAffinityLabelSelector[0].labelSelector[0].values | string | `"metaflow"` |  |
| clickhouse.podAntiAffinityLabelSelector[0].labelSelector[1].key | string | `"component"` |  |
| clickhouse.podAntiAffinityLabelSelector[0].labelSelector[1].operator | string | `"In"` |  |
| clickhouse.podAntiAffinityLabelSelector[0].labelSelector[1].values | string | `"clickhouse"` |  |
| clickhouse.podAntiAffinityLabelSelector[0].topologyKey | string | `"kubernetes.io/hostname"` |  |
| clickhouse.podAntiAffinityTermLabelSelector | list | `[]` |  |
| clickhouse.podManagementPolicy | string | `"{{ .Values.global.podManagementPolicy }}"` |  |
| clickhouse.podSecurityContext | object | `{}` |  |
| clickhouse.replicas | string | `"{{ .Values.global.replicas }}"` |  |
| clickhouse.resources | object | `{}` |  |
| clickhouse.securityContext | object | `{}` |  |
| clickhouse.service.additionalPorts | list | `[]` |  |
| clickhouse.service.annotations | object | `{}` |  |
| clickhouse.service.clusterIP | string | `""` |  |
| clickhouse.service.externalIPs | list | `[]` |  |
| clickhouse.service.externalTrafficPolicy | string | `"Local"` |  |
| clickhouse.service.labels | object | `{}` |  |
| clickhouse.service.loadBalancerIP | string | `""` |  |
| clickhouse.service.loadBalancerSourceRanges | list | `[]` |  |
| clickhouse.service.ports[0].name | string | `"http-monitor-port"` |  |
| clickhouse.service.ports[0].nodePort | string | `nil` |  |
| clickhouse.service.ports[0].port | int | `8123` |  |
| clickhouse.service.ports[0].protocol | string | `"TCP"` |  |
| clickhouse.service.ports[0].targetPort | int | `8123` |  |
| clickhouse.service.ports[1].name | string | `"tcp-port"` |  |
| clickhouse.service.ports[1].nodePort | string | `"{{ .Values.global.clickhouseNodePort }}"` |  |
| clickhouse.service.ports[1].port | int | `9000` |  |
| clickhouse.service.ports[1].protocol | string | `"TCP"` |  |
| clickhouse.service.ports[1].targetPort | int | `9000` |  |
| clickhouse.service.ports[2].name | string | `"interserver-http-port"` |  |
| clickhouse.service.ports[2].nodePort | string | `nil` |  |
| clickhouse.service.ports[2].port | int | `9009` |  |
| clickhouse.service.ports[2].protocol | string | `"TCP"` |  |
| clickhouse.service.ports[2].targetPort | int | `9009` |  |
| clickhouse.service.type | string | `"NodePort"` |  |
| clickhouse.storageConfig.hostPath | string | `"/opt/metaflow-clickhouse"` |  |
| clickhouse.storageConfig.persistence[0].accessModes[0] | string | `"ReadWriteOnce"` |  |
| clickhouse.storageConfig.persistence[0].annotations | string | `nil` |  |
| clickhouse.storageConfig.persistence[0].name | string | `"clickhouse-path"` |  |
| clickhouse.storageConfig.persistence[0].size | string | `"100Gi"` |  |
| clickhouse.storageConfig.persistence[0].storageClass | string | `"-"` |  |
| clickhouse.storageConfig.persistence[1].accessModes[0] | string | `"ReadWriteOnce"` |  |
| clickhouse.storageConfig.persistence[1].annotations | string | `nil` |  |
| clickhouse.storageConfig.persistence[1].name | string | `"clickhouse-storage-path"` |  |
| clickhouse.storageConfig.persistence[1].size | string | `"200Gi"` |  |
| clickhouse.storageConfig.persistence[1].storageClass | string | `"-"` |  |
| clickhouse.storageConfig.s3StorageEnabled | bool | `false` |  |
| clickhouse.storageConfig.type | string | `"persistentVolumeClaim"` |  |
| clickhouse.timezone | string | `"{{ .Values.global.timezone }}"` |  |
| clickhouse.tolerations | list | `[]` |  |
| config."server.yaml" | string | `` |  |

| grafana."grafana.ini".analytics.check_for_updates | bool | `true` |  |
| grafana."grafana.ini".database.host | string | `"{{ $.Release.Name }}-mysql:30130"` |  |
| grafana."grafana.ini".database.name | string | `"grafana"` |  |
| grafana."grafana.ini".database.password | string | `"{{ .Values.global.password.mysql }}"` |  |
| grafana."grafana.ini".database.type | string | `"mysql"` |  |
| grafana."grafana.ini".database.user | string | `"root"` |  |
| grafana."grafana.ini".log.mode | string | `"console"` |  |
| grafana."grafana.ini".paths.plugins | string | `"/var/lib/grafana/plugins"` |  |
| grafana."grafana.ini".plugins.allow_loading_unsigned_plugins | string | `"yunshan-metaflow-datasource,yunshan-metaflow-panel,metaflow-topo-panel"` |  |
| grafana.adminPassword | string | `"{{ .Values.global.password.grafana }}"` |  |
| grafana.datasources."datasources.yaml".apiVersion | int | `1` |  |
| grafana.datasources."datasources.yaml".datasources[0].access | string | `"proxy"` |  |
| grafana.datasources."datasources.yaml".datasources[0].isDefault | bool | `true` |  |
| grafana.datasources."datasources.yaml".datasources[0].jsonData.requestUrl | string | `"http://{{ include \"metaflow.fullname\" . }}-server:20416"` |  |
| grafana.datasources."datasources.yaml".datasources[0].jsonData.traceUrl | string | `"http://{{ include \"metaflow.fullname\" . }}-app:20404"` |  |
| grafana.datasources."datasources.yaml".datasources[0].name | string | `"MetaFlow"` |  |
| grafana.datasources."datasources.yaml".datasources[0].type | string | `"yunshan-metaflow-datasource"` |  |
| grafana.datasources."datasources.yaml".datasources[0].url | string | `nil` |  |
| grafana.defaultDashboardsEnabled | bool | `true` |  |
| grafana.defaultDashboardsTimezone | string | `"utc"` |  |
| grafana.enabled | bool | `true` |  |
| grafana.extraEmptyDirMounts[0].mountPath | string | `"/var/lib/grafana/plugins"` |  |
| grafana.extraEmptyDirMounts[0].name | string | `"custom-plugins"` |  |
| grafana.extraInitContainers[0].args[0] | string | `"-c"` |  |
| grafana.extraInitContainers[0].args[1] | string | `"cp -raf /metaflow-plugins/* /var/lib/grafana/plugins/"` |  |
| grafana.extraInitContainers[0].command[0] | string | `"sh"` |  |
| grafana.extraInitContainers[0].image | string | `"{{ .Values.global.image.repository }}/metaflow-init-grafana:latest"` |  |
| grafana.extraInitContainers[0].imagePullPolicy | string | `"{{ tpl .Values.global.image.pullPolicy . }}"` |  |
| grafana.extraInitContainers[0].name | string | `"init-custom-plugins"` |  |
| grafana.extraInitContainers[0].volumeMounts[0].mountPath | string | `"/var/lib/grafana/plugins/"` |  |
| grafana.extraInitContainers[0].volumeMounts[0].name | string | `"custom-plugins"` |  |
| grafana.forceDeployDashboards | bool | `false` |  |
| grafana.forceDeployDatasources | bool | `false` |  |
| grafana.namespaceOverride | string | `""` |  |
| grafana.rbac.create | bool | `true` |  |
| grafana.rbac.namespaced | bool | `true` |  |
| grafana.rbac.pspEnabled | bool | `false` |  |
| grafana.service.enabled | bool | `true` |  |
| grafana.service.type | string | `"NodePort"` |  |
| grafana.sidecar.dashboards.annotations | object | `{}` |  |
| grafana.sidecar.dashboards.enabled | bool | `true` |  |
| grafana.sidecar.dashboards.label | string | `"grafana_dashboard"` |  |
| grafana.sidecar.dashboards.labelValue | string | `"1"` |  |
| grafana.sidecar.dashboards.provider.allowUiUpdates | bool | `false` |  |
| grafana.sidecar.skipTlsVerify | bool | `true` |  |


| metaflow-agent.enabled | bool | `true` |  |
| metaflow-agent.fullnameOverride | string | `"metaflow-agent"` |  |
| metaflow-agent.hostNetwork | string | `"true"` |  |
| metaflow-agent.image.pullPolicy | string | `"{{ .Values.global.image.pullPolicy }}"` |  |
| metaflow-agent.image.repository | string | `"{{ .Values.global.image.repository }}/metaflow-agent"` |  |
| metaflow-agent.image.tag | string | `"latest"` |  |
| metaflow-agent.imagePullSecrets | list | `[]` |  |
| metaflow-agent.metaflowAgentConfig."metaflow-agent.yaml" | string | `"controller-ips:\n- \"{{ $.Release.Name }}-server-headless\"\n# kubernetes-cluster-id: __K8S_CLUSTER_ID__\n# ingress-flavour: __INGRESS_FLAVOUR__\n# vtap-group-id-request: \"__VTAPGROUPID__\"\n"` |  |
| metaflow-agent.nameOverride | string | `""` |  |
| metaflow-agent.nodeAffinityLabelSelector | list | `[]` |  |
| metaflow-agent.nodeAffinityTermLabelSelector | list | `[]` |  |
| metaflow-agent.nodeSelector | object | `{}` |  |
| metaflow-agent.podAffinityLabelSelector | list | `[]` |  |
| metaflow-agent.podAffinityTermLabelSelector | list | `[]` |  |
| metaflow-agent.podAnnotations | object | `{}` |  |
| metaflow-agent.podAntiAffinityLabelSelector | list | `[]` |  |
| metaflow-agent.podAntiAffinityTermLabelSelector | list | `[]` |  |
| metaflow-agent.podSecurityContext | object | `{}` |  |
| metaflow-agent.resources | object | `{}` |  |
| metaflow-agent.securityContext.privileged | bool | `true` |  |
| metaflow-agent.service.additionalPorts | list | `[]` |  |
| metaflow-agent.service.annotations | object | `{}` |  |
| metaflow-agent.service.clusterIP | string | `""` |  |
| metaflow-agent.service.externalIPs | list | `[]` |  |
| metaflow-agent.service.externalTrafficPolicy | string | `"Local"` |  |
| metaflow-agent.service.labels | object | `{}` |  |
| metaflow-agent.service.loadBalancerIP | string | `""` |  |
| metaflow-agent.service.loadBalancerSourceRanges | list | `[]` |  |
| metaflow-agent.service.ports[0].name | string | `"otel"` |  |
| metaflow-agent.service.ports[0].nodePort | string | `nil` |  |
| metaflow-agent.service.ports[0].port | int | `4317` |  |
| metaflow-agent.service.ports[0].protocol | string | `"TCP"` |  |
| metaflow-agent.service.ports[0].targetPort | int | `4317` |  |
| metaflow-agent.service.type | string | `"ClusterIP"` |  |
| metaflow-agent.tolerations | list | `[]` |  |
| mysql.dnsPolicy | string | `"ClusterFirst"` |  |
| mysql.externalMySQL.enabled | bool | `false` |  |
| mysql.externalMySQL.hostIP | string | `"192.168.1.1"` |  |
| mysql.externalMySQL.port | int | `30130` |  |
| mysql.fullnameOverride | string | `""` |  |
| mysql.hostNetwork | string | `"false"` |  |
| mysql.imagePullSecrets | list | `[]` |  |
| mysql.nameOverride | string | `""` |  |
| mysql.nodeAffinityLabelSelector | list | `[]` |  |
| mysql.nodeAffinityTermLabelSelector | list | `[]` |  |
| mysql.nodeSelector | object | `{}` |  |
| mysql.password | string | `"{{ .Values.global.password.mysql }}"` |  |
| mysql.podAffinityLabelSelector | list | `[]` |  |
| mysql.podAffinityTermLabelSelector | list | `[]` |  |
| mysql.podAnnotations | object | `{}` |  |
| mysql.podAntiAffinityLabelSelector | list | `[]` |  |
| mysql.podAntiAffinityTermLabelSelector | list | `[]` |  |
| mysql.podSecurityContext | object | `{}` |  |
| mysql.resources | object | `{}` |  |
| mysql.securityContext | string | `nil` |  |
| mysql.service.additionalPorts | list | `[]` |  |
| mysql.service.annotations | object | `{}` |  |
| mysql.service.clusterIP | string | `""` |  |
| mysql.service.externalIPs | list | `[]` |  |
| mysql.service.externalTrafficPolicy | string | `"Cluster"` |  |
| mysql.service.labels | object | `{}` d |  |
| mysql.service.loadBalancerIP | string | `""` |  |
| mysql.service.loadBalancerSourceRanges | list | `[]` |  |
| mysql.service.ports[0].name | string | `"tcp"` |  |
| mysql.service.ports[0].nodePort | string | `nil` |  |
| mysql.service.ports[0].port | int | `30130` |  |
| mysql.service.ports[0].protocol | string | `"TCP"` |  |
| mysql.service.ports[0].targetPort | int | `30130` |  |
| mysql.service.type | string | `"ClusterIP"` |  |
| mysql.storageConfig.hostPath | string | `"/opt/metaflow-mysql"` |  |
| mysql.storageConfig.hostPathChownContainerEnabled | bool | `true` |  |
| mysql.storageConfig.persistence.accessMode | string | `"ReadWriteOnce"` |  |
| mysql.storageConfig.persistence.annotations."helm.sh/resource-policy" | string | `"keep"` |  |
| mysql.storageConfig.persistence.size | string | `"50Gi"` |  |
| mysql.storageConfig.persistence.storageClass | string | `"-"` |  |
| mysql.storageConfig.type | string | `"persistentVolumeClaim"` |  |
| mysql.timezone | string | `"{{ .Values.global.timezone }}"` |  |
| mysql.tolerations | list | `[]` |  |
