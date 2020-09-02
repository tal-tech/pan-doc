### rabbitmq
-----

本小节主要介绍如何使用pan快速完成rabbitmq消息的生产，在此不再对rabbitmq做相关的介绍，不太了解rabbitmq的可以去[rabbitmq官网](https://www.rabbitmq.com/)阅读相关文档。

#### 1、启动Rabbitmq
```shell
./rabbitmq-server
```
#### 2、修改pan中rabbitmq相关配置
```shell
[RabbitmqProxy]
enable=false
url=amqp://guest:guest@localhost:5672/
valid=test:test log:test//白名单
failMode=retry/save/discard(无限次重试、保存到redis、丢弃)

```
配置文档请点击[这里](config/config.md)

#### 3、编译
```shell
make
```
#### 4、运行
```shell
./bin/pan -c ../conf/conf.ini
```
#### 5、业务代码
业务方往pan中发消息，需要引入rabbitmqutil，具体使用方法请看[这里](https://git.100tal.com/wangxiao_go_lib/xesTools/tree/master/rabbitmqutil)。