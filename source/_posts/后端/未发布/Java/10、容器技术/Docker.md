---
abbrlink: 36863
---
# Docker教程

教程

[Docker 教程 | 菜鸟教程](https://www.runoob.com/docker/docker-tutorial.html)

[(这可能是最为详细的Docker入门吐血总结](https://blog.csdn.net/deng624796905/article/details/86493330)

官网

[docker中文社区,docker帮助,docker手册,docker教程,docker安装手册 - docker中文社区](https://www.docker.org.cn/)

[Empowering App Development for Developers | Docker](https://www.docker.com/)

## Docker概念

Docker 是一个`开源的应用容器引擎`，基于 [Go 语言](https://www.runoob.com/go/go-tutorial.html) 并遵从 Apache2.0 协议开源。

Docker 可以`让开发者打包他们的应用以及依赖包到一个轻量级、可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化`。

容器是完全使用沙箱机制，相互之间不会有任何接口（类似 iPhone 的 app）,更重要的是容器性能开销极低。

Docker 从 17.03 版本之后分为，我们用社区版就可以了。

-  CE（Community Edition: 社区版）
-  EE（Enterprise Edition: 企业版）





## Docker 安装



### Ubuntu Docker 安装



### Debian Docker 安装



### CentOS  Docker 安装



### Windows10  Docker 安装

#### 开启 `Hyper -V`

控制面板\程序\程序和功能\==> 启动或关闭Windows 功能

#### 安装 Toolbox

https://hub.docker.com/?overlay=onboarding

#### 镜像加速

统右下角托盘 Docker 图标内右键菜单选择 Settings，打开配置窗口后左侧导航菜单选择 Docker Engine。在 Registrymirrors 一栏中填写加速器地址 **https://registry.docker-cn.com** ，之后点击 Apply 保存后 Docker 就会重启并应用配置的镜像地址了。

```
{
  "registry-mirrors": [],
  "insecure-registries": [],
  "debug": true,
  "experimental": false
}
```

### Docker 镜像加速

国内从 DockerHub 拉取镜像有时会遇到困难，此时可以配置镜像加速器。Docker 官方和国内很多云服务商都提供了国内加速器服务，例如：

- 网易：**https://hub-mirror.c.163.com/**
- 阿里云：**https://<你的ID>.mirror.aliyuncs.com**
- 七牛云加速器：**https://reg-mirror.qiniu.com**

**创建或修改 /etc/docker/daemon.json 文件，修改为如下形式**

```
{
  "registry-mirrors": [
    "https://registry.docker-cn.com",
    "http://hub-mirror.c.163.com",
    "https://docker.mirrors.ustc.edu.cn"
  ]
}
```

Windows 10

对于使用 Windows 10 的系统，在系统右下角托盘 Docker 图标内右键菜单选择 Settings，打开配置窗口后左侧导航菜单选择 Daemon。在 Registrymirrors 一栏中填写加速器地址 **https://registry.docker-cn.com** ，之后点击 Apply 保存后 Docker 就会重启并应用配置的镜像地址了。

**加载重启docker**

```
$ sudo systemctl daemon-reload
$ sudo systemctl restart docker
```

当配置某一个加速器地址之后，若发现拉取不到镜像，请切换到另一个加速器地址。国内各大云服务商均提供了 Docker 镜像加速服务，建议根据运行 Docker 的云平台选择对应的镜像加速服务。

阿里云镜像获取地址：https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors，登陆后，左侧菜单选中镜像加速器就可以看到你的专属地址了：

### 检查加速器是否生效

检查加速器是否生效配置加速器之后，如果拉取镜像仍然十分缓慢，请手动检查加速器配置是否生效，在命令行执行 **docker info**，如果从结果中看到了如下内容，说明配置成功。

```
$ docker info
Registry Mirrors:
    https://reg-mirror.qiniu.com
```



### Linux 云服务器







## Docker 使用

### 容器使用

查看到 Docker 客户端的所有命令选项

```bash
docker
```

通过命令 **docker command --help** 更深入的了解指定的 Docker 命令使用方法。

```
docker stats --help
```

获取镜像

```
docker pull nginx
```

启动容器





镜像使用



### 容器连接



### 仓库管理

仓库（Repository）是集中存放镜像的地方。以下介绍一下 [Docker Hub](https://hub.docker.com/)。当然不止 docker hub，只是远程的服务商不一样，操作都是一样的。





Dockerfile



Componse



Machine



集群管理





## Docker 实例

### 默认安装步骤

0、搜索要安装软件的版本

[Explore - Docker Hub](https://hub.docker.com/search?q=&type=image)

1、查看可用的软件版本

```bash
docker search 软件名称
```

2、取得新版的node镜像

```bash
docker pull 软件名称:latest //最新版本
docker pull 软件名称其他版本
```

3、查看本地镜像

```
docker images
```

4、运行容器

```bash
docker run -itd --name mysql-test  mysql
--name mysql-test：容器名称。
```

5、查看安装是否成功

```bash
docker ps
```

`CTRL + D 退出`







### 安装Ubuntu

Ubuntu 是基于 Debian 的 Linux 操作系统。

安装新版的ubuntu镜像

```bash
docker pull ubuntu:latest
```

运行容器

```bash
docker run -itd --name ubuntu-test ubuntu
//docker run -itd --name 
```





### 安装Centos 

CentOS（Community Enterprise Operating System）是 Linux 发行版之一，它是来自于 Red Hat Enterprise Linux(RHEL) 依照开放源代码规定发布的源代码所编译而成。由于出自同样的源代码，因此有些要求高度稳定性的服务器以 CentOS 替代商业版的 Red Hat Enterprise Linux 使用。

Ubuntu 是基于 Debian 的 Linux 操作系统。

安装新版的ubuntu镜像

```bash
docker pull centos:latest
docker pull centos:centos7
```

运行容器

```bash
docker run -itd --name centos-test centos:centos7
//docker run -itd --name  软件-test 软件
```



### 安装Nginx

Nginx 是一个高性能的 HTTP 和反向代理 web 服务器，同时也提供了 IMAP/POP3/SMTP 服务 。

安装新版的nginx镜像

```bash
docker pull nginx:latest
```

运行容器

```bash
docker run --name nginx-test -p 8080:80 -d nginx
--name nginx-test：容器名称。
-p 8080:80： 端口进行映射，将本地 8080 端口映射到容器内部的 80 端口。
-d nginx： 设置容器在在后台一直运行。
```

访问 本机IP:8080 



### 安装Node.js

Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境，是一个让 JavaScript 运行在服务端的开发平台。

取得新版的node镜像

```bash
docker pull node:latest
```

运行容器

```bash
docker run -itd -name node-test node
// --name node-test 容器名称
```

安装成功

```
docker exec -it node-test /bin/bash
node -v
```

`CTRL + D 退出`

### 安装PHP

方法一、docker pull php

这里我们拉取官方的镜像,标签为5.6-fpm

```
runoob@runoob:~/php-fpm$ docker pull php:5.6-fpm
```

等待下载完成后，我们就可以在本地镜像列表里查到REPOSITORY为php,标签为5.6-fpm的镜像。

```
runoob@runoob:~/php-fpm$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
php                 5.6-fpm             025041cd3aa5        6 days ago          456.3 MB
```



### 安装MySQL

MySQL 是世界上最受欢迎的开源数据库。凭借其可靠性、易用性和性能，MySQL 已成为 Web 应用程序的数据库优先选择。

取得新版的mysql镜像

```bash
docker pull mysql:latest
```

运行容器

```bash
docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql
-p 3306:3306 ：映射容器服务的 3306 端口到宿主机的 3306 端口，外部主机可以直接通过 宿主机ip:3306 访问到 MySQL 的服务。
MYSQL_ROOT_PASSWORD=123456：设置 MySQL 服务 root 用户的密码
```

安装成功

```bash
docker ps
mysql -h localhost -u root -p
```

`CTRL + D 退出`



### 安装Tomact

方法一  docker pull tomcat

```
docker pull tomcat:latest
docker search tomcat
等待下载完成后，我们就可以在本地镜像列表里查到 REPOSITORY 为 tomcat 的镜像。
docker images|grep tomcat
```

方法二 通过Dockerfile 创建

使用tomcat 镜像

```
runoob@runoob:~/tomcat$ docker run --name tomcat -p 8080:8080 -v $PWD/test:/usr/local/tomcat/webapps/test -d tomcat  
acb33fcb4beb8d7f1ebace6f50f5fc204b1dbe9d524881267aa715c61cf75320
runoob@runoob:~/tomcat$
-p 8080:8080：将容器的 8080 端口映射到主机的 8080 端口。

-v $PWD/test:/usr/local/tomcat/webapps/test：将主机中当前目录下的 test 挂载到容器的 /test。

查看容器启动情况
```

```
docker ps
```



### 安装Python

方法一、docker pull python:3.5

```
docker pull python:3.5
```

方法二、通过 Dockerfile 构建

使用 python 镜像

在 ~/python/myapp 目录下创建一个 helloworld.py 文件，代码如下：

```
#!/usr/bin/python

print("Hello, World!");
```

运行容器

```
runoob@runoob:~/python$ docker run  -v $PWD/myapp:/usr/src/myapp  -w /usr/src/myapp python:3.5 python helloworld.py
```

命令说明：

**-v $PWD/myapp:/usr/src/myapp:** 将主机中当前目录下的 myapp 挂载到容器的 /usr/src/myapp。

**-w /usr/src/myapp:** 指定容器的 /usr/src/myapp 目录为工作目录。

**python helloworld.py:** 使用容器的 python 命令来执行工作目录中的 helloworld.py 文件。

输出结果：

```
Hello, World!
```



### 安装Redis

1、查看可用的Node版本

```bash
docker search redis 
```

2、取得新版的node镜像

```bash
docker pull mysql:latest
```

3、查看本地镜像

```
docker images
```

4、运行容器

```bash
docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql
-p 3306:3306 ：映射容器服务的 3306 端口到宿主机的 3306 端口，外部主机可以直接通过 宿主机ip:3306 访问到 MySQL 的服务。
MYSQL_ROOT_PASSWORD=123456：设置 MySQL 服务 root 用户的密码
```

5、安装成功

```bash
docker ps
mysql -h localhost -u root -p
```

`CTRL + D 退出`



### 安装MongoDB

MongoDB 是一个免费的开源跨平台面向文档的 NoSQL 数据库程序。

1、查看可用的Node版本

```bash
docker search mongo
```

2、取得新版的node镜像

```bash
docker pull mongo:latest
```

3、查看本地镜像

```
docker images
```

4、运行容器

```bash
docker run -itd --name mongo -p 27017:27017 mongo --auth
-p 27017:27017 ：映射容器服务的 27017 端口到宿主机的 27017 端口。外部可以直接通过 宿主机 ip:27017 访问到 mongo 的服务。
--auth：需要密码才能访问容器服务。
```

5、安装成功

```bash
$ docker exec -it mongo mongo admin
# 创建一个名为 admin，密码为 123456 的用户。
>  db.createUser({ user:'admin',pwd:'123456',roles:[ { role:'userAdminAnyDatabase', db: 'admin'}]});
# 尝试使用上面创建的用户信息进行连接。
> db.auth('admin', '123456')
```

`CTRL + D 退出`



### 安装Apache

方法一 docker pull httpd

拉取官方的镜像

```
docker pull httpd
```

等待下载完成后，我们就可以在本地镜像列表里查到REPOSITORY为httpd的镜像

```
docker images httpd
```

方法二 通过 Docker File 创建

使用apache 镜像

运行容器

```
docker run -p 80:80 -v $PWD/www/:/usr/local/apache2/htdocs/ -v $PWD/conf/httpd.conf:/usr/local/apache2/conf/httpd.conf -v $PWD/logs/:/usr/local/apache2/logs/ -d httpd

-p 80:80: 将容器的 80 端口映射到主机的 80 端口。

-v $PWD/www/:/usr/local/apache2/htdocs/: 将主机中当前目录下的 www 目录挂载到容器的 /usr/local/apache2/htdocs/。

-v $PWD/conf/httpd.conf:/usr/local/apache2/conf/httpd.conf: 将主机中当前目录下的 conf/httpd.conf 文件挂载到容器的 /usr/local/apache2/conf/httpd.conf。

-v $PWD/logs/:/usr/local/apache2/logs/: 将主机中当前目录下的 logs 目录挂载到容器的 /usr/local/apache2/logs/。

查看容器启动情况：
```





