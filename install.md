### 安装升级
------

#### 环境检查
* 当前golang项目统一使用 [go mod](http://go.xesv5.com/publish/#/dependcy) 作为依赖管理，请先按文档安装或对照相应版本
* 调试项目请在linux系统中编译打包，windows不保证可正常运行

#### 安装脚手架
通过 [rigger](https://wiki.zhiyinlou.com/pages/viewpage.action?pageId=34029786#id-%E5%91%BD%E4%BB%A4%E5%8F%8A%E5%8A%9F%E8%83%BD-new)(git地址git.100tal.com/wangxiao_go_center/rigger)脚手架可一键创建xesGo模板的api项目

#### 生成框架

此处以"myproject"为项目名称
```shell
$ rigger new api myproject
正克隆到 '/winshare/go/src/myproject'...
myprojec项目已创建完成, 使用:
 cd /winshare/go/src/myproject && rigger build 
开始你的微服务之旅！

```