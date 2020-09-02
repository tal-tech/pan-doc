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
配置文档请点击[这里](../config/config.md)

#### 3、编译
```shell
make
```
#### 4、运行
```shell
./bin/pan -c ../conf/conf.ini
```
#### 5、业务代码
业务方往pan中发消息，需要引入rabbitmqutil，具体使用方法如下

#### 使用方法
```go
package main
 
import (
    "fmt"
    "time"
 
    "github.com/tal-tech/xtools/rabbitmqutil"
)

func main() {
    t := time.Tick(5 * time.Second)
    count := 0
    for {
        select {
        case <-t:
            count++
            s := fmt.Sprintf("rabbitmq %d", count)
            err := rabbitmqutil.Send2Proxy("test", "test", []byte(s))
            if err != nil {
                fmt.Println(err)
            }
            err = rabbitmqutil.Send2Proxy("test", "test1", []byte(s))
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
[RabbitmqProxy]
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