# docker
https://blog.csdn.net/zzq060143/article/details/91050272

解决开发和部署环境不同造成代码运行失败的问题
部署时将开发时的环境和配置一同搬运到服务端
提交镜像
基于GO语言  云开源 一次封装处处运行
仓库 镜像 容器



## 指令

```bat
docker --version    # docker的版本
docker ps       #检查容器的详细信息
docker version   #客户端和服务端版本
docker info  # 查看插件、硬件等属性
docker run hello-world   # 以测试从Docker Hub中拉取图像并启动容器
docker run -it ubuntu bash         # 运行一个Ubuntu容器
docker rm -f webserver   # 这将删除容器
docker images 

docker run -it -v /e/dockerWorkspace:/home dockerhub.nie.netease.com/hztantive4/debian-protobot /bin/bash
```



docker run -it -v /home/hjhn2155/workspace:/home dockerhub.nie.netease.com/hztantive4/debian-protobot /bin/bash


docker run -it -v [宿主机目录绝对路径]:[镜像内挂载的路径] ubuntu64 /bin/bash

docker run -it -v E:\dockerWorkspace:/home dockerhub.nie.netease.com/hztantive4/debian-protobot:latest /bin/bash


### 其他
Nginx (engine x) 是一个高性能的HTTP和反向代理web服务器，同时也提供了IMAP/POP3/SMTP服务。Nginx是由伊戈尔·赛索耶夫为俄罗斯访问量第二的Rambler.ru站点（俄文：Рамблер）开发的，第一个公开版本0.1.0发布于2004年10月4日。
其将源代码以类BSD许可证的形式发布，因它的稳定性、丰富的功能集、示例配置文件和低系统资源的消耗而闻名。2011年6月1日，nginx 1.0.4发布。
Nginx是一款轻量级的Web 服务器/反向代理服务器及电子邮件（IMAP/POP3）代理服务器，在BSD-like 协议下发行。其特点是占有内存少，并发能力强，事实上nginx的并发能力在同类型的网页服务器中表现较好，中国大陆使用nginx网站用户有：百度、京东、新浪、网易、腾讯、淘宝等。

