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
配置文档请点击[这里](../config/config.md)

#### 4、编译
```shell
make
```
#### 5、运行
```shell
./bin/pan -c ../conf/conf.ini
```
#### 6、业务代码
业务方往pan中发消息，需要引入rocketmqutil，具体使用方法如下

#### 使用方法
```go
package main
 
import (
    "fmt"
    "time"
 
    "github.com/tal-tech/xtools/rocketmqutil"
)
 
func main() {
    t := time.Tick(5 * time.Second)
    count := 0
    for {
        select {
        case <-t:
            count++
            s := fmt.Sprintf("rocketmq %d", count)
            err := rocketmqutil.Send2Proxy("TopicTest", "stu_test_0", []byte(s))
            if err != nil {
                fmt.Println(err)
            }
            err = rocketmqutil.Send2Proxy("TopicTest", "stu_test_1", []byte(s))
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
[RocketmqProxy]
unix=/home/www/pan.xesv5.com/pan.sock   //pan的sock文件地址
host=localhost:9999  //mqproxy的ip:port地址
```

#### 注意事项
注意go.mod文件中替换包
```shell
replace github.com/henrylee2cn/teleport v5.0.0+incompatible => github.com/hhtlxhhxy/github.com_henrylee2cn_teleport v1.0.0

或

replace github.com/henrylee2cn/teleport v0.0.0 => github.com/hhtlxhhxy/github.com_henrylee2cn_teleport v1.0.0
```