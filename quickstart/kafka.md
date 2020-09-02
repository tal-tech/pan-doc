### kafka
-----

本小节主要介绍如何使用pan快速完成kafka消息的生产，在此不再对kafka做相关的介绍，不太了解kafka的可以去[kafka官网](https://kafka.apache.org/)阅读相关文档。

#### 1、启动zookeeper
```shell
./bin/zookeeper-server-start /usr/local/etc/kafka/zookeeper.properties
```
#### 2、启动kafka
```shell
./bin/kafka-server-start /usr/local/etc/kafka/server.properties
```
#### 3、创建topic
```shell
./bin/kafka-topics  --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test
```
#### 4、修改pan中kafka相关配置
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
failMode=retry/save/discard(无限次重试、保存到redis、丢弃)

```
配置文档请点击[这里](config/config.md)

#### 5、编译
```shell
make
```
#### 6、运行
```shell
./bin/pan -c ../conf/conf.ini
```
#### 7、业务代码
业务方往pan中发消息，需要引入kafkautil，具体使用方法请看[这里](https://git.100tal.com/wangxiao_go_lib/xesTools/tree/master/kafkautil)。