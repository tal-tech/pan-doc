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
配置文档请点击[这里](../config/config.md)

#### 5、编译
```shell
make
```
#### 6、运行
```shell
./bin/pan -c ../conf/conf.ini
```
#### 7、业务代码

业务方往pan中发消息，需要引入kafkautil，具体使用方法如下
#### 使用方法
```go
package main
 
import (
    "fmt"
    "time"
 
    "github.com/tal-tech/xtools/kafkautil"

    "github.com/spf13/cast"
)
 
func main() {
    t := time.Tick(5 * time.Second)
    count := 0
    for {
        select {
        case <-t:
            count++
            err := kafkautil.Send2Proxy("test", []byte("kafka "+cast.ToString(count)))
            if err != nil {
                fmt.Println(err)
            }
            continue
        }
    }
}
```
#### 使用配置
```shell
[KafkaProxy]
unix=/home/www/pan.xesv5.com/pan.sock   //pan的sock文件地址
host=localhost:9999  //pan的ip:port地址
```

#### 注意事项
注意go.mod文件中替换包
```shell
replace github.com/henrylee2cn/teleport v5.0.0+incompatible => github.com/hhtlxhhxy/github.com_henrylee2cn_teleport v1.0.0

或

replace github.com/henrylee2cn/teleport v0.0.0 => github.com/hhtlxhhxy/github.com_henrylee2cn_teleport v1.0.0
```