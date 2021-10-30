---
title: MySQL关系型数据库
categories:
- 数据库
tags:
- MySQL
abbrlink: 46527
---
#  MySQL

## 数据库集成环境安装

### wampserve

账号 root 密码 无

```mysql
mysql -h 127.0.0.1 -u root -p 
```

### phpstudy（推荐）

账号 root 密码 root

```mysql
mysql -h 127.0.0.1 -uroot -proot
```

集成环境常遇到的问题：

- 环境变量
- 端口占用

### mysql 安装

CentOS 的yum源中没有mysql，需要到mysql的官网下载yum repo配置文件

```bash
wget https://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm
rpm -ivh mysql57-community-release-el7-9.noarch.rpm
在/etc/yum.repos.d/目录下生成两个repo文件mysql-community.repo mysql-community-source.repo
```

```bash
yum install mysql-server
systemctl start mysqld #启动MySQL restart start enable 开机启动 disable 关机 
grep 'temporary password' /var/log/mysqld.log // 获取安装时的临时密码（在第一次登录时就是用这个密码）
rm -rf /var/lib/mysql // 删除mysql
```

修改密码

```
查看初始密码 
SHOW VARIABLES LIKE 'validate_password%
ALTER USER 'root'@'localhost' IDENTIFIED BY '@abcd123456';
set password=password("yourpassword"); 
```

开启远程连接

```
use mysql;
show tables;
select Host, User,Password from user;
update user set Host='%' where User='root'; 
flush privileges;

GRANT ALL PRIVILEGES ON *.* TO root@"%" IDENTIFIED BY "rw";
flush privileges;
exit;
```

修改密码

[CentOS7下安装mysql5.7](https://blog.csdn.net/wohiusdashi/article/details/89358071)

```mysql
获取安装时的临时密码（在第一次登录时就是用这个密码）
grep 'temporary password' /var/log/mysqld.log

查看 mysql 初始的密码策略
SHOW VARIABLES LIKE 'validate_password%';
set global validate_password_length=6;
// 设置密码的验证强度等级
set global validate_password_policy=LOW;
修改密码
ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
systemctl restart mysqld

在终端输入：mysql -u用户名 -p密码，回车进入Mysql。
> use mysql;
> update user set password=PASSWORD('新密码') where user='用户名';
> flush privileges; #更新权限
> quit; #退出
```

### Docker 安装



## 数据库工具

- MySQL
- Navicat

## 数据库绘图 ER 图



## 数据库基础知识

### 什么是数据库

MySQL 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好的 RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

数据库（Database）是按照数据结构来``组织、存储和管理数据``的仓库。使用关系型数据库管理系统（RDBMS）来存储和管理大数据量。关系型数据库，是建立在关系模型基础上的数据库，借助于集合代数等数学概念和方法来处理数据库中的数据。

也可以将数据存储在文件中，但是``在文件中读写数据速度相对较慢``。

### RDBMS (关系数据库管理系统)

RDBMS的特点

- 数据以表格的形式出现
- 每行为各种记录名称
- 每列为记录名称所对应的数据域
- 许多的行和列组成一张表单
- 若干的表单组成database

RDBMS的术语

| 术语             | 作用                                                         |
| ---------------- | ------------------------------------------------------------ |
| 数据库`database` | 数据库是一些关联表的集合。                                   |
| 数据表`table`    | 表是数据的矩阵。在一个数据库中的表看起来像一个简单的电子表格。 |
| 列、`column  `   | 一列(数据元素) 包含了相同类型的数据, 例如邮政编码的数据。    |
| 行 `row`         | 一行（=元组，或记录）是一组相关的数据，例如一条用户订阅的数据。 |
| 冗余             | 存储两倍数据，冗余降低了性能，但提高了数据的安全性。（复制一份） |
| 主键             | 主键是唯一的。一个数据表中只能包含一个主键。你可以使用主键来查询数据。 |
| 外键             | `外键用于关联两个表`。                                       |
| 复合键           | 复合键（组合键）将多个列作为一个索引键，一般用于复合索引。   |
| 索引             | 使用索引可``快速访问数据库表中的特定信息。``索引是对数据库表中一列或多列的值进行排序的一种结构。类似于书籍的目录。 |
| 参照完整性       | 参照的完整性要求关系中不允许引用不存在的实体。与实体完整性是关系模型必须满足的完整性约束条件，目的是保证数据的一致性。 |

MySQL 为关系型数据库(Relational Database Management System), 这种所谓的"关系型"可以理解为"表格"的概念, 一个关系型数据库由一个或数个表格组成, 如图所示的一个表格

| 术语         | 作用                                         |
| ------------ | -------------------------------------------- |
| 表头`header` | 每一列的名称                                 |
| 列`col`      | 具有相同数据类型的数据集合                   |
| 行`row`      | 每一行用来描述某条记录的具体信息             |
| 值`value`    | 行的具体信息, 每个值必须与该列的数据类型相同 |
| 键`key`      | 键的值在当前列中具有唯一性                   |

### 数据类型 23个

- MySQL支持所有标准SQL数值数据类型。

- 关键字INT是INTEGER的同义词，关键字DEC是DECIMAL的同义词

| 数据类型         |                                                              |
| ---------------- | ------------------------------------------------------------ |
| 数值             | `tinyint、smallint、mediumint、int或integer、bigint、float、double、decimal` |
| 日期/时间        | `date、time、year、datetime、timestamp`                      |
| 字符串(字符)类型 | `char、varchar、tinyblob、tinytext、blob、text、mediumblob、mediumtext、longblob、longtext` |

#### 数值类型 8个

- `tinyint、smallint、mediumint、int或integer、bigint、`  1\2\3\4\8 Bytes
- `float、double` 4\8 Bytes
- `decimal`  小数值

| 类型         | 大小                                     | 范围（有符号）                                               | 范围（无符号）                                               | 用途            |
| :----------- | :--------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------- |
| TINYINT      | 1 byte                                   | (-128，127)                                                  | (0，255)                                                     | 小整数值        |
| SMALLINT     | 2 bytes                                  | (-32 768，32 767)                                            | (0，65 535)                                                  | 大整数值        |
| MEDIUMINT    | 3 bytes                                  | (-8 388 608，8 388 607)                                      | (0，16 777 215)                                              | 大整数值        |
| INT或INTEGER | 4 bytes                                  | (-2 147 483 648，2 147 483 647)                              | (0，4 294 967 295)                                           | 大整数值        |
| BIGINT       | 8 bytes                                  | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)      | (0，18 446 744 073 709 551 615)                              | 极大整数值      |
|              |                                          |                                                              |                                                              |                 |
| FLOAT        | 4 bytes                                  | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38)                  | 单精度 浮点数值 |
| DOUBLE       | 8 bytes                                  | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度 浮点数值 |
|              |                                          |                                                              |                                                              |                 |
| DECIMAL      | 对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2 | 依赖于M和D的值                                               | 依赖于M和D的值                                               | 小数值          |

