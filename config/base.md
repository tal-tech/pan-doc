### 基础配置
------
本节主要介绍pan的基础配置，主要是监控、日志等。
```shell
[Pprof]
enable=false
port=9112

[PerfProxy]
host=127.0.0.1:13333
level=I
timedebug=false

[Pan]
stype=file//持久化方式，可选：file、redis、leveldb
tcpPort=9999
unixSocket=/home/www/pan.xesv5.com/pan.sock//通信方式为本地unixSocket,sock文件地址
path=/home/www/pan.xesv5.com/panqueue
grayMode=false//是否开启灰度模式，当前仅支持kafka，开启后，默认发送topic后加"_gray"
grayAddrs=10.0.0.1//灰度机ip地址
bufferLimit=2000//内存缓冲区大小
levelDB=/home/www/pan.xesv5.com/level

[Redis]
redis=127.0.0.1:6379//若持久化方式为redis，持久化的redis集群地址
delayRedis=127.0.0.1:6379//若开启了延时队列，数据保存的redis集群地址
fallbackRedis=127.0.0.1:6379

```

* Pprof是golang进程堆栈监控
* PerfProxy是采集打点数据
* Pan中是持久化方式和通信方式的配置
* Redis是依赖的一些redis配置