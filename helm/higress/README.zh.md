## Higress for Kubernetes

Higress 是基于阿里巴巴内部网关实践打造的云原生 API 网关。

依托 Istio 与 Envoy，Higress 实现了流量网关、微服务网关、安全网关三合一的高集成度架构，从而大幅降低部署运维成本。

## 配置仓库信息

```console
helm repo add higress.io https://higress.io/helm-charts
helm repo update
```

## 安装

以 `higress` 作为发布名称进行安装：

```console
helm install higress -n higress-system higress.io/higress --create-namespace --render-subchart-notes
```

## 卸载

删除 higress 部署：

```console
helm delete higress -n higress-system
```

此命令将移除与图表关联的所有 Kubernetes 组件并删除发布。

## 参数

## 配置项

| 键 | 类型 | 默认值 | 描述 |
|-----|------|---------|-------------|
| clusterName | string | `""` |  |
| controller.affinity | object | `{}` |  |
| controller.automaticHttps.email | string | `""` |  |
| controller.automaticHttps.enabled | bool | `true` |  |
| controller.autoscaling.enabled | bool | `false` |  |
| controller.autoscaling.maxReplicas | int | `5` |  |
| controller.autoscaling.minReplicas | int | `1` |  |
| controller.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| controller.env | object | `{}` |  |
| controller.hub | string | `"higress-registry.cn-hangzhou.cr.aliyuncs.com/higress"` |  |
| controller.image | string | `"higress"` |  |
| controller.imagePullSecrets | list | `[]` |  |
| controller.labels | object | `{}` |  |
| controller.name | string | `"higress-controller"` |  |
| controller.nodeSelector | object | `{}` |  |
| controller.podAnnotations | object | `{}` |  |
| controller.podLabels | object | `{}` | 应用于 Pod 的标签 |
| controller.podSecurityContext | object | `{}` |  |
| controller.ports[0].name | string | `"http"` |  |
| controller.ports[0].port | int | `8888` |  |
| controller.ports[0].protocol | string | `"TCP"` |  |
| controller.ports[0].targetPort | int | `8888` |  |
| controller.ports[1].name | string | `"http-solver"` |  |
| controller.ports[1].port | int | `8889` |  |
| controller.ports[1].protocol | string | `"TCP"` |  |
| controller.ports[1].targetPort | int | `8889` |  |
| controller.ports[2].name | string | `"grpc"` |  |
| controller.ports[2].port | int | `15051` |  |
| controller.ports[2].protocol | string | `"TCP"` |  |
| controller.ports[2].targetPort | int | `15051` |  |
| controller.probe.httpGet.path | string | `"/ready"` |  |
| controller.probe.httpGet.port | int | `8888` |  |
| controller.probe.initialDelaySeconds | int | `1` |  |
| controller.probe.periodSeconds | int | `3` |  |
| controller.probe.timeoutSeconds | int | `5` |  |
| controller.rbac.create | bool | `true` |  |
| controller.replicas | int | `1` | Higress Controller Pod 数量 |
| controller.resources.limits.cpu | string | `"1000m"` |  |
| controller.resources.limits.memory | string | `"2048Mi"` |  |
| controller.resources.requests.cpu | string | `"500m"` |  |
| controller.resources.requests.memory | string | `"2048Mi"` |  |
| controller.securityContext | object | `{}` |  |
| controller.service.type | string | `"ClusterIP"` |  |
| controller.serviceAccount.annotations | object | `{}` | 服务账户的注解 |
| controller.serviceAccount.create | bool | `true` | 指定是否创建服务账户 |
| controller.serviceAccount.name | string | `""` | 如果未设置且 create 为 true，则使用 fullname 模板生成名称 |
| controller.tag | string | `""` |  |
| controller.tolerations | list | `[]` |  |
| downstream | object | `{"connectionBufferLimits":32768,"http2":{"initialConnectionWindowSize":1048576,"initialStreamWindowSize":65535,"maxConcurrentStreams":100},"idleTimeout":180,"maxRequestHeadersKb":60,"routeTimeout":0}` | 下游配置设置 |
| gateway.affinity | object | `{}` |  |
| gateway.annotations | object | `{}` | 应用于所有资源的注解 |
| gateway.autoscaling.enabled | bool | `false` |  |
| gateway.autoscaling.maxReplicas | int | `5` |  |
| gateway.autoscaling.minReplicas | int | `1` |  |
| gateway.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| gateway.containerSecurityContext | string | `nil` |  |
| gateway.env | object | `{}` | Pod 环境变量 |
| gateway.hostNetwork | bool | `false` |  |
| gateway.httpPort | int | `80` |  |
| gateway.httpsPort | int | `443` |  |
| gateway.hub | string | `"higress-registry.cn-hangzhou.cr.aliyuncs.com/higress"` |  |
| gateway.image | string | `"gateway"` |  |
| gateway.kind | string | `"Deployment"` | 使用 `DaemonSet` 或 `Deployment` |
| gateway.labels | object | `{}` | 应用于所有资源的标签 |
| gateway.metrics.enabled | bool | `false` | 如果为 true，为网关创建 PodMonitor 或 VMPodScrape |
| gateway.metrics.honorLabels | bool | `false` |  |
| gateway.metrics.interval | string | `""` |  |
| gateway.metrics.metricRelabelConfigs | list | `[]` | 用于 operator.victoriametrics.com/v1beta1.VMPodScrape |
| gateway.metrics.metricRelabelings | list | `[]` | 用于 monitoring.coreos.com/v1.PodMonitor |
| gateway.metrics.provider | string | `"monitoring.coreos.com"` | CustomResourceDefinition 的提供者组名，可以是 monitoring.coreos.com 或 operator.victoriametrics.com |
| gateway.metrics.rawSpec | object | `{}` | 更多原始 podMetricsEndpoints 配置 |
| gateway.metrics.relabelConfigs | list | `[]` |  |
| gateway.metrics.relabelings | list | `[]` |  |
| gateway.metrics.scrapeTimeout | string | `""` |  |
| gateway.name | string | `"higress-gateway"` |  |
| gateway.networkGateway | string | `""` | 如果指定，网关将作为给定网络的网络网关。 |
| gateway.nodeSelector | object | `{}` |  |
| gateway.podAnnotations."prometheus.io/path" | string | `"/stats/prometheus"` |  |
| gateway.podAnnotations."prometheus.io/port" | string | `"15020"` |  |
| gateway.podAnnotations."prometheus.io/scrape" | string | `"true"` |  |
| gateway.podAnnotations."sidecar.istio.io/inject" | string | `"false"` |  |
| gateway.podLabels | object | `{}` | 应用于 Pod 的标签 |
| gateway.rbac.enabled | bool | `true` | 如果启用，将创建角色以允许从网关访问证书。当使用 http://gateway-api.org/ 时不需要此设置。 |
| gateway.readinessFailureThreshold | int | `30` | 指示准备就绪失败前的连续失败探测次数。 |
| gateway.readinessInitialDelaySeconds | int | `1` | 准备就绪探测的初始延迟秒数。 |
| gateway.readinessPeriodSeconds | int | `2` | 准备就绪探测之间的间隔。 |
| gateway.readinessSuccessThreshold | int | `1` | 指示准备就绪成功前的连续成功探测次数。 |
| gateway.readinessTimeoutSeconds | int | `3` | 准备就绪超时秒数 |
| gateway.replicas | int | `2` | Higress Gateway Pod 数量 |
| gateway.resources.limits.cpu | string | `"2000m"` |  |
| gateway.resources.limits.memory | string | `"2048Mi"` |  |
| gateway.resources.requests.cpu | string | `"2000m"` |  |
| gateway.resources.requests.memory | string | `"2048Mi"` |  |
| gateway.revision | string | `""` | 修订版本声明此网关所属的修订版本 |
| gateway.rollingMaxSurge | string | `"100%"` |  |
| gateway.rollingMaxUnavailable | string | `"25%"` | 如果 global.local 为 true，默认值为 100%，否则为 25% |
| gateway.securityContext | string | `nil` | 定义 Pod 的安全上下文。如果未设置，将自动设置为绑定到端口 80 和 443 所需的最小权限。在 Kubernetes 1.22+ 上，这只需要 `net.ipv4.ip_unprivileged_port_start` 系统调用。 |
| gateway.service.annotations | object | `{}` |  |
| gateway.service.externalTrafficPolicy | string | `""` |  |
| gateway.service.loadBalancerClass | string | `""` |  |
| gateway.service.loadBalancerIP | string | `""` |  |
| gateway.service.loadBalancerSourceRanges | list | `[]` |  |
| gateway.service.ports[0].name | string | `"http2"` |  |
| gateway.service.ports[0].port | int | `80` |  |
| gateway.service.ports[0].protocol | string | `"TCP"` |  |
| gateway.service.ports[0].targetPort | int | `80` |  |
| gateway.service.ports[1].name | string | `"https"` |  |
| gateway.service.ports[1].port | int | `443` |  |
| gateway.service.ports[1].protocol | string | `"TCP"` |  |
| gateway.service.ports[1].targetPort | int | `443` |  |
| gateway.service.type | string | `"LoadBalancer"` | 服务类型。设置为 "None" 以完全禁用服务 |
| gateway.serviceAccount.annotations | object | `{}` | 服务账户的注解 |
| gateway.serviceAccount.create | bool | `true` | 如果设置，将创建服务账户。否则使用默认值 |
| gateway.serviceAccount.name | string | `""` | 使用的服务账户名称。如果未设置，则使用发布名称 |
| gateway.tag | string | `""` |  |
| gateway.tolerations | list | `[]` |  |
| gateway.unprivilegedPortSupported | string | `nil` |  |
| global.autoscalingv2API | bool | `true` | 是否使用 autoscaling/v2 模板进行 HPA 设置，仅供内部使用，用户不应配置。 |
| global.caAddress | string | `""` | 自定义 CA 地址，用于为集群中的 Pod 检索证书。CSR 客户端（如 Istio Agent 和入口网关）可以使用此地址指定 CA 端点。如果未显式设置，则默认为 Istio 发现地址。 |
| global.caName | string | `""` | 工作负载证书的 CA 名称。例如，当 caName=GkeWorkloadCertificate 时，GKE 工作负载证书将用作工作负载的证书。默认值为 ""，当 caName="" 时，CA 将通过其他机制（如环境变量 CA_PROVIDER）配置。 |
| global.configCluster | bool | `false` | 将远程集群配置为外部 istiod 的配置集群。 |
| global.defaultPodDisruptionBudget | object | `{"enabled":false}` | 为控制平面启用 Pod 中断预算，用于确保 Istio 控制平面组件逐步升级或恢复。 |
| global.defaultResources | object | `{"requests":{"cpu":"10m"}}` | 应用于所有部署的最小请求资源集，以便 Horizontal Pod Autoscaler 能够工作（如果设置）。每个组件可以通过在下面的相关部分添加自己的资源块并设置所需的资源值来覆盖这些默认值。 |
| global.defaultUpstreamConcurrencyThreshold | int | `10000` |  |
| global.disableAlpnH2 | bool | `false` | 是否在 ALPN 中禁用 HTTP/2 |
| global.enableGatewayAPI | bool | `false` | 如果为 true，Higress Controller 还将监控 Gateway API 资源 |
| global.enableH3 | string | `"false222"` |  |
| global.enableIPv6 | bool | `false` |  |
| global.enableIstioAPI | bool | `true` | 如果为 true，Higress Controller 还将监控 istio 资源 |
| global.enableLDSCache | bool | `false` |  |
| global.enableProxyProtocol | bool | `false` |  |
| global.enablePushAllMCPClusters | bool | `true` |  |
| global.enableRedis | bool | `false` | 是否为 Higress 启用 Redis(redis-stack-server)，默认为 false。 |
| global.enableSRDS | bool | `true` |  |
| global.enableStatus | bool | `true` | 如果为 true，Higress Controller 将更新 Ingress 资源的状态字段。从 Nginx Ingress 迁移时，为了避免 Ingress 对象的状态字段被覆盖，需要将此参数设置为 false，这样 Higress 就不会将入口 IP 写入相应 Ingress 对象的状态字段。 |
| global.externalIstiod | bool | `false` | 配置由外部 istiod 控制的远程集群数据平面。当设置为 true 时，本地不部署 istiod，仅启用其他发现图表的子集。 |
| global.hostRDSMergeSubset | bool | `false` |  |
| global.hub | string | `"higress-registry.cn-hangzhou.cr.aliyuncs.com/higress"` | Istio 镜像的默认仓库。发布版本发布到 docker hub 的 'istio' 项目下。来自 prow 的开发构建位于 gcr.io |
| global.imagePullPolicy | string | `""` | 如果不需要默认行为，则指定镜像拉取策略。默认行为：最新镜像将始终拉取，否则 IfNotPresent。 |
| global.imagePullSecrets | list | `[]` | 所有 ServiceAccount 的 ImagePullSecrets，用于拉取引用此 ServiceAccount 的 Pod 中的任何镜像的同一命名空间中的秘密列表。对于不使用 ServiceAccounts 的组件（即 grafana、servicegraph、tracing），ImagePullSecrets 将添加到相应的 Deployment(StatefulSet) 对象中。对于配置了私有 docker 注册表的任何集群，必须设置此项。 |
| global.ingressClass | string | `"higress"` | IngressClass 过滤 higress controller 监视的 ingress 资源。默认的 ingress 类是 higress。对于特殊的 ingress 类有一些特殊情况。1. 当 ingress 类设置为 nginx 时，higress controller 将监视具有 nginx ingress 类或没有任何 ingress 类的 ingress 资源。2. 当 ingress 类设置为空时，higress controller 将监视 k8s 集群中的所有 ingress 资源。 |
| global.istioNamespace | string | `"istio-system"` | 用于定位 istiod。 |
| global.istiod | object | `{"enableAnalysis":false}` | 默认在主分支中启用以最大化测试。 |
| global.jwtPolicy | string | `"third-party-jwt"` | 配置验证 JWT 的策略。目前支持两个选项："third-party-jwt" 和 "first-party-jwt"。 |
| global.kind | bool | `false` |  |
| global.liteMetrics | bool | `false` |  |
| global.local | bool | `false` | 当部署到本地集群（例如：kind 集群）时，将此设置为 true。 |
| global.logAsJson | bool | `false` |  |
| global.logging | object | `{"level":"default:info"}` | 以逗号分隔的要输出的消息的最小每范围日志级别，形式为 <scope>:<level>,<scope>:<level> 控制平面根据组件有不同的范围，但可以配置所有组件的默认日志级别 如果为空，将使用代码中配置的默认范围和级别 |
| global.meshID | string | `""` | 如果网格管理员未指定值，Istio 将使用网格信任域的值。最佳实践是选择一个适当的信任域值。 |
| global.meshNetworks | object | `{}` |  |
| global.mountMtlsCerts | bool | `false` | 使用用户指定的、挂载为秘密卷的密钥和证书用于 Pilot 和工作负载。 |
| global.multiCluster.clusterName | string | `""` | 应设置为运行此安装的集群的名称。这对于 sidecar 注入正确标记代理是必需的 |
| global.multiCluster.enabled | bool | `true` | 设置为 true 以通过各自的 ingressgateway 服务连接两个 kubernetes 集群，当每个集群中的 Pod 无法直接相互通信时。所有集群都应使用 Istio mTLS，并且必须具有共享的根 CA 才能使此模型工作。 |
| global.network | string | `""` | 网络定义此集群所属的网络。此名称对应于网格网络映射中的网络。 |
| global.o11y | object | `{"enabled":false,"promtail":{"image":{"repository":"higress-registry.cn-hangzhou.cr.aliy