#### 日期/时间类型 5个

- `year(年份)`  1
- `date(日期)、time(时间)、datetime(混合日期和时间值)`    3、3、8
- `timestamp(时间戳)` 4

| 类型      | 大小 ( bytes) | 范围                                                         | 格式                | 用途                     |
| :-------- | :------------ | :----------------------------------------------------------- | :------------------ | :----------------------- |
| YEAR      | 1             | 1901/2155                                                    | YYYY                | 年份值                   |
| DATE      | 3             | 1000-01-01/9999-12-31                                        | YYYY-MM-DD          | 日期值                   |
| TIME      | 3             | '-838:59:59'/'838:59:59'                                     | HH:MM:SS            | 时间值或持续时间         |
| TIMESTAMP | 4             | 1970-01-01 00:00:00/2038结束时间是第 **2147483647** 秒，北京时间 **2038-1-19 11:14:07**，格林尼治时间 2038年1月19日 凌晨 03:14:07 | YYYYMMDD HHMMSS     | 混合日期和时间值，时间戳 |
| DATETIME  | 8             | 1000-01-01 00:00:00/9999-12-31 23:59:59                      | YYYY-MM-DD HH:MM:SS | 混合日期和时间值         |

#### 字符串类型 10个

- `tiny、medium、long`
- char、varchar
- tinyblob、blob、mediumblob、longblob(二进制形式)
- tinytext、text、mediumtext、longtext

