# redis笔记
数据结构型服务器：字符串/哈希/列表/集合/有序集合
[Redis 官网](https://redis.io/)

[Redis 在线测试](http://try.redis.io/)

[Redis 命令参考](http://doc.redisfans.com/)


## pika
pika是360奇虎公司开源的一款类redis存储系统，主要解决的是用户使用 Redis 的内存大小超过 50G、80G 等等这样的情况，会遇到启动恢复时间长，一主多从代价大，硬件成本贵，缓冲区容易写满等问题。

Pika 就是针对这些场景的一个解决方案：

Pika 的单线程的性能肯定不如 Redis，Pika 是多线程的结构，因此在线程数比较多的情况下，某些数据结构的性能可以优于 Redis；
Pika 肯定不是完全优于 Redis 的方案，只是在某些场景下面更适合，DBA 可以根据业务的场景挑选合适的方案。
 