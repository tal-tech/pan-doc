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
window=5 //延时容错s
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
业务方往pan中发送延时消息，需要引入delaymqutil，具体使用方法如下
#### 使用方法
```go
package main

import (
	"fmt"
	"time"

	"github.com/tal-tech/xtools/delaymqutil"

	"github.com/spf13/cast"
)

func main() {
	t := time.Tick(3 * time.Second)
	count := 0
	for {
		select {
		case <-t:
			count++
			now := time.Now().Format("2006-01-02 15:04:05")
			sendTimestamp := time.Now().Unix() + 10
			err := delaymqutil.Send2Proxy("kafka", "test", "", []byte("kafka "+cast.ToString(count)+" "+now), sendTimestamp)
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
[DelayMQProxy]
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


