### 版本
------

下面记录pan的版本更新历史

#### [v1.0.18](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.18) [2020-07-03]
* 支持不同的失败模式

#### [v1.0.17](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.17) [2020-06-25]
* 修复unixSocket和tcp必须同时开启的限制

#### [v1.0.16](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.16) [2020-06-12]
* 灰度模式校验灰度机IP
* 内存缓冲区大小可配置
* 底层支持leveldb存储

#### [v1.0.15](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.15) [2020-06-05]
* kafka支持灰度发送模式
* 修复queue pop出空数据导致狂刷日志的bug
* 新增日志保留时长配置

#### [v1.0.14](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.14) [2020-05-29]
* kafka可配置消息分区方式
* 增加kafka消息生产超时时间配置

#### [v1.0.13](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.13) [2020-05-15]
* 延时队列key支持自定义
* 增加延时队列获取数据限制
* 增加开关控制消息是否失败回传

#### [v1.0.12](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.12) [2020-04-17]
* 支持延时队列

#### [v1.0.11](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.11) [2020-03-25]
* 修复log bug,增加最大文件打开数设置

#### [v1.0.10](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.10) [2020-03-23]
* rabbitmq 支持设置过期时间

#### [v1.0.9](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.9) [2020-03-17]
* pan支持redis远程存储，整理配置文件

#### [v1.0.8](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.8) [2020-03-11]
* 删除从zk中获取kafka地址的代码，直接从配置中获取kafka地址

#### [v1.0.7](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.7) [2020-02-25]
* 修改socket文件的权限为0777

#### [v1.0.6](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.6) [2020-02-22]
* 修复配置文件中的bug
* Kafka支持认证

#### [v1.0.5](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.5) [2020-02-17]
* 支持不使用白名单

#### [v1.0.4](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.4) [2020-02-13]
* 更新部署脚本

#### [v1.0.3](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.3) [2020-02-07]
* 修改底层协议版本以便支持PHP版本client

#### [v1.0.2](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.2) [2020-02-05]
* 消息发生落盘现象增加Warn日志

#### [v1.0.1](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.1) [2019-12-25]
* 删除一些无用的配置文件
* 更新了supervisor配置
* 增加了针对kafka的性能测试test/kafka_test.go

#### [v1.0.0](https://git.100tal.com/wangxiao_go_center/pan/tree/v1.0.0) [2019-12-09]
* 支持kafka、rabbitmq、rocketmq、nsq四种不同消息队列进行消息生产
* 兼容旧版本的kafkaProxy
* 调整代码整体架构，更易于扩展
* 修复rabbitmq生产逻辑，pan不再关注bind相关操作，只关注将消息生产到指定的exchange


#### 后续版本计划
* 服务注册和服务发现
* 支持更多的消息队列
* 完善监控和日志


