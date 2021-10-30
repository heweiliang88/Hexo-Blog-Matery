---
title: Maven
categories:
- Java
tags:
- Java
- Maven
abbrlink: 32913
---
# Maven 项目管理工具

[Maven 教程 ](https://www.runoob.com/maven/maven-tutorial.html)

## 基本概念

### 什么是Maven

Maven的正确发音是[ˈmevən]，而不是“马瘟”以及其他什么瘟。Maven在美国是一个口语化的词语，代表专家、内行的意思。
一个对Maven比较正式的定义是这么说的：`Maven是一个项目管理工具`，它包含了一个项目对象模型 (POM：Project Object Model)，一组标准集合，一个项目生命周期(Project Lifecycle)，一个依赖管理系统(Dependency Management System)，和用来运行定义在生命周期阶段(phase)中插件(plugin)目标(goal)的逻辑。

### 解决什么问题

可以把你从上面的繁琐工作中解放出来，能帮你`构建工程，管理jar包，编译代码，还能帮你自动运行单元测试，打包，生成报表，甚至能帮你部署项目，生成Web站点`，Maven就可以解决上面所提到的这些问题。

### Maven的好处

- 节省磁盘空间
- 可以一键构建
- 可以跨平台
- 应用在大型项目时可以提高开发效率

### Maven的优势



### Maven的两个经典作用

#### Maven的依赖管理

Maven的一个核心特性就是依赖管理。当我们涉及到多模块的项目（包含成百个模块或者子项目），管理依赖就变成一项困难的任务。Maven展示出了它对处理这种情形的高度控制。
传统的WEB项目中，我们必须将工程所依赖的jar包复制到工程中，导致了工程的变得很大。那么maven工程是如何使得工程变得很少呢？
分析如下：

![image-20200808140021289](https://i.loli.net/2020/08/08/2hZ9H1TgeROGWSp.png)



通过分析发现：maven工程中不直接将jar包导入到工程中，而是通过在pom.xml文件中添加所需jar包的坐标，这样就很好的避免了jar直接引入进来，在需要用到jar包的时候，只要查找pom.xml文件，再通过pom.xml文件中的坐标，到一个专门用于”存放jar包的仓库”(maven仓库)中根据坐标从而找到这些jar包，再把这些jar包拿去运行。
那么问题来了
第一：”存放jar包的仓库”长什么样？
第二：通过读取pom.xml 文件中的坐标，再到仓库中找到jar包，会不会很慢？从而导致这种方式不可行！
第一个问题：存放jar包的仓库长什么样，这一点我们后期会分析仓库的分类，也会带大家去看我们的本地的仓库长什么样。
第二个问题：通过pom.xml文件配置要引入的jar包的坐标，再读取坐标并到仓库中加载jar包，这样我们就可以直接使用jar包了，为了解决这个过程中速度慢的问题，maven中也有索引的概念，通过建立索引，可以大大提高加载jar包的速度，使得我们认为jar包基本跟放在本地的工程文件中再读取出来的速度是一样的。这个过程就好比我们查阅字典时，为了能够加快查找到内容，书前面的目录就好比是索引，有了这个目录我们就可以方便找到内容了，一样的在maven仓库中有了索引我们就可以认为可以快速找到jar包。

#### 项目的一键构建

我们的项目，往往都要经历编译、测试、运行、打包、安装 ，部署等一系列过程。
什么是构建？
指的是项目从编译、测试、运行、打包、安装 ，部署整个过程都交给maven进行管理，这个过程称为构建。
一键构建
指的是整个构建过程，使用maven一个命令可以轻松完成整个工作。

Maven规范化构建流程如下：

![image-20200808135940157](https://i.loli.net/2020/08/08/TjSzxCqn3ihbMKR.png)

## 安装和仓库种类

### 安装

Apache-maven-3.5.2下载地址：http://archive.apache.org/dist/maven/maven-3/

Maven及JDK 配置

安装 JDK path 

```
JAVA_HOME/bin 配置环境变量path
```

配置`MAVEN_HOME`，变量值就是你的 maven 安装的路径（bin目录之前一级目录）

注意这个目录就是之前你解压maven的压缩文件包在的的目录，最好不要有中文和空格。

Maven 软件版本测试

```
mvn -v
看到maven的版本为3.5.2及java版本为1.8即为安装成功。
```

### 仓库种类

三种仓库

- 本地仓库
- 远程仓库（私服）
- 中央仓库

### 常用命令

```
Compile
Test
Package
Install
Deploy
Clean
```

### 坐标

#### 坐标的书写规范

```
groupId 公司或组织域名的倒序
artifactId 项目名或模块名
version 版本号
```

#### 如何添加坐标

- 在本地仓库搜索
- 互联网上搜：http://www.mvnrepository.com/

#### 依赖范围

- Compile
- Test
- Runtime
- Rrovided



## 标准目录和常用结构



## 生命周期和概念模型图



## 使用骨架创建maven的Java工程



## maven工程的servlet 实例





## maven 构建SSM 工程







## maven 分模块构建



## 私服