| 类型       | 大小                  | 用途                            |
| :--------- | :-------------------- | :------------------------------ |
| CHAR       | 0-255 bytes           | 定长字符串                      |
| VARCHAR    | 0-65535 bytes         | 变长字符串                      |
|            |                       |                                 |
| TINYBLOB   | 0-255 bytes           | 不超过 255 个字符的二进制字符串 |
| BLOB       | 0-65 535 bytes        | 二进制形式的长文本数据          |
| MEDIUMBLOB | 0-16 777 215 bytes    | 二进制形式的中等长度文本数据    |
| LONGBLOB   | 0-4 294 967 295 bytes | 二进制形式的极大文本数据        |
|            |                       |                                 |
| TINYTEXT   | 0-255 bytes           | 短文本字符串                    |
| MEDIUMTEXT | 0-16 777 215 bytes    | 中等长度文本数据                |
| TEXT       | 0-65 535 bytes        | 长文本数据                      |
| LONGTEXT   | 0-4 294 967 295 bytes | 极大文本数据                    |

## 数据库基本操作

### 命令行启动关闭

```mysql
验证 MySQL 安装
mysqladmin --version
```

```mysql
//启动
cd c:/mysql/bin
mysqld --console
//关闭
mysqladmin -uroot shutdown
```

### 连接数据库

```mysql
mysql -h 主机名字 host -u用户名 user -p 密码 password
mysql -h 127.0.0.1 -uroot -p
//连接到本机上的MySQL
// 默认127.0.0.1
mysql -uroot -p
// 无密码 直接回车
```

### 显示所有的数据库

```mysql
show databases;
```

### 退出数据库

```mysql
mysql> exit
mysql> quit
```

## 数据库（增删改查） 

库：use create drop update select show 

### 使用数据库

```
use test; // use 数据库名;
```

### 创建数据库 `增`

```mysql
create database test;
create database test default charse=utf-8; // 中文乱码
```

### 删除数据库 `删`

```mysql
drop database test;
```

### 查看当前使用的数据库 `查`

```mysql
select database();
```

## 数据表（增删改查）

当前数据库包含的表信息

```mysql
show tables;
INSERT INTO student('sno', 'name', 'sex', 'age', 'dept') VALUES ('1700001', '张三', '男', 20, '计算机系');
INSERT INTO student('sno', 'name', 'sex', 'age', 'dept') VALUES ('1700002', '李四', '女', 19, '外语系');
INSERT INTO student('sno', 'name', 'sex', 'age', 'dept') VALUES ('1700003', '王五', '男', 18, '哲学系');
INSERT INTO student('sno', 'name', 'sex', 'age', 'dept') VALUES ('1830315','成六','男',18,'计算机系');
```

### 创建表 `增`

- 表名
- 表字段
- 定义每个表字段

`not null` ：操作数据库时如果输入该字段的数据为**NULL** ，就会报错

`auto_increment`：定义列为自增的属性，一般用于主键，数值会自动加1

`primary key`：关键字用于定义列为主键。 您可以使用多列来定义主键，列间以逗号分隔

`engine`：设置存储引擎

`charset`：设置编码

```mysql
create table <表名> (<字段名1><类型1>  [,..<字段名 n> <类型 n>]);
create table MyClass(
    id int(4) not null primary key auto_increment,
    name char(20) not null,
    sex int(4) ,
    degree double(16,2)
);

create table MyDoubleClass(
	id int(4) not null primary key auto_increment
    name char(20) 
)

create table MyGuests{
	id int(4) not null primary key,
	firstname 
}

create table user( username char(20) not null  , password char(20) not null);
insert into user values('123','123'),('456','456'), ('789', '789');

create table student(
    学号 char(10) not null primary key,
    姓名 varchar(10) not null unique,
    性别 char(2),
    出生时间 datetime
) engine = myisam default charset=utf8 // 表格中文乱码

create table if not exists 表名(){
	
} engine = InnoDB default charset=utf8; 
```

```mysql
修改表中数据
命令:update 表名 set 字段=新值,... where 条件
update MyClass set name='Mary' where id=1;
```

插入数据

```mysql
insert into <表名> [( <字段名 1>[,..<字段名 n > ])] values ( 值 1 )[, ( 值 n )]
部分列
insert into table_name (column_name,column_name2,...) values (value1,value2),(value1,value2);
全部列 
insert into myclass values(1,'Tom',96.45),(2,'Joan',82.99), (2,'Wang', 96.59);
```

**第一、只复制表结构到新表**

create table 新表 select * from 旧表 where 1=2 或者

create table 新表 like 旧表 

**第二、复制表结构及数据到新表**

create table新表 select * from 旧表 

### 获取表结构

```mysql
desc 表名;
// describe MyClass
show columns from 表名;
```

### 删除表 `删`

```mysql
drop table <表名>;
delete from student;
delete from student where 姓名 = “王五”
```

### 更改表名 `改`

```mysql
rename table 原表名 to 新表名
```

更新字段内容

