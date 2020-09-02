### delaymq
-----

本小节主要介绍如何使用pan中的延时队列功能，目前延时队列仅支持kafka。

#### 1、修改pan中kafka和delaymq相关配置
```shell
[KafkaProxy]
enable=true//开关
KafkaWaitAll=true
KafkaCompression=true
KafkaPartitioner=round
KafkaProducerTimeout=10
brokers=localhost:9092
sasl=false
user=
password=
valid= //topic白名单，若为空则所有topic均可发送
fallback=false //消息发送失败是否回传（若回传，一直失败，可能会造成CPU短暂飙升）

[DelayMQProxy]
enable=true //开关
key=delay_queue //redis中key名称
limit=50 //一次性获取数据限制，建议设置为1000以下
```
配置文档请点击[这里](config/config.md)

#### 2、编译
```shell
make
```
#### 3、运行
```shell
./bin/pan -c ../conf/conf.ini
```
#### 4、业务代码
业务方往pan中发送延时消息，需要引入delaymqutil，具体使用方法请看[这里](https://git.100tal.com/wangxiao_go_lib/xesTools/tree/master/delaymqutil)。