## Publish

* tag(version control)
  * release-it
* rollback

server:

1. connect server by `github` action
2. get latest code by tag
3. start project

rollback:

1. rerun previous tag correspond ci job
2. execute current tag code
3. start project

### Monitor and Alarm

* 主动防御：如 XSS预防
* 心跳检测：每隔一定时间调用一下接口，看会不会报错
* Alarm: occur error need send email first time
* [alinode](https://www.aliyun.com/product/nodejs) 服务器监控: 实时检测CPU 内存 硬盘的健康状态
