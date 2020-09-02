### server
------
#### 职责
* 接收业务消息
* 白名单判断
* 将消息传给给下游pchan

#### 源码实现
源码实现请见[server.go](https://github.com/tal-tech/pan/blob/master/internal/server.go)

#### server结构
```go
type Server struct {
	mqs           []string        //已注册mq类型
	tcp           net.Listener    //tcp监听对象
	unix          net.Listener    //unixSocket监听对象
	path          string          //socket文件地址
	Input         chan<- []byte   //下游pchan中的input管道
	locker        *sync.RWMutex   //锁
	counter       int64           //成功发送消息计数
	failcnt       int64           //失败消息计数
	validTopic    map[string]bool //kafka rocketmq nsa 白名单
	validExchange map[string]bool //rabbitmq 白名单
	exit          chan struct{}   //退出信号
}
```

#### 注意事项
* 通过读取meta中的信息确定消息的类型，见server.go中[第164行](https://git.100tal.com/wangxiao_go_center/pan/blob/master/internal/server.go#L164)
