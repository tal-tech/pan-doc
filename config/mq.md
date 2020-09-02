### 队列配置
------
本节主要介绍pan的队列配置，主要是消息队列例如kafka、rabbitmq、rocketmq、nsq的相关配置。
```shell
[KafkaProxy]
enable=true
KafkaWaitAll=true
KafkaCompression=true
KafkaPartitioner=round  //可选round、random、hash
KafkaProducerTimeout=10 //单位s
brokers=localhost:9092
sasl=false
user=
password=
valid=
failMode=retry/save/discard(无限次重试、保存到redis、丢弃)

[RabbitmqProxy]
enable=false
url=amqp://guest:guest@localhost:5672/
valid=test:test log:test
failMode=retry/save/discard(无限次重试、保存到redis、丢弃)

[RocketmqProxy]
enable=false
producerGroup=test
nameServer=127.0.0.1:9876
producerRetry=2
valid=TopicTest
failMode=retry/save/discard(无限次重试、保存到redis、丢弃)

[NSQProxy]
enable=false
nsqdAddr=127.0.0.1:4150
valid=test
failMode=retry/save/discard(无限次重试、保存到redis、丢弃)

[DelayMQProxy]
enable=false
key=delay_queue //延时队列key名称
limit=1000 //zrange命令一次取数据最大限制，建议设置为1000
```

* kafka队列配置主要包括broker地址，kafka压缩方式，是否启用kafka等
* rabbitmq配置主要包括是否启用rabbitmq、rabbitmq地址
* rocketmq配置主要包括是否启用rocketmq、nameserver地址等
* nsq配置主要包括是否启用nsq、nsqd地址
* delaymq配置主要包括是否开始延时功能配置