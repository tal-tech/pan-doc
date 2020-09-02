### 生产部署
--------
pan生产环境部署分为两步

#### 机器预装
pan已支持rpm安装，在生产环境下的安装运维统一处理，请联系运维处理，如遇到问题，可联系我们。

##### 执行命令
```
yum install pan
```

##### 安装验证
安装成功后，请验证，pan可执行文件被放在/usr/bin目录下


#### 发布
各业务使用方，使用pan的配置不相同，故发布阶段完成配置发布，服务启动工作

发布系统发布任务，参考[部署](http://go.xesv5.com/publish/#/deploy)

##### 配置
具体配置需单独创建git项目，克隆自[panConfig](https://git.100tal.com/wangxiao_go_center/panconfig)

需修改conf\_release.ini、conf\_sjhl.ini等配置

pan.ini配置需要替换pan.conf.com为发布系统中发布项目域名

##### 发布
发布系统中创建项目，关联配置git

配置发布后执行command为:

```
//pan.conf.com同样替换为发布系统中发布项目域名
sh /home/www/pan.conf.com/deploy.sh pan.conf.com pan 1
```

配置完成可进行发布

##### 验证
可通过supervisorctl status或查看pan进程是否启动验证

