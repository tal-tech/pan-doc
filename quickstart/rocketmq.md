### rocketmq
-----

本小节主要介绍如何使用pan快速完成rocketmq消息的生产，在此不再对rocketmq做相关的介绍，不太了解rocketmq的可以去[rocketmq官网](https://rocketmq.apache.org/)阅读相关文档。

#### 1、启动NameServer
```shell
sh mqnamesrv
```
#### 2、启动Broker
```shell
sh mqbroker -n localhost:9876 autoCreateTopicEnable=true
```
#### 3、修改pan中rocketmq相关配置
```shell
[RocketmqProxy]
enable=false
producerGroup=test
nameServer=127.0.0.1:9876
producerRetry=2
valid=TopicTest
failMode=retry/save/discard(无限次重试、保存到redis、丢弃)

```
配置文档请点击[这里](config/config.md)

#### 4、编译
```shell
make
```
#### 5、运行
```shell
./bin/pan -c ../conf/conf.ini
```
#### 6、业务代码
业务方往pan中发消息，需要引入rocketmqutil，具体使用方法请看[这里](https://git.100tal.com/wangxiao_go_lib/xesTools/tree/master/rocketmqutil)。