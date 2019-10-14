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

## istio源码结构
|仓库地址|语言|模块|
|---|---|---|
|https://github.com/istio/istio|Go|包含istio控制面的大部分组件: pilot, mixer, citadel, galley, sidecar-injector等|
|https://github.com/istio/proxy|C++|包含 istio 使用的sidecar代理, 这个边车代理包含envoy和mixer client两块功能|
|https://github.com/istio/api|Go|包含istio组件之间的API 以及资源配置定义, 使用 protobuf 进行定义|


## 参考

[https://jimmysong.io/istio-handbook/concepts/istio-architecture.html](https://jimmysong.io/istio-handbook/concepts/istio-architecture.html)

[https://www.digitalocean.com/community/tutorials/how-to-install-and-use-istio-with-kubernetes](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-istio-with-kubernetes)

[https://www.katacoda.com/courses/istio/deploy-istio-on-kubernetes](https://www.katacoda.com/courses/istio/deploy-istio-on-kubernetes,"在线学习环境")
