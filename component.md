# 组件功能介绍

框架内除框架主体部分外，扩展功能都拆分成可独立运行的组件，可以通过项目根目录下composer require直接安装。

```php
composer require php/fend-plugin-db
```

## 可选组件列表
| 插件| 介绍 |
| :--------------------- | :--------- |
|[php/fend-dev-docker](https://git.100tal.com/php/fend-dev-docker)| 开发时使用的本地镜像，方便环境统一 |
|[php/fend-demo](https://git.100tal.com/php/fend-demo) | Composer拆分版本演示项目，可以按需拷贝项目内内容|
|[php/fend-test](https://git.100tal.com/php/fend-test) | 框架整体单元测试，框架所有组件及功能的单元测试 |
|[php/fend-core](https://git.100tal.com/php/fend-core) | 框架内核，内含所有组件都会使用的功能，如：依赖注入，异常，日志 |
|[php/fend-plugin-alarm](https://git.100tal.com/php/fend-plugin-alarm)| 错误警报服务，服务会自动将重复日志进行聚合，统一发送钉钉、邮件预警|
|[php/fend-plugin-cache](https://git.100tal.com/php/fend-plugin-cache)| Fend所有cache统一工厂类，对Redis、Memcache驱动对象进行统一管理 |
|[php/fend-plugin-redis](https://git.100tal.com/php/fend-plugin-redis)| Redis驱动组件，需要配合cache组件|
|[php/fend-plugin-memcache](https://git.100tal.com/php/fend-plugin-memcache)| Memcached驱动封装，需要配合cache组件使用|
|[php/fend-plugin-console](https://git.100tal.com/php/fend-plugin-console)| Symfony Console封装，能够对所有cli命令进行统一封装管理，方便用户自定义命令|
|[php/fend-plugin-db](https://git.100tal.com/php/fend-plugin-db)| Fend所有数据库统一工厂类，对Mysqli及PDO驱动进行统一管理|
|[php/fend-plugin-mysqli](https://git.100tal.com/php/fend-plugin-mysqli)| Mysqli驱动，配合DB组件使用|
|[php/fend-plugin-pdo](https://git.100tal.com/php/fend-plugin-pdo)| PDO驱动，配合DB组件使用|
|[php/fend-plugin-router](https://git.100tal.com/php/fend-plugin-router)| Fend请求路由组件，统一提供路由配置及不同路由组件拼合|
|[php/fend-plugin-fastrouter](https://git.100tal.com/php/fend-plugin-fastrouter)| 如果有个性网址路由需要，可以引入此组件，需要配合router组件使用，会降低性能|
|[php/fend-plugin-server](https://git.100tal.com/php/fend-plugin-server)| Swoole Http服务组件，Fend用户可以直接平滑切换使用此服务，对外提供高性能API服务|
|[php/fend-plugin-validator](https://git.100tal.com/php/fend-plugin-validator)| 输入验证组件，提供对数据的简单验证和过滤|
|[php/fend-plugin-kafka](https://git.100tal.com/php/fend-plugin-kafka)| kafka网关组件，可以拉取推送消息到kafka网关|
|[php/fend-plugin-template](https://git.100tal.com/php/fend-plugin-template)| smarty 模板组件|
|[php/fend-plugin-errorcode](https://git.100tal.com/php/fend-plugin-errorcode)| 统一异常错误码管理，用于错误码及错误信息统一管理配置|
|[php/fend-plugin-redismodel](https://git.100tal.com/php/fend-plugin-redismodel)| Redis key model ，对于散乱的Redis Key进行统一管理封装|
|[php/fend-plugin-elasticsearch](https://git.100tal.com/php/fend-plugin-elasticsearch)| ElasticSearch 调用封装，支持数据索引创建更改，并提供较复杂的查询统计封装|
|[php/fend-plugin-xhprof](https://git.100tal.com/php/fend-plugin-xhprof)| Xhprof组件，用于查看xhprof插件输出的性能分析文件|

## 组件版本
1.2.x 为LTS版本，会持续维护更新，内含FPM及Swoole 阻塞版本
1.3.x 也为LTS版本，会持续维护更新，内含FPM及Swoole 阻塞版本及 swoole协程版本