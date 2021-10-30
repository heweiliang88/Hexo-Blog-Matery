---
title: Nginx
categories:
- 运维
tags:
- 服务器
- Nginx
abbrlink: 54876
---

# Nginx

> - 书籍
> 	- 
> - 视频
> 	- 
> - 教程
> 	- [前端工程师不可不知的Nginx知识](https://juejin.cn/post/6864085814571335694)
> 	- [前端必备 Nginx 配置](https://juejin.cn/post/6844903942262882318)
> 	- [前端必会的 Nginx入门视频教程(共11集)](https://juejin.cn/post/6844903701459501070)

## 基础知识

Nginx是一款轻量级高性能的HTTP和反向代理服务器，，同时也是一个通用 代理服务器 （TCP/UDP/IMAP/POP3/SMTP），采用事件驱动的异步非阻塞处理方式框架，这让其具有极好的IO性能，时常用于服务端的反向代理和负载均衡。

- Nginx更擅长于底层服务器端资源的处理（静态资源处理转发、反向代理，负载均衡等）
- Node.js更擅长于上层具体业务逻辑的处理。两者可以实现完美组合，助力前端开发。

使用场景

- 静态资源服务，通过本地文件系统提供服务
- 反向代理服务、负载均衡
- API服务、权限控制，减少应用服务器压力

安装

```bash
yum install nginx -y
```

基本命令

```bash
nginx -t   检查配置文件是否有语法错误
nginx -s reload   
nginx -s start // nginx
// 停止ngix
nginx -s stop
nginx -s quit  从容停止服务
systemctl start/stop/reload/ nginx.service
// 查看端口号
netstat -tlnp 
```

目录结构

```
rpm -ql nginx
/etc/nginx/nginx.conf 核心配置文件
/etc/nginx/conf.d/default.conf 默认http服务器配置文件
/etc/nginx/fastcgi_params fastcgi配置
/etc/nginx/scgi_params scgi配置
/etc/nginx/uwsgi_params uwsgi配置
/etc/nginx/koi-utf
/etc/nginx/koi-win
/etc/nginx/win-utf 这三个文件是编码映射文件，因为作者是俄国人
/etc/nginx/mime.types 设置HTTP协议的Content-Type与扩展名对应关系的文件
/usr/lib/systemd/system/nginx-debug.service
/usr/lib/systemd/system/nginx.service
/etc/sysconfig/nginx
/etc/sysconfig/nginx-debug 这四个文件是用来配置守护进程管理的
/etc/nginx/modules 基本共享库和内核模块
/usr/share/doc/nginx-1.18.0 帮助文档
/usr/share/doc/nginx-1.18.0/COPYRIGHT 版权声明
/usr/share/man/man8/nginx.8.gz 手册
/var/cache/nginx Nginx的缓存目录
/var/log/nginx Nginx的日志目录
/usr/sbin/nginx 可执行命令
/usr/sbin/nginx-debug 调试执行可执行命令
```

配置文件

```bash
cp /etc/nginx/nginx.conf /etc/nginx/nginx.bak
/etc/nginx/nginx.conf 核心配置文件
```

## 基本配置



## 正向代理

正向代理的对象是客户端，服务器端看不到真正的客户端  Nginx服务器是客户端，转发给服务器端

```conf
resolver 8.8.8.8 # 谷歌的域名解析地址server
{ 
    location / {      
        # 当客户端请求我的时候，我会把请求转发给它      
        # $http_host 要访问的主机名 $request_uri 请求路径      
    	proxy_pass http://$http_host$request_uri; 
    }
}
```

## 反向代理

反向代理的对象是服务端，客户端看不到真正的服务端 Nginx服务器是服务端，转发给服务器端

```bash

```

## 跨域

nginx 部署多个不同项目的端口

```conf
// /etc/nginx
server{
	listen 80;
	server_name panda.cdemo.com;
	location /static{
		alias /home/edwin/djangoPros/panda/static;
	}
	location /{
		include uwsgi_params;
		uwsgi_pass 127.0.0.1:8000
		#proxy_pass http://127.0.0.1:8000
	} 
}

server{
	listen 80;
	server_name www.cdemo.com;

	location /{
		include uwsgi_params;
		uwsgi_pass 127.0.0.1:9000
		#proxy_pass http://127.0.0.1:8900
	} 
}
```

nginx 配置跨域和指定端口部署

```js
// 设置需要跨域指定文件
location ^~/res/ {
    add_header Access-Control-Allow-Origin *;
    add_header Access-Control-Allow-Methods 'GET,POST';
    add_header Access-Control-Allow-Headers 'DNT,X-Mx-ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization';
    alias /data/web/res/;
}
// 设置允许全局跨域
server {
　　 ....
    add_header Access-Control-Allow-Origin *;
    add_header Access-Control-Allow-Methods 'GET,POST';
    add_header Access-Control-Allow-Headers 'DNT,X-Mx-ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization';  
}

// 设置跨域
server{
    listen 80;
    server_name localhost;  # 用户访问 localhost，反向代理到 http://baidu.com
    location / {
        proxy_pass http://baidu.com.com
    }
}
```

## Gzip

Gzip 是互联网上非常普遍的一种数据压缩格式，对于纯文本来说可以压缩到原大小的 40%，可以节省大量的带宽。不过需要注意的是，启用 Gzip 所需的 HTTP 最低版本是 1.1。





## 根据文件类型设置过期时间





## 请求限制





## 访问控制





## ab命令



## 防盗链

防止文件被其他网站调用

```
location ~* \.(gif|jpg|png)${
	# 192.168.0.1
	valid_refers none
}
```





## 禁止文件缓存







## 负载均衡

解决高并发、海量数据问题，就需要使用负载均衡来调度服务器。将请求合理的分发到应用服务器集群中的一台台服务器上。

```
# upstream 指定后端服务器地址
# weight 设置权重
# server 中会将 http://webcanteen 的请求转发到 upstream 池中
upstream webcanteen{
	server 
}
server {
 	location / {
 	 	proxy_pass http://www.baidu.com
 	}
}
```

## 使用域名设置虚拟主机





