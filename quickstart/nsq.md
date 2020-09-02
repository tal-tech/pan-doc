### nsq
-----

本小节主要介绍如何使用pan快速完成nsq消息的生产，在此不再对nsq做相关的介绍，不了解nsq的可以去[nsq官网](https://nsq.io/)阅读相关文档。

#### 1、启动nsqlookupd
```shell
./bin/nsqlookupd
```
#### 2、启动nsqd
```shell
./bin/nsqd --lookupd-tcp-address=127.0.0.1:4160
```
#### 3、修改pan中nsq相关配置
```shell
[NSQProxy]
enable=false
nsqdAddr=127.0.0.1:4150
valid=test
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
业务方往pan中发消息，需要引入nsqutil，具体使用方法请看[这里](https://git.100tal.com/wangxiao_go_lib/xesTools/tree/master/nsqutil)。