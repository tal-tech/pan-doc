### 简介
------

Pan 是使用纯Go语言编写的高性能高稳定的消息中间件生产端代理, 支持市面上主流的消息队列，例如kafka、rabbitmq、rocketmq、nsq等，而且易于扩展，可满足生产环境下不同的业务需求。

 * [**简介**](README.md)
    * [背景](introduce/background.md)
    * [特性](introduce/special.md)

 * [**快速开始**](quickstart/quickstart.md)
    * [kafka](quickstart/kafka.md)
    * [rabbitmq](quickstart/rabbitmq.md)
    * [rocketmq](quickstart/rocketmq.md)
    * [nsq](quickstart/nsq.md)
    * [延时队列](quickstart/delaymq.md)
    
 * [**架构**](design/design.md)
    * [架构设计](design/framework.md)
    * [server](design/server.md)
    * [pchan](design/pchan.md)
    * [proxy](design/proxy.md)

* [**配置**](config/config.md)
    * [基础配置](config/base.md)
    * [队列配置](config/mq.md)

* [**部署**](deploy/local.md)

* [**测试**](test/test.md)
    * [性能测试](test/performance.md)
    
* [**稳定性建设**](test/stable.md)

