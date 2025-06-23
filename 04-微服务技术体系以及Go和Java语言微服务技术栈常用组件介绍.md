
## 一、微服务技术体系
下图列出了微服务的技术体系：

![](https://img2020.cnblogs.com/blog/650581/202007/650581-20200714192039539-1038488973.png)

## 二、Golang微服务技术栈

### Go 微服务技术栈思维导图

![image](https://img2023.cnblogs.com/blog/650581/202311/650581-20231110174011014-599130233.png)


### 微服务框架
- [go-micro](https://github.com/micro/go-micro)
- [go-kit](https://github.com/go-kit/kit)

国内的bilibili、好未来和斗鱼也出了一个微服务框架：
- [kratos](https://github.com/go-kratos/kratos) bilibili B站出品
- [jupiter](https://github.com/douyu/jupiter) 斗鱼出品
- [go-zero](https://github.com/zeromicro/go-zero) 好未来出品

### 网关
- [kong](https://github.com/Kong/kong)
- [nginx](https://github.com/nginx/nginx)+lua
- [traefik](https://docs.traefik.io)
- [apisix](https://github.com/apache/incubator-apisix)

### 服务注册和发现
- [consul](https://github.com/hashicorp/consul)
- [etcd](https://github.com/etcd-io/etcd)
- [zookeeper](https://zookeeper.apache.org)

### 配置中心
- [Apollo](https://github.com/ctripcorp/apollo)，
- [Nacos](https://github.com/alibaba/Nacos)

... ...

### 服务治理
断路器：
- [hystrix-go](https://github.com/afex/hystrix-go)

流量控制：
- [sentinel-golang](https://github.com/alibaba/sentinel-golang) 
从限流、流量整形、熔断降级、系统负载保护等多个维度来帮助您保障微服务的稳定性。

### 链路监控
zipkin，pinpoint，skywalking，jaeger

### 日志、业务、系统监控
[prometheus](https://prometheus.io/)
[ELK](https://www.elastic.co/)

### CI/CD
- [jenkins](https://www.jenkins.io)
- [drone](https://drone.io/)

......

> golang技术学习和微服务学习，[这里有个学习路线图](https://github.com/jiujuan/go-collection)，可以去学习

## 三、java微服务技术栈

用java技术开发微服务，比较主流的选择有：Spring Cloud 和 Dubbo。

### Spring Cloud

[Spring Cloud](https://github.com/spring-cloud)是在Spring基础上构建的，它后面有2大公司支撑，Pivotal 和 Netflix 的技术支持。它的核心就是 Netflix 贡献的源码，也是这家公司构建了整套微服务体系，才使得微服务架构逐渐流行开来，所以说Netflix在微服务上的贡献是巨大的。

#### Pivotal 的 SpingCloud 框架

[Spring Cloud](https://github.com/spring-cloud) ，这个是 Pivotal 集成了 Netflix，或者重新改写了它的框架。

![SpringCloud（Pivotal）组件](https://github.com/user-attachments/assets/c99391d5-f514-46e8-99d1-d8c3c68c5b09)



Spring 是一个全家桶，Spring Cloud 也是一个全家桶，它由很多技术组件组合而成：

- **断路器**：Hystrix

- **服务注册和发现**：Netflix Eureka
  当然我们也有其他的选择，比如consul，etcd，zookeeper等
  
- **负载均衡**：Ribbon

- **REST客户端**：Feign、openfeign
  
- **网关**：
  API 网关：Zuul
  
  当然我们也可以选择其他的，比如Spring Cloud Gateway，kong，nginx+lua，apisix等
  
- **分布式链路监控**：
  - Spring Cloud Sleuth：埋点和发送数据
    
  当然还有其他的比如 zipkin，pinpoint，skywalking，jaeger等
  
- **消息组件**：
  - Spring Cloud Stream
  - Spirng Cloud Bus
    
  消息中间件的其他软件：RocketMQ，Kafka，RabbitMQ
  
- **配置中心**：
  - Spring Cloud Config
    
   配置中心可以有其他的替代，比如Apollo，Nacos等
  
- **安全控制**：
  - Spring Cloud Security
  
  
[https://spring.io/projects/spring-cloud](https://spring.io/projects/spring-cloud) 这个地址列出了springcloud各种框架，就是它的文档地址。

#### 阿里巴巴的SpringCloud

阿里巴巴在SpringCloud之上，开发了自己的微服务框架[spring-cloud-alibaba](https://github.com/alibaba/spring-cloud-alibaba) 。
- [spring-cloud-alibaba wiki](https://github.com/alibaba/spring-cloud-alibaba/wiki)

##### 主要功能

- **服务限流降级**：默认支持 WebServlet、WebFlux, OpenFeign、RestTemplate、Spring Cloud Gateway, Zuul, Dubbo 和 RocketMQ 限流降级功能的接入，可以在运行时通过控制台实时修改限流降级规则，还支持查看限流降级 Metrics 监控。
- **服务注册与发现**：适配 Spring Cloud 服务注册与发现标准，默认集成了 Ribbon 的支持。
- **分布式配置管理**：支持分布式系统中的外部化配置，配置更改时自动刷新。消息驱动能力：基于 Spring Cloud Stream 为微服务应用构建消息驱动能力。
- **分布式事务**：使用 @GlobalTransactional 注解， 高效并且对业务零侵入地解决分布式事务问题。
- **阿里云对象存储**：阿里云提供的海量、安全、低成本、高可靠的云存储服务。支持在任何应用、任何时间、任何地点存储和访问任意类型的数据。
- **分布式任务调度**：提供秒级、精准、高可靠、高可用的定时（基于 Cron 表达式）任务调度服务。同时提供分布式的任务执行模型，如网格任务。网格任务支持海量子任务均匀分配到所有 Worker（schedulerx-client）上执行。
- **阿里云短信服务**：覆盖全球的短信服务，友好、高效、智能的互联化通讯能力，帮助企业迅速搭建客户触达通道。

> 看上面介绍，集成了阿里云的一些服务。

##### 组件

[Sentinel](https://github.com/alibaba/Sentinel)：把流量作为切入点，从流量控制、熔断降级、系统负载保护等多个维度保护服务的稳定性。

[Nacos](https://github.com/alibaba/Nacos)：一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台。

[RocketMQ](https://rocketmq.apache.org/)：一款开源的分布式消息系统，基于高可用分布式集群技术，提供低延时的、高可靠的消息发布与订阅服务。

[Dubbo](https://github.com/apache/dubbo)：Apache Dubbo™ 是一款高性能 Java RPC 框架。

[Seata](https://github.com/seata/seata)：阿里巴巴开源产品，一个易于使用的高性能微服务分布式事务解决方案。

[Alibaba Cloud ACM](https://www.aliyun.com/product/acm)：一款在分布式架构环境中对应用配置进行集中管理和推送的应用配置中心产品。

Alibaba Cloud OSS: 阿里云对象存储服务（Object Storage Service，简称 OSS），是阿里云提供的海量、安全、低成本、高可靠的云存储服务。您可以在任何应用、任何时间、任何地点存储和访问任意类型的数据。

Alibaba Cloud SchedulerX: 阿里中间件团队开发的一款分布式任务调度产品，提供秒级、精准、高可靠、高可用的定时（基于 Cron 表达式）任务调度服务。

Alibaba Cloud SMS: 覆盖全球的短信服务，友好、高效、智能的互联化通讯能力，帮助企业迅速搭建客户触达通道。

> 也是集成了一些阿里云的服务

### Dubbo
从上面spring-cloud-alibabba组件组成来看，Dubbo是它的一个子框架。
Dubbo的治理能力相当丰富，文档也很完善。[中文文档](http://dubbo.apache.org/zh-cn/docs/user/quick-start.html) [英文文档](http://dubbo.apache.org/en-us/docs/user/quick-start.html)，这是它的一个优势。

Dubbo具有调度、发现、监控、治理、服务发现等功能。
优点：
- Dubbo 支持 RPC 调用，服务之间的调用性能会很好
- 支持多种序列化协议，如 Hessian、HTTP、WebService。
- Dobbo Admin后台管理功能强大，提供了路由规则、动态配置、访问控制、权重调节、均衡负载等功能。
- 在国内影响力比较大，中文社区文档较为全面。

缺点：
- 它只是微服务的一个子集，一个子框架。服务治理
- 国内公司用的多，阿里以前不维护，现在重启维护

阿里以前没有进行维护，现在重启维护，而且还捐献给了apache基金会。

### Dubbo和Spring Cloud对比
![](https://img2020.cnblogs.com/blog/650581/202007/650581-20200714192202818-1795575891.png)


Dubbo是专注于RPC和服务治理，Spring Cloud是一个微服务的全家桶，也可以说是微服务生态，功能齐全，社区维护也积极。
SpringCloud国内外公司应用多，dubbo主要是国内公司用的多。

### java微服务框架总结
就微服务体系来说，Dubbo只是整个微服务的一部分。Spring Cloud是一整套微服务体系，它是一个完整的解决方案。Spring Cloud社区强大，也很活跃。



## 参考
- https://spring.io/projects/spring-cloud
- https://github.com/spring-cloud
- https://github.com/spring-projects/spring-cloud
- https://github.com/alibaba/spring-cloud-alibaba/blob/master/README-zh.md
- https://blog.csdn.net/karamos/article/details/80127976 网易考拉海购Dubbok框架优化详解
- https://www.zhihu.com/question/45413135 spring cloud 和 dubbo 各自的优缺点是什么?
- https://www.cnblogs.com/xishuai/p/dubbo-and-spring-cloud.html Java微服务框架选型（Dubbo 和 Spring Cloud？）
