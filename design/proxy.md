### proxy
------
#### 职责
* 接收上游pchan中output管道中的消息
* 将不同的消息种类发送到对应的消息队列对象实体
* 管理消息队列实体的对象初始化

#### 源码实现
源码实现请见[mq.go](https://git.100tal.com/wangxiao_go_center/pan/blob/master/mq/mq.go)

#### 结构
```go
type ProxyManager struct {
	pchan  *internal.PChan
	server *internal.Server

	input    <-chan []byte
	fallback chan<- []byte

	mqMap map[string]MQ
	quits []chan struct{}
}
```

* pchan和server分别是pchan和server对象
* input和fallback分别是pchan的OutPut和Input管道
* mqMap是消息队列对象映射表
* quits退出信号

#### 如何实现一个新的消息队列类型？
* 实现MQ接口
```go
type MQ interface {
	Input() chan<- []byte
	Close()
}
```
* 实现Register和Init方法，见[kafka.go](https://git.100tal.com/wangxiao_go_center/pan/blob/master/mq/kafka/kafka.go#L37)
* 添加Register到main，见[main.go](https://git.100tal.com/wangxiao_go_center/pan/blob/master/main.go#L35)
