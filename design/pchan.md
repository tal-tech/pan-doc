### pchan
------
#### 职责
* 接上游server消息
* 将消息转发给下游proxy
* 维持一个mmap，消息传递发生阻塞时，负责将消息落盘，避免消息丢失

#### 源码实现
源码实现请见[pchan.go](https://github.com/tal-tech/pan/blob/master/internal/pchan.go)

#### 结构
```go
type PChan struct {
	exit       chan struct{} //退出信号
	needStore  bool          //是否需要落盘
	storeMutex *sync.Mutex   //锁
	waiter     *sync.WaitGroup
	queue      *fqueue.FQueue //利用fqueue实现的mmap，大小4G
	limit      int            //阈值
	input      chan []byte    //input管道，有缓冲型，大小 limit*1.5
	output     chan []byte    //output管道，有缓冲型l,大小 limit*1.5

	Input  chan<- []byte //外部使用的input,主要是给server使用，还有proxy失败回传
	Output <-chan []byte //外部使用的output，主要是给proxy使用，proxy从中读取消息
}
```

#### 注意事项
* pchan中不对消息的内容做任何处理，只负责向下游传递
* pchan的主要功能就是防止因为下游消息生产阻塞，造成上游业务阻塞
