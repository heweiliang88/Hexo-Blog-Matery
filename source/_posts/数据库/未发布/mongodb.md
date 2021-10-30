---
title: MongoDB非关系型数据库
categories:
- 数据库
tags:
- MongoDB
abbrlink: 51937
---

# MongoDB

mongoose 模块

```
npm i mongoose
```





> 分布式文件存储的数据库
>
> 介于关系数据库和非关系数据库之间的产品

MongoDB 是一个`基于分布式文件存储的开源数据库系统`。由 C++ 语言编写。旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。

MongoDB 是一个`介于关系数据库和非关系数据库之间的产品`，是非关系数据库当中功能最丰富，最像关系数据库的。

在高负载的情况下，添加更多的节点，可以保证服务器性能

MongoDB 将数据存储为一个文档，数据结构由键值(key=>value)对组成。MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。

主要特点

- MongoDB 是一个`面向文档存储的数据库`，操作起来比较简单和容易。

- 你可以在MongoDB记录中设置任何属性的索引 (如：FirstName="Sameer",Address="8 Gandhi Road")来实现更快的排序。
- 你可以通过本地或者网络创建数据镜像，这使得MongoDB有更强的扩展性。
- 如果负载的增加（需要更多的存储空间和更强的处理能力） ，它可以分布在计算机网络中的其他节点上这就是所谓的分片。
- Mongo支持丰富的查询表达式。查询指令使用JSON形式的标记，可轻易查询文档中内嵌的对象及数组。
- MongoDb 使用update()命令可以实现替换完成的文档（数据）或者一些指定的数据字段 。
- Mongodb中的Map/reduce主要是用来对数据进行批量处理和聚合操作。
- Map和Reduce。Map函数调用emit(key,value)遍历集合中所有的记录，将key与value传给Reduce函数进行处理。
- Map函数和Reduce函数是使用Javascript编写的，并可以通过db.runCommand或mapreduce命令来执行MapReduce操作。
- GridFS是MongoDB中的一个内置功能，可以用于存放大量小文件。
- MongoDB允许在服务端执行脚本，可以用Javascript编写某个函数，直接在服务端执行，也可以把函数的定义存储在服务端，下次直接调用即可。
- MongoDB支持各种编程语言:RUBY，PYTHON，JAVA，C++，PHP，C#等多种语言。
- MongoDB安装简单。

语言支持

C、C++、C# / .NET、Erlang、Haskell、Java、JavaScript、Lisp、node.JS、Perl、PHP、Python、Ruby、Scala

## 概述