```mysql
命令:update 表名 set 字段名 = 新内容
update 表名 set 字段名 = replace(字段名, '旧内容', '新内容');
例如:文章前面加入 4 个空格
update article set content=concat('    ', content);
update table_name set column_name = new_calue,column_name2 = new_value2,...[where condition]
update student set 专业 = ’软件技术‘ where 姓名 = ’王丹‘;
```

### 查询表中得数据  `查`

查询所有行

```mysql
select * from MyClass;
```

查询前几行数据

```mysql
前2行数据
select * from MyClass order by id limit 0,2;
select * from MyClass limit 0,2;
```

查询数据库记录

```mysql
select field 
from table_name 
where
```

```mysql
select field //要查询的内容，选择那些列
from table_name // 指定数据表
where condition  // 查询时需要满足的条件
order by fileldm1 [ASC|DESC]  //对查询结果进排序的条件
limit row_count  //限定输出的查询结果
group by field  // 对查询结果进行分组的条件

查询指定列
select 列名1,列名2 from 表名;

命别名
select 学号 as id，姓名 as name from student;

满足的条件  
注意使用的是单引号，而不是双引号
select * from student where 专业 = '软件技术' and 性别 = '男'
select * from student where 专业 = '软件技术' or 性别 = '男'
 
select * from student where 总学分 between 15 and 20 // 包括边界
select * from student where 总学分 not between 15 and 20 // 包括边界

// 查询指定的值
select * from student where 姓名 in(’刘鑫‘);
select * from student where 姓名 not in(’刘鑫‘);

select * from student where 姓名 like '王_'
select * from student where 姓名 like '王__'
select * from student where 姓名 like '王%'
```

查询表中的一列或多列

```mysql
在where 子句中使用谓语
between and 在两数之间
not  between  and 不在两数之间 

in<值表> 是否在特定的集合里	
not in <值表> ：
like 是否匹配与一个模式 模糊查询
```

## 数据库导入导出

### 导出

#### 导出所有数据库

```
mysqldump -u [数据库用户名] -p -A>[备份文件的保存路径]
```

#### 导出数据和数据结构

特别注意

```
mysqldump -h localhost -u root -p management >C:/mydb.sql

c:\> mysqldump -h localhost -u root -p mydb(数据库名) mytable(数据库里面的表名)> c:\MySQL\mytable.sql
运行命令是在 盘符 而不是 mysql> 里面运行  
要新建目录，要不然找不到目录的位置
```

```
mysqldump -u [数据库用户名] -p [要备份的数据库名称]>[备份文件的保存路径]
```

```mysql
导出数据库
例 1:将数据库 mydb 导出到 e:\MySQL\mydb.sql 文件中。
打开开始->运行->输入“cmd”,进入命令行模式。
c:\> mysqldump -h localhost -u root -p management >c:\mydb.sql;
然后输入密码,等待一会导出就成功了,可以到目标文件中检查是否成功。

导出数据表
例 2:将数据库 mydb 中的 mytable 导出到 e:\MySQL\mytable.sql 文件中。
c:\> mysqldump -h localhost -u root -p mydb mytable>e:\MySQL\mytable.sql

数据库结构
例 3:将数据库 mydb 的结构导出到 e:\MySQL\mydb_stru.sql 文件中。
c:\> mysqldump -h localhost -u root -p mydb --add-drop-table >e:\MySQL\mydb_stru.sql
备注:-h localhost 可以省略,其一般在虚拟主机上用。
```

#### 只导出数据不导出数据结构

```mysql
mysqldump -u [数据库用户名] -p -t [要备份的数据库名称]>[备份文件的保存路径]
```

#### 导出数据库中的Events

```mysql
mysqldump -u [数据库用户名] -p -E [数据库用户名]>[备份文件的保存路径]
```

#### 导出数据库中的存储过程和函数

```mysql
mysqldump -u [数据库用户名] -p -R [数据库用户名]>[备份文件的保存路径]
```

#### 从外部文件导出数据库中

#### 从数据库导出数据文件

```
\.  sql文件所在的目录
source  sql文件所在的目录
```

使用“mysqldump”命令
首先进入 DOS 界面,然后进行下面操作。

#### 使用 "source" 命令

```mysql
首先进入“mysql”命令控制台,然后创建数据库,然后使用该数据库。最后执行下面操作。
mysql> source [备份文件的保存路径]
```

#### 使用 " < " 符号

```mysql
mysql -u root -p < [备份文件的保存路径]
```

### 导入





