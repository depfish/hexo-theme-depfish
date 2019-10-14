---
title: istio概览
catalog: true
date: 2019-09-23 13:57:46
subtitle:
header-img:
tags:
- istio
catagories:
- servicemesh
---

## istio 6大组件及作用
|组件|作用|
|---|---|
|Envoy| Sidecar proxies per microservice to handle ingress/egress traffic|
|Mixer|核心组件,授权、限流|
|Pilot|configuring the proxies at runtime,负责配置proxy|
|Citadel| certificate issuance and rotation，管理证书|
|Citadel Agent|A per-node component responsible for certificate issuance and rotation|
|Galley|Central component for validating, ingesting, aggregating, transforming and distributing config within Istio|

## istio源码结构
可以参考官方 [https://github.com/istio/istio](https://github.com/istio/istio) 的 Introduction部分
|仓库地址|语言|模块|
|---|---|---|
|https://github.com/istio/istio|Go|istio的主要仓库,包括大部分组件: security目录(Citadel和citadel agent), pilot,istioctl, mixer, galley, sidecar-injector等|
|https://github.com/istio/api|Go|包含istio组件之间的API 以及资源配置定义, 使用 protobuf 进行定义|
|https://github.com/istio/proxy|C++|包含 istio 使用的sidecar代理, 这个sidecar代理包含envoy和mixer client两块功能|


https://github.com/istio/istio 包含的主要的镜像和命令:

|容器名|镜像名|启动命令|源码入口|
|---|---|---|---|
|Istio_init|istio/proxy_init|istio-iptables.sh|istio/tools/deb/istio-iptables.sh|
|istio-proxy|istio/proxyv2|pilot-agent|istio/pilot/cmd/pilot-agent|
|sidecar-injector-webhook|istio/sidecar_injector|sidecar-injector|istio/pilot/cmd/sidecar-injector|
|discovery|istio/pilot|pilot-discovery|istio/pilot/cmd/pilot-discovery|
|galley|istio/galley|galley|istio/galley/cmd/galley|
|mixer|istio/mixer|mixs|istio/mixer/cmd/mixs|
|citadel|istio/citadel|istio_ca|istio/security/cmd/istio_ca|

## 参考

[https://jimmysong.io/istio-handbook/concepts/istio-architecture.html](https://jimmysong.io/istio-handbook/concepts/istio-architecture.html)

[https://www.digitalocean.com/community/tutorials/how-to-install-and-use-istio-with-kubernetes](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-istio-with-kubernetes)

[https://www.katacoda.com/courses/istio/deploy-istio-on-kubernetes](https://www.katacoda.com/courses/istio/deploy-istio-on-kubernetes,"在线学习环境")