[MongoDB中文网](https://www.mongodb.org.cn/)

### 安装MongoDB

[Download MongoDB Community Server | MongoDB](https://www.mongodb.com/try/download/community)

安装图形化界面

可以使用： Navicat Premium 15  软件

#### 目录结构

```
bin
data
log
```

> **命令行下运行 MongoDB 服务器** 和 **配置 MongoDB 服务** 任选一个方式启动就可以。任选一个操作就好

#### 方法一

##### 运行MongoDB服务器 `bin目录`

```bash
:\bin\mongod --dbpath 当前的:\data\db
D:\SoftWare\NodeJs\mongodb\bin\mongod --dbpath D:\SoftWare\NodeJs\mongodb\data\db
```

##### 连接MongoDB `bin目录`

```
:\bin\mongo.exe
```

#### 方法二

##### 配置MongoDB服务

创建目录，执行下面的语句来创建数据库和日志文件的目录

```
mkdir c:\data\db
mkdir c:\data\log
```

##### 创建配置文件

创建一个配置文件。该文件必须设置 systemLog.path 参数，包括一些附加的配置选项更好。

例如，创建一个配置文件位于 C:\mongodb\mongod.cfg，其中指定 systemLog.path 和 storage.dbPath。具体配置内容如下：

```
systemLog:
    destination: file
    path: c:\data\log\mongod.log
storage:
    dbPath: c:\data\db
```

##### 安装 MongoDB服务

通过执行mongod.exe，使用--install选项来安装服务，使用--config选项来指定之前创建的配置文件。

```
C:\mongodb\bin\mongod.exe --config "C:\mongodb\mongod.cfg" --install
```

要使用备用 dbpath，可以在配置文件（例如：C:\mongodb\mongod.cfg）或命令行中通过 --dbpath 选项指定。

如果需要，您可以安装 mongod.exe 或 mongos.exe 的多个实例的服务。只需要通过使用 --serviceName 和 --serviceDisplayName 指定不同的实例名。只有当存在足够的系统资源和系统的设计需要这么做。

启动MongoDB服务

```
net start MongoDB
```

关闭MongoDB服务

```
net stop MongoDB
```

移除 MongoDB 服务

```
C:\mongodb\bin\mongod.exe --remove
```

------

#### MongoDB 后台管理 Shell

如果你需要进入MongoDB后台管理，你需要先打开mongodb装目录的下的bin目录，然后执行`mongo.exe`文件，MongoDB Shell是MongoDB自带的交互式Javascript shell,用来对MongoDB进行操作和管理的交互式环境。

当你进入mongoDB后台后，它默认会链接到 test 文档（数据库）：

```
> mongo
MongoDB shell version: 3.0.6
connecting to: test
……
```

由于它是一个JavaScript shell，您可以运行一些简单的算术运算:

```
> 2 + 2
4
>
```

**db** 命令用于查看当前操作的文档（数据库）：

```
> db
test
>
```

插入一些简单的记录并查找它：

```
> db.runoob.insert({x:10})
WriteResult({ "nInserted" : 1 })
> db.runoob.find()
{ "_id" : ObjectId("5604ff74a274a611b0c990aa"), "x" : 10 }
>
```

第一个命令将数字 10 插入到 runoob 集合的 x 字段中。

概念解析

mongodb中基本的概念是文档、集合、数据库

数据库



文档



集合



元数据



MongoDB 数据类型





## 数据库

### 连接数据库

启动MongoDB服务

在 MongoDB 安装目录的 bin 目录下执行 **mongodb** 即可。

```
mongodb
```

连接 MongoDB 服务器

使用 MongoDB shell 来连接 Mongodb 服务

```
mongodb://[username:password@]host1[:port1][,host2[:port2],...[,hostN[:portN]]][/[database][?options]]
mongodb:// 这是固定的格式，必须要指定。
username:password@ 可选项，如果设置，在连接数据库服务器之后，驱动都会尝试登陆这个数据库
host1 必须的指定至少一个host, host1 是这个URI唯一要填写的。它指定了要连接服务器的地址。如果要连接复制集，请指定多个主机地址。
portX 可选的指定端口，如果不填，默认为27017
/database 如果指定username:password@，连接并验证登陆指定数据库。若不指定，默认打开 test 数据库。
?options 是连接选项。如果不使用/database，则前面需要加上/。所有连接选项都是键值对name=value，键值对之间通过&或;（分号）隔开
```

MongoDB连接命令格式()

使用用户名和密码连接到 MongoDB 服务器

```
username:password@hostname/dbname
```

### 查看所有数据库

```sql
show dbs
```

### 创建数据库

创建数据库

```sql
use DATABASE_NAME //数据库名
use admin
// 如果数据库不存在，则创建数据库，否则切换到指定数据库。
```

刚创建的数据库 并不在数据库的列表中， 要显示它，我们需要向 数据库插入一些数据。

```
db.admin.insert({"username":'123456'}) //admin 数据库名
show dbs
```

MongoDB 中默认的数据库为 test，如果你没有创建新的数据库，集合将存放在 test 数据库中。

### 删除数据库

> 删除数据库要先切换到要删除的数据库

删除当前数据库

```sql
db.dropDatabase()
删除当前数据库，默认为test
```

查看所有数据库

```sql
show dbs
```

切换数据库

```sql
use admin // admin 数据库名
switched to db admin
db.dropDatabase() // 删除命令
```

## 集合

### 创建集合

集合可以类似为数组

```
use admin // 创建数据库
db.createCollection(name,option)
name : 要创建的名称
option：可选的参数，指定的有关内存大小及索引
```

| 字段        | 类型 | 描述                                                         |
| :---------- | :--- | :----------------------------------------------------------- |
| capped      | 布尔 | （可选）如果为 true，则创建固定集合。固定集合是指有着固定大小的集合，当达到最大值时，它会自动覆盖最早的文档。 **当该值为 true 时，必须指定 size 参数。** |
| autoIndexId | 布尔 | 3.2 之后不再支持该参数。（可选）如为 true，自动在 _id 字段创建索引。默认为 false。 |
| size        | 数值 | （可选）为固定集合指定一个最大值，以千字节计（KB）。 **如果 capped 为 true，也需要指定该字段。** |
| max         | 数值 | （可选）指定固定集合中包含文档的最大数量。                   |

创建固定集合 mycol，整个集合空间大小 6142800 KB, 文档最大个数为 10000 个。

```sql
db.createCollection("mycol",{ // mycol 集合名
    capped:true,
    autoIndexId:true,
    size:6142800,
    max:10000
})
```

重点：在 MongoDB 中，你不需要创建集合。当你插入一些文档时，MongoDB 会自动创建集合。

插入数据

```sql
db.mycol2.insert({"username":"123456"}) //mycol2 集合名
show collections
```

### 查看集合

```sql
show collections //或者 show tables
```

### 删除集合

```sql
db.collection.drop()
// db.集合名.drop()
```

## 文档 

BJSON 格式的数据

### 插入文档（增）

如何将数据插入到 MongoDB 的集合中

文档的数据结构和 JSON 基本一样。

所有存储在集合中的数据都是 BSON 格式。

BSON 是一种类似 JSON 的二进制形式的存储格式，是 Binary JSON 的简称。

MongoDB 使用 insert() 或 save() 方法向集合中插入文档

```
db.COLLECTION_NAME.insert(document)
db.COLLECTION_NAME.save(document)
```



### 更新文档（改）



### 删除文档（删）



### 查询文档（查）

MongoDB 查询文档使用 find() 方法。

find() 方法以非结构化的方式来显示所有文档。

```
db.collection.find(query,projection)
query ：可选，使用查询操作符指定查询条件
projection ：可选，使用投影操作符指定返回的键。查询时返回文档中所有键值， 只需省略该参数即可（默认省略）。
```

如果你需要以易读的方式来读取数据，可以使用 pretty() 方法，语法格式如下：

```
db.col.find().pretty()
```



## 基础

### MongoDB 条件操作符			

### MongoDB $type 操作符			

### MongoDB Limit与Skip方法			

### MongoDB 排序			

### MongoDB 索引			

### MongoDB 聚合			

### MongoDB 复制(副本集)			

### MongoDB 分片			

### MongoDB 备份与恢复			

### MongoDB 监控



## 高级

### MongoDB 关系	

​		

### MongoDB 数据库引用			



### MongoDB 覆盖索引查询		

​	

### MongoDB 查询分析			



### MongoDB 原子操作			



### MongoDB 高级索引			



### MongoDB 索引限制

​			

### MongoDB ObjectId

​			

### MongoDB Map Reduce		

​	

### MongoDB 全文检索		

​	

### MongoDB 正则表达式			



### MongoDB 管理工具			



### MongoDB GridFS			



### MongoDB 固定集合			



### MongoDB 自动增长			



可视化工具 Rob3T

## 使用

### MongoDB Java

---



### MongoDB PHP

---



### Node.js MongoDB

---

MongoDB是一种`文档导向数据库管理系统`，由C++撰写而成。

#### 安装驱动

```bash
npm install mongodb
```

#### 创建数据库

创建数据库，创建一个MongoClient 对象，配置指定的URL 和端口号

```js
var MongoClient = require('mongodb').MongoClient;
var url = "mongodb://localhost:27017/heweiliang";

MongoClient.conntect(url,{ useNewUrlParser:true },function(err,db){
    if(err) throw err;
    console.log('数据库已经创建成功')；
    db.close();
})
```



#### 创建集合



#### 数据库操作（CURD）

插入数据



查询数据



更新数据



删除数据



#### 排序



#### 查询分页



#### 连续操作



#### 删除集合



#### 使用Promise



#### promise 数据操作



#### 用异步函数实现相同的数据操作









