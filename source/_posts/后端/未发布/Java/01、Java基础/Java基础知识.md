---
title: Java基础知识
categories:
- Java
tags:
- Java
- 基础知识
abbrlink: 43282
---
[2020年最新Java学习路线图（干货） - 知乎](https://zhuanlan.zhihu.com/p/115890802)

# Java基础知识

## 基础语法

Java语言是美国Sun公司（Stanford University Network），在1995年推出的高级的编程语言。所谓编程语言，是
计算机的语言，人们可以使用编程语言对计算机下达命令，让计算机完成人们需要的功能。

### 版本

- 1995年Sun公司发布Java1.0版本
- 1997年发布Java 1.1版本
- 1998年发布Java 1.2版本
- 2000年发布Java 1.3版本
- 2002年发布Java 1.4版本
- 2004年发布Java 1.5版本
- 2006年发布Java 1.6版本
- 2009年Oracle甲骨文公司收购Sun公司，并于2011发布Java 1.7版本
- 2014年发布Java 8版本
- 2017年发布Java 9.0版本
- 2018年3月发行 Java 10 版本

### 做什么

Java语言主要应用在互联网程序的开发领域。常见的互联网程序比如天猫、京东、物流系统、网银系统等，以及服
务器后台处理大数据的存储、查询、数据挖掘等也有很多应用。

## 安装

### Java虚拟机——JVM

JVM（Java Virtual Machine ）：Java虚拟机，简称JVM，是运行所有Java程序的假想计算机，是Java程序的
运行环境，是Java 最具吸引力的特性之一。我们编写的Java代码，都运行在JVM 之上。
跨平台：任何软件的运行，都必须要运行在操作系统之上，而我们用Java编写的软件可以运行在任何的操作系
统上，这个特性称为Java语言的跨平台特性。该特性是由JVM实现的，我们编写的程序运行在JVM上，而JVM
运行在操作系统上。

Java的虚拟机本身不具备跨平台功能的，每个操作系统下都有不同版本的虚拟机。

### JRE 和JDK

JRE (Java Runtime Environment) ：是Java程序的运行时环境，包含JVM 和运行时所需要的核心类库 。
JDK (Java Development Kit)：是Java程序开发工具包，包含JRE 和开发人员使用的工具。
我们想要运行一个已有的Java程序，那么只需安装JRE 即可。
我们想要开发一个全新的Java程序，那么必须安装JDK 。
北

![07-JDK&JRE&JVM关系示意图](https://i.loli.net/2020/08/06/hnBjFPZQW3a8yvb.png)

![image-20200806231516568](https://i.loli.net/2020/08/06/wWui7S1oDfvXE8l.png)

Java 目录结构

```
bin
conf
include
jmods
legal
lib
```

设置path

`JAVA_HOME` java的目录位置,而不是bin的目录

Path  添加 `%JAVA_HOME%\bin`

> 错误: 找不到或无法加载主类 basic.HelloWorld
> 原因: java.lang.ClassNotFoundException: basic.HelloWorld
>
> [(29条消息)IDEA 错误: 找不到或无法加载主类 解决方法_渣渣想逆袭-CSDN博客_错误: 找不到或无法加载主类](https://blog.csdn.net/kevinxxw/article/details/88647617)

没有指定.java 转换成 .class 文件的路径

```
.java 编译成 .class 文件
IDEA 软件中的项目结构
路径中的使用模块编译输出路径，要手动指定路径默认的路径出现错误
D:\GitRepository\IDEAWorkSpace\JavaAdvanced\production
```

IDEA 软件

项目构建

> Javac helllo.java 编译
>
> java hello 运行

```java
package basic;

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World"); // 控制台输出语句
    }
}   
```

## 基础

程序运行步骤

编写、编译、运行

文件名要与类名一致

编译文件

```
javac Hello.world.java
```

运行文件

```
java 类名
```

编译：是指将我们编写的Java源文件翻译成JVM认识的class文件，在这个过程中， javac 编译器会检查我们
所写的程序是否有错误，有错误就会提示出来，如果没有错误就会编译成功。
运行：是指将class文件 交给JVM去运行，此时JVM就会去执行我们编写的程序了。

main方法：称为主方法。写法是固定格式不可以更改。main方法是程序的入口点或起始点，无论我们编写多
少程序，JVM在运行的时候，都会从main方法这里开始执行。



注释

```
//

/*

*/
```

关键字与标识符

关键字：是指在程序中，Java已经定义好的单词，具有特殊含义。

标识符：是指在程序中，我们自己定义内容。比如类的名字、方法的名字和变量的名字等等，都是标识符。

命名规则： 硬性要求

- 标识符可以包含英文字母26个(区分大小写) 、0-9数字 、$（美元符号） 和_（下划线） 。
- 标识符不能以数字开头。
- 标识符不能是关键字。

命名规范： 软性建议

- `类名规范：首字母大写，后面每个单词首字母大写（大驼峰式）`。
- `方法名规范： 首字母小写，后面每个单词首字母大写（小驼峰式）`。
- `变量名规范：全部小写`。

### 常量和变量

常量：是指在Java程序中固定不变的数据。

| 类型       | 含义                                 | 数据举例    |
| ---------- | ------------------------------------ | ----------- |
| 整数常量   | 所有的整数                           | 23          |
| 小数常量   | 所有的小数                           | 0.34        |
| 字符常量   | 单引号引起来,只能写一个字符,必须有内 | `‘a’`       |
| 字符串常量 | 双引号引起来,可以写多个字符,也可以不 | "A"         |
| 布尔值常量 | 只有两个值（流程控制中讲解）         | true、false |
| 空常量     | 只有一个值（引用数据类型中讲解）     | null        |

 变量

变量：常量是固定不变的数据，那么在程序中可以变化的量称为变量。

Java中要求一个变量每次只能保存一个数据，必须要明确保存的数据类型。

```
 数据类型 变量名称 = 数据值; 
 int num = 1000;
 int num;
 num = 1000;
```

### 数据类型

Java的数据类型分为两大类：

- 基本数据类型：整数(byte、short、int 、long)、浮点型（float、double）、字符(char)、布尔（boolean）
- 引用数据类型：类、数组、接口、字符串、Lambda

基本数据类型

四类八种基本数据类型

| 数据类型     | 关键字       | 内存占用 | 取值范围               |
| ------------ | ------------ | -------- | ---------------------- |
| 字节型       | byte         | 1个字节  | -128~127               |
| 短整型       | short        | 2个字节  | -32768~32767           |
| 整型         | int(默认)    | 4个字节  | -231次方~2的31次方-1   |
| 长整型       | long         | 8个字节  | -2的63次方~2的63次方-1 |
| 单精度浮点数 | float        | 4个字节  | 1.4013E-45~3.4028E+38  |
| 双精度浮点数 | double(默认) | 8个字节  | 4.9E-324~1.7977E+308   |
| 字符型       | char         | 2个字节  | 0-65535                |
| 布尔类型     | boolean      | 1个字节  | true，false            |

Java中的默认类型：整数类型是int 、浮点类型是double 。

```
byte b = 100;
short s = 1000;
int i = 123454;
long l = 123412434566L;
float f = 5.5F;
double d = 8.7;
boolean bool = false;
char c = 'A';
```

注意

- 变量名不可以重复
- 对于float和long 类型来说，字母后缀F 和 L不要丢掉
- 作用域：从定义变量的一行开始，一直到直接所属的大括号结束为止
- 如果使用byte 或者 short类型的变量，右侧的数据值不能超过左侧类型的范围
- long 类型：建议数据后面加L 表示
- float类型： 建议数据后面加F表示
- 字符串不是基本类型，而是引用类型
- 浮点型可能只是一个近似值，并非精确的值
- 数据范围与字节数不一定相关，例如float 数据范围比long 更加广泛，但是float 是4个字节，long是8个字节

> Java BigInteger 的常用方法
>
> [Java中 BigInteger 的常用方法与注意事项 - 高欣的博客 - 博客园](https://www.cnblogs.com/Hrain/p/10354916.html)

### 数据类型转换

自动转换：将取值范围小的类型自动提升为取值范围大的类型 。





强制转换：将取值范围大的类型强制转换成取值范围小的类型。





对于byte/short/char 三种类型来说 ，如果右侧赋值的数值没有超过范围

那么javac 编译器将会自动隐含地为我们补上一个（Byte） (Short) (char) 

1. 如果 没有超过左侧的范围，编译器补上强转
2. 如果右侧超过左侧范围，那么直接编译器报错

```
byte num1 = /*(byte)*/ 30
```



```
数据类型 变量名 = （数据类型）被转数据值；
// double类型数据强制转成int类型，直接去掉小数点。
int i = (int)1.5;
```



### 运算符

#### 算数运算符

```
算数运算符包括：
+ 加法运算，字符串连接运算
- 减法运算
* 乘法运算
/ 除法运算
% 取模运算，两个数字相除取余数
++ 、 -- 自增自减运算

++ 运算，变量自己增长1。反之， -- 运算，变量自己减少1，用法与++ 一致。
独立运算：
变量在独立运算时， 前++ 和后++ 没有区别 。
变量前++ ：例如 ++i 。
变量后++ ：例如 i++ 。
混合运算：
和其他变量放在一起， 前++ 和后++ 就产生了不同。
```



#### 赋值运算符

```
赋值运算符包括：
= 等于号
+= 加等于
-= 减等于
*= 乘等于
/= 除等于
%= 取模等
```



#### 比较运算符

```
比较运算符包括：
== 比较符号两边数据是否相等，相等结果是true。
< 比较符号左边的数据是否小于右边的数据，如果小于结果是true。
> 比较符号左边的数据是否大于右边的数据，如果大于结果是true。
<= 比较符号左边的数据是否小于或者等于右边的数据，如果小于结果是true。
>= 比较符号左边的数据是否大于或者等于右边的数据，如果小于结果是true。
！= 不等于符号 ，如果符号两边的数据不相等，结果是true。
```



#### 逻辑运算符

```
逻辑运算符包括：
&& 短路与
1. 两边都是true，结果是true
2. 一边是false，结果是false
短路特点：符号左边是false，右边不再运算
|| 短路或
1. 两边都是false，结果是false
2. 一边是true，结果是true
短路特点： 符号左边是true，右边不再运算
！ 取反
1. ! true 结果是false
2. ! false结果是true
```



#### 三元运算符

```
数据类型 变量名 = 布尔类型表达式？结果1：结果2
三元运算符计算方式：
布尔类型表达式结果是true，三元运算符整体结果为结果1，赋值给变量。
布尔类型表达式结果是false，三元运算符整体结果为结果2，赋值给变量。
```



### 方法

#### 方法入门

方法：就是将一个功能抽取出来，把代码单独定义在一个大括号内，形成一个单独的功能。
当我们需要这个功能的时候，就可以去调用。这样即实现了代码的复用性，也解决了代码冗余的现象。

格式

```
修饰符 返回值类型 方法名 （参数列表）｛
代码...
return ;
｝
```

定义格式解释：
修饰符： 目前固定写法 public static 。

返回值类型： 目前固定写法 void ，其他返回值类型在后面的课程讲解。
方法名：为我们定义的方法起名，满足标识符的规范，用来调用方法。
参数列表： 目前无参数， 带有参数的方法在后面的课程讲解。
return：方法结束。因为返回值类型是void，方法大括号内的return可以不写。



方法的调用

方法在定义完毕后，方法不会自己运行，必须被调用才能执行，我们可以在主方法main中来调用我们自己定义好的方法。在
主方法中，直接写要调用的方法名字就可以调用了。

```
public static void main(String[] args) {
//调用定义的方法method
method();
}
//定义方法，被main方法调用
public static void method() {
System.out.println("自己定义的方法，需要被main调用运行");
}
```

定义方法的两个明确

需求：定义方法实现两个整数的求和计算。
明确返回值类型：方法计算的是整数的求和，结果也必然是个整数，返回值类型定义为int类型。
明确参数列表：计算哪两个整数的和，并不清楚，但可以确定是整数，参数列表可以定义两个int类型的
变量，由调用者调用方法时传递

```
public class Method_Demo2 {
public static void main(String[] args) {
// 调用方法getSum，传递两个整数，这里传递的实际数据又称为实际参数
// 并接收方法计算后的结果，返回值
int sum = getSum(5, 6);
System.out.println(sum);
}
/*
定义计算两个整数和的方法
返回值类型，计算结果是int
参数：不确定数据求和，定义int参数.参数又称为形式参数
*/
public static int getSum(int a, int b) {
return a + b;
}
}
```

定义方法的注意事项

定义位置，类中方法外面。
返回值类型，必须要和return 语句返回的类型相同，否则编译失败 。、

```
// 返回值类型要求是int
public static int getSum() {
return 5;// 正确，int类型
return 1.2;// 错误，类型不匹配
return true;// 错误，类型不匹配
}
不能在return 后面写代码， return 意味着方法结束，所有后面的代码永远不会执行，属于无效代码。
```

调用的三种形式

直接调用

```
public static void main(String[] args) {
print();
}
public static void print() {
System.out.println("方法被调用");
}
```

赋值调用

```
public static void main(String[] args) {
int sum = getSum(5,6);
System.out.println(sum);
}
public static int getSum(int a,int b) {
return a + b;
}
```

输出语句调用

```
public static void main(String[] args) {
System.out.println(getSum(5,6));
}
public static int getSum(int a,int b) {
return a + b;
}
```



#### 方法重载

方法重载：指在同一个类中，允许存在一个以上的同名方法，只要它们的参数列表不同即可，与修饰符和返
回值类型无关。
参数列表：个数不同，数据类型不同，顺序不同。
重载方法调用：JVM通过方法的参数列表，调用不同的方法。

```
public class Method_Demo6 {
public static void main(String[] args) {
//定义不同数据类型的变量
byte a = 10;
byte b = 20;
short c = 10;
short d = 20;
int e = 10;
int f = 10;
long g = 10;
long h = 20;
// 调用
System.out.println(compare(a, b));
System.out.println(compare(c, d));
System.out.println(compare(e, f));
System.out.println(compare(g, h));
}
// 两个byte类型的
public static boolean compare(byte a, byte b) {
System.out.println("byte");
return a == b;
}
// 两个short类型的
public static boolean compare(short a, short b) {
System.out.println("short");
return a == b;
}
// 两个int类型的
public static boolean compare(int a, int b) {
System.out.println("int");
return a == b;
}
// 两个long类型的
public static boolean compare(long a, long b) {
System.out.println("long");
return a == b;
}
}
```



### JShell

jdk 9.0 版本 以上

退出 ctrl + D

/exit

 

1. 





### 语句

流程控制

在一个程序执行的过程中，各条语句的执行顺序对程序的结果是有直接影响的。也就是说，程序的流程对运行结果
有直接的影响。所以，我们必须清楚每条语句的执行流程。而且，很多时候我们要通过控制语句的执行顺序来实现
我们要完成的功能。

顺序结构







判断语句

```
if(){

}

if(){

}else{

}

if(){

}else if(){

}else{

}
```

if 语句和三元运算符的互换

```
c = a > b ? a : b
```

#### 选择语句

```
switch(表达式) {
    case 常量值1:
    语句体1;
    break;
    case 常量值2:
    语句体2;
    break;
    ...
    default:
    语句体n+1;
    break;
}
switch (i){
    case 0:
    System.out.println("执行case0");
    break;
    case 5:
    System.out.println("执行case5");
    case 10:
    System.out.println("执行case10");
    default:
    System.out.println("执行default");
}
```

#### 循环语句

```
for(){}
while()
do while()
```

break 和 continue

break

使用场景：终止switch或者循环
在选择结构switch语句中
在循环语句中
离开使用场景的存在是没有意义的

continue

使用场景：结束本次循环，继续下一次的循环

死循环

死循环：也就是循环中的条件永远为true，死循环的是永不结束的循环。例如：while(true){}。

在后期的开发中，会出现使用死循环的场景，例如：我们需要读取用户输入的输入，但是用户输入多少数据我们并
不清楚，也只能使用死循环，当用户不想输入数据了，就可以结束循环了，如何去结束一个死循环呢，就需要使用
到跳出语句了。

#### 嵌套循环

所谓嵌套循环，是指一个循环的循环体是另一个循环。比如for循环里面还有一个for循环，就是嵌套循环。

总共的循环次数=外循环次数*内循环次数
嵌套循环格式：

```
for(初始化表达式①; 循环条件②; 步进表达式⑦) {
for(初始化表达式③; 循环条件④; 步进表达式⑥) {
执行语句⑤;
}
}
```

嵌套循环执行流程：
执行顺序：①②③④⑤⑥>④⑤⑥>⑦②③④⑤⑥>④⑤⑥
外循环一次，内循环多次。
比如跳绳：一共跳5组，每组跳10个。5组就是外循环，10个就是内循环。

### 数组

#### 数组的概念

数组就是存储数据长度固定的容器，保证多个数据的数据类型要一致。

#### 数组的定义

```java
        int[] arr = new int[]{1,2,3,4,5,6};
        int[] arr = {1,2,3,4,5,6};
        int arr[] = new int[3];
        arr[0] = 1;
        arr[1] = 2;
        arr[2] = 3;
        for (int arrs : arr) {
            System.out.println(arrs);
        }
```

方法1

```
数组存储的数据类型[] 数组名字 = new 数组存储的数据类型[长度];

数组定义格式详解：
数组存储的数据类型： 创建的数组容器可以存储什么数据类型。
[] : 表示数组。
数组名字：为定义的数组起个变量名，满足标识符规范，可以使用名字操作数组。
new：关键字，创建数组使用的关键字。
数组存储的数据类型： 创建的数组容器可以存储什么数据类型。
[长度]：数组的长度，表示数组容器中可以存储多少个元素。
注意：数组有定长特性，长度一旦指定，不可更改。

int[] arr = new int[3]
```

方法2

```
数据类型[] 数组名 = new 数据类型[]{元素1,元素2,元素3...};

int[] arr = new int[]{1,2,3,4,5}
```

方法3

```
数据类型[] 数组名 = {元素1,元素2,元素3,...};

int[] arr = {1,2,3,4,5};
```

#### 数组的访问

索引： 每一个存储到数组的元素，都会自动的拥有一个编号，从0开始，这个自动编号称为数组索引
(index)，可以通过数组的索引访问到数组中的元素。

```
数组名[索引]
```

数组的长度属性： 每个数组都具有长度，而且是固定的，Java中赋予了数组的一个属性，可以获取到数组的
长度，语句为： 数组名.length ，属性length的执行结果是数组的长度，int类型结果。由次可以推断出，数
组的最大索引值为数组名.length-1 。

索引访问数组中的元素：

- 数组名[索引]=数值，为数组中的元素赋值
- 变量=数组名[索引]，获取出数组中的元素

#### 数组原理内存图

内存概述

内存是计算机中的重要原件，临时存储区域，作用是运行程序。我们编写的程序是存放在硬盘中的，在硬盘中的程
序是不会运行的，必须放进内存中才能运行，运行完毕后会清空内存。
Java虚拟机要运行程序，必须要对内存进行空间的分配和管理。

java 虚拟机的内存划分

为了提高运算效率，就对空间进行了不同区域的划分，因为每一片区域都有特定的处理数据方式和内存管理方式。

JVM 的内存划分

区域名称作用
寄存器给CPU使用，和我们开发无关。
本地方法栈JVM在使用操作系统功能的时候使用，和我们开发无关。
方法区存储可以运行的class文件。
堆内存存储对象或者数组，new来创建的，都存储在堆内存。
方法栈方法运行时使用的内存，比如main方法运行，进入方法栈中执行。

数组在内存中的存储

```
public static void main(String[] args) {
    int[] arr = new int[3];
    System.out.println(arr);//[I@5f150435
}
```

以上方法执行，输出的结果是[I@5f150435，这个是什么呢？是数组在内存中的地址。new出来的内容，都是在堆
内存中存储的，而方法中的变量arr保存的是数组的地址。
输出arr[0]，就会输出arr保存的内存地址中数组中0索引上的元素

![image-20200808123134868](https://i.loli.net/2020/08/08/J8VaGutTgRn65os.png)

两个数组内存图

```
public static void main(String[] args) {
int[] arr = new int[3];
int[] arr2 = new int[2];
System.out.println(arr);
System.out.println(arr2);
}
```

![image-20200808123157640](https://i.loli.net/2020/08/08/K48udsgZTVUjBQh.png)





两个变量指向一个数组

```
public static void main(String[] args) {
// 定义数组，存储3个元素
int[] arr = new int[3];
//数组索引进行赋值
arr[0] = 5;
arr[1] = 6;
arr[2] = 7;
//输出3个索引上的元素值
System.out.println(arr[0]);
System.out.println(arr[1]);
System.out.println(arr[2]);
//定义数组变量arr2，将arr的地址赋值给arr2
int[] arr2 = arr;
arr2[1] = 9;
System.out.println(arr[1]);
}
```

![image-20200808123224024](https://i.loli.net/2020/08/08/RD9IeJArzmG3Vkt.png)







#### 数组的常见操作

数组越界

程序运行后，将会抛出 ArrayIndexOutOfBoundsException 数组越界异常。



数组空指针异常

```
public static void main(String[] args) {
int[] arr = {1,2,3};
arr = null;
System.out.println(arr[0]);
｝


```

运行的时候
会抛出NullPointerException 空指针异常。

数组遍历

```
public static void main(String[] args) {
int[] arr = { 1, 2, 3, 4, 5 };
for (int i = 0; i < arr.length; i++) {
System.out.println(arr[i]);
}
}
```

数组获取最大值

```
public static void main(String[] args) {
int[] arr = { 5, 15, 2000, 10000, 100, 4000 };
//定义变量，保存数组中0索引的元素
int max = arr[0];
//遍历数组，取出每个元素
for (int i = 0; i < arr.length; i++) {
//遍历到的元素和变量max比较
//如果数组元素大于max
if (arr[i] > max) {
//max记录住大值
max = arr[i];
}
}
System.out.println("数组最大值是： " + max);
}
```

数组翻转

```
public static void main(String[] args) {
int[] arr = { 1, 2, 3, 4, 5 };
/*
循环中定义变量min=0最小索引
max=arr.length‐1最大索引
min++,max‐‐
*/
for (int min = 0, max = arr.length ‐ 1; min <= max; min++, max‐‐) {
//利用第三方变量完成数组中的元素交换
int temp = arr[min];
arr[min] = arr[max];
arr[max] = temp;
}
// 反转后，遍历数组
for (int i = 0; i < arr.length; i++) {
System.out.println(arr[i]);
}
}
```



#### 数组作为方法参数和返回值

数组作为方法参数

数组作为方法参数传递，传递的参数是数组内存的地址。

```
public static void main(String[] args) {
int[] arr = { 1, 3, 5, 7, 9 };
//调用方法，传递数组
printArray(arr);
}
/*
创建方法，方法接收数组类型的参数
进行数组的遍历
*/
public static void printArray(int[] arr) {
for (int i = 0; i < arr.length; i++) {
System.out.println(arr[i]);
}
}
```

数组作为方法返回值

数组作为方法的返回值，返回的是数组的内存地址

```
public static void main(String[] args) {
//调用方法，接收数组的返回值
//接收到的是数组的内存地址
int[] arr = getArray();
for (int i = 0; i < arr.length; i++) {
System.out.println(arr[i]);
}
}
/*
创建方法，返回值是数组类型
return返回数组的地址
*/
public static int[] getArray() {
int[] arr = { 1, 3, 5, 7, 9 };
//返回数组的地址，返回到调用者
return arr;
}
```





方法的参数类型区别

```
public static void main(String[] args) {
int a = 1;
int b = 2;
System.out.println(a);
System.out.println(b);
change(a, b);
System.out.println(a);
System.out.println(b);
}
public static void change(int a, int b) {
a = a + b;
b = b + a;
}
```

方法的参数为基本类型时,传递的是数据值. 方法的参数为引用类型时,传递的是地址值.

### IDEA IDE 集成开发环境

项目的SDK 就是Java的目录，配置安装的JDK版本

新建项目

模块

包和类 所谓包，就是文件夹，用来对类文件进行管理。

可见com.itheima.demo ，表示创建了多级的文件夹。com/itheima.demo

字体设置

菜单栏上的File->Settings->Editor->Font 修改字体

我们创建的项目，在d:\ideawork目录的demo下
.idea 目录和demo.iml 和我们开发无关，是IDEA工具自己使用的
out 目录是存储编译后的.class文件
src 目录是存储我们编写的.java源文件

IDEA常用快捷键

Alt+Enter 导入包，自动修正代码
Ctrl+Y 删除光标所在行
Ctrl+D 复制光标所在行的内容，插入光标位置下面
Ctrl+Alt+L 格式化代码·
Ctrl+/ 单行注释
Ctrl+Shift+/ 选中代码注释，多行注释，再按取消注释
Alt+Ins 自动生成代码，toString，get，set等方法
Alt+Shift+上下箭头移动当前代码行

IDEA修改快捷键

在IDEA工具中， Ctrl+空格的快捷键，可以帮助我们补全代码，但是这个快捷键和Windows中的输入法切换快捷
键冲突，需要修改IDEA中的快捷键。
File->Settings->keymap->Main menu->code->Completion->Basic



## 





