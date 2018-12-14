# CQBot-swoole


[![作者QQ](https://img.shields.io/badge/作者QQ-627577391-orange.svg)]()
[![license](https://img.shields.io/badge/license-MIT-blue.svg)]()


A fast and multi-task framework for Coolq-HTTP-API

一个异步、多进程的[CQ-HTTP-API插件](https://cqhttp.cc/)框架 made by php-swoole

## 什么是Swoole
Swoole是一个C编写的、高性能的PHP扩展。支持多线程、多进程、同步、异步、协程、SQL等。

众所周知，PHP原生对多线程、多进程、异步等特性支持不是很好，但有了Swoole，你可以非常简单自由地写出优雅的高性能服务器。

框架使用Swoole Websocket Server为基础，借助PHP语言便捷的优势，易于上手。

本项目原生支持多机器人连接，故选择了反向Websocket连接方式。同时更适用于高并发、多机器人同时连接以及对接**微信公众号**和**web前端**等场景。

[Swoole官网](https://www.swoole.com/)


## CQBot-swoole 文档
本项目的文档正在努力编写中：[https://cqbot.crazywhale.org/](https://cqbot.crazywhale.org/)


## 框架简介
本机器人框架是基于PHP Swoole框架而写的一个CQ-HTTP-API SDK，具有高性能、高并发和多机器人连接的特性。框架本身常驻内存的特性解决了读写文件、读写数据库等造成的性能问题。

框架自身作为一个高性能的Swoole **WebSocket**兼容HTTP服务器，可以同时完成更多websocket和HTTP环境的业务逻辑。此外还保留了微信公众号接口，未来可以与微信公众号开发者平台对接。


## 环境部署
由于框架是独立于酷Q和HTTPAPI插件运行的，故你可以在多台主机上部署酷Q的docker。

如果你是新用户或重新安装含有HTTPAPI插件的**酷Q-Docker**的话，可以在你需要部署酷Q的Linux主机下使用下面的脚本快速构建酷Q环境，此脚本会引导进行相关的cqhttp插件设置。每台部署酷Q的主机均可直接使用此条命令（服务器需要提前安装Docker）

```shell
curl -O https://raw.githubusercontent.com/crazywhalecc/CQBot-swoole/master/start-coolq.sh
chmod +x start-coolq.sh
./start-coolq.sh
```



## 框架部署
### 手动安装到Linux主机上
``` shell
# 安装PHP
apt-get update
apt-get install php7.2 php7.2-dev php7.2 php7.2-mbstring php7.2-json php7.2 php-pear

# 安装Swoole
pecl install swoole
echo 'extension=swoole.so' >> /etc/php/7.2/cli/php.ini

# 部署框架
git clone https://github.com/crazywhalecc/CQBot-swoole.git
cd CQBot-swoole/


# 以上指令可能需要sudo执行
```


### 使用Docker快速构建
``` shell
docker pull jesse2061/cqbot-swoole
mkdir cqbot && cd cqbot
curl -O https://raw.githubusercontent.com/crazywhalecc/CQBot-swoole/master/start-docker.sh
chmod +x start-docker.sh
```


## 启动
#### 直接安装后启动框架（第一次会有初始化设置）

```shell
cd CQBot-swoole/
php start.php
```

#### 在screen中运行框架

```shell
cd CQBot-swoole/
chmod +x start-screen.sh
./start-screen.sh
```

#### 使用Docker构建下启动框架

```shell
sudo docker run -it --rm --name cqbot -v $(pwd)/cqbot/:/root/ jesse2061/cqbot-swoole

# 进入docker后输入
php start.php
```

#### 使用Docker在screen中运行框架

```shell
curl -O https://raw.githubusercontent.com/crazywhalecc/CQBot-swoole/master/start-docker-screen.sh
chmod +x start-docker-screen.sh
./start-docker-screen.sh
```

## 关于

框架和SDK部分代码直接从`炸毛机器人`中移植而来，炸毛机器人（2230833894）是作者写的一个高性能的机器人，曾获全国计算机设计大赛一等奖。

欢迎随时在HTTP-API插件群提问，当然更好的话可以加作者QQ（627577391）或提交issue进行疑难解答。