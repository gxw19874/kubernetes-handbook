# 总结

**注意：本书中的 Service Mesh 章节已不再维护，请转到** [**istio-handbook**](https://jimmysong.io/istio-handbook) **中浏览。**

最后是对全书的总结，2018年必然是一场服务网格或者说Proxy的战争。

## 用还是不用

既然Service Mesh这么好，那到底用还是不用，如果用的话应该什么时候用，应该怎么用？这取决于您的公司的云原生技术的成熟度曲线的位置，服务的规模，业务核心和底层基础设施管理是否适应等。

技术总是在不断向前发展，容器出现后，解决的软件环境和分发的问题；但是如何管理分布式的应用呢，又出现了容器编排软件；容器编排软件解决的微服务的部署问题，但是对于微服务的治理的功能太弱，这才出现了Service Mesh，当然Service Mesh也不是万能的，下一步会走向何方呢？会是Serverless吗？我们拭目以待。

Service Mesh还有一些遗留的问题没有解决或者说比较薄弱的功能：

* 分布式应用的调试，可以参考[squash](https://github.com/solo-io/squash)
* 服务拓扑和状态图，可以参考[kiali](https://github.com/kiali/kiali)和[vistio](https://github.com/nmnellis/vistio)
* 多租户和多集群的支持
* 白盒监控、支持APM
* 加强负载测试工具slow\_cooker、fortio、lago等
* 更高级的fallback路径支持
* 可拔插的证书授权组建，支持外部的CA

下面是采纳Service Mesh之前需要考虑的因素。

| 因素 | 可以考虑使用Service Mesh | 强烈建议使用Service Mesh |
| :--- | :--- | :--- |
| 服务通信 | 基本无需跨服务间的通讯 | 十分要求服务间通讯 |
| 可观察性 | 只关注边缘的指标即可 | 内部服务和边缘指标都要考虑以更好的了解服务的行为 |
| 客户关注 | 主要关注外部API的体验，内外用户是隔离的 | 内部外部用户没有区别体验一致 |
| API的界限 | API主要是作为客户端为客户提供，内部的API与外部是分离的 | API即产品，API就是你的产品能力 |
| 安全模型 | 通过边缘、防火墙可信内部网络的方式控制安全 | 所有的服务都需要认证和鉴权、服务间要加密、zero-trust安全观念 |

在考虑完上述因素后，尽量选择开源的平台和解决方案，还要想好开源软件的边界在哪里，哪些能力将是企业版才会提供的。
