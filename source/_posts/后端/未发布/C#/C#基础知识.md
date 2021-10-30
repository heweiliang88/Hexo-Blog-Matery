---
title: C#基础知识
categories:
- C#
tags:
- C#
abbrlink: 15084
---
## C#基础知识

Asp.Net动态Web设计

###### C#相应的岗位

ASP.NET软件工程师

.NET WinForm工程师

### C#介绍

C#是微软（Microsoft）**为.NET Framework量身定做的程序语言**，在Visual Studio中，使用.NET基本类库可以开发多种应用程序，如**控制台应用程序、Windows 窗体应用程序、ASP.NET Web窗体应用程序、WPF应用程序**等。

**C#语言的特点**

- **语法简洁**
- **彻底的面向对象设计**
- **与** **Web** **紧密结合**
- **强大的安全机制**
- **完善** **的错误、异常处理机制**
- **灵活 ** **的版本处理技术**
- **兼容性**  

###### C#是什么？

1. C# 编程是**基于 C 和 C++ 编程语言衍生出来的面向对象的编程语言**

2. C#是微软公司发布的一种面向对象的、**运行于.NET Framework之上**的高级程序设计语言。

###### C#与java的对比

1. 同点：它包括了诸如单一继承、接口、与Java几乎同样的语法和编译成中间代码再运行的过程。

2. 不同点：它借鉴了Delphi的一个特点，与COM（组件对象模型）是直接集成的，而且它是微软公司 .NET windows网络框架的主角。

###### C#与C和C++的对比

1. **C#是由C和C++衍生出来的面向对象的编程语言**。
2. 它在继承C和C++强大功能的同时去掉了一些它们的复杂特性（例如：没有宏以及不允许多重继承）。
3. C#综合了VB简单的可视化操作和C++的高运行效率，以其强大的操作能力、优雅的语法风格、创新的语言特性和便捷的面向组件编程的支持成为.NET开发的首选语言。

###### C#的适用环境

1. C#适合为**独立和嵌入式的系统编写程序**。

2. 适用于使用**复杂操作系统的大型系统**。
3. 适用于**特定应用的小型系统**。

###### 搭建C#开发环境

Microsoft Visual Studio 2010（简称VS）、微软的一个完整的开发工具集

勾选 Visual C# +Visual Basic 功能

组件**Mincrosoft.NET Framework (.NET框架)，它是开发平台的基础**，包括**公共语言运行（CLR）和。NET类库两部分**。

CLR负责管理和执行

.NET 编辑器编译产生的中间语言代码

.NET类库封装了系统底层的功能

新建项目

Visual C# ->Windows 窗体应用程序

###### 创建简单的C#应用程序

控制台应用程序、Windows窗体应用程序与WPF应用程序

|                    应用程序                    |                             功能                             |
| :--------------------------------------------: | :----------------------------------------------------------: |
|                 控制台应用程序                 |                  没有图形界面，只有字符界面                  |
|              Windows窗体应用程序               |              有图形界面，是对Windows API的封装               |
| WPF应用程序（Windows Presentation Foundation） | 应用程序也是用来做图形界面的，但WPF**不是对Windows API的直接封装，而是对DirectX的封装**，更能利用显卡，所以可以**较容易地做出酷炫界面效果** |

第一个Hello C#语句

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;		//导入命名空间
namespace 任务2-1 //自定义任务2-1命名空间
{		             // 任务2-1命名空间的开始大括号
    class Program          //自定义Program类
    {   //Program类的开始大括号
        static void Main(string[] args)	 //入口方法Main
        {	//Main的开始大括号
            Console.WriteLine("欢迎进入C#世界！");  //向屏幕输出信息
        }	//Main的结束大括号
    }// Program类的结束大括号
} //任务2-1命名空间的结束大括号
```

**不调试**:【Ctrl+F5】 快捷键，或如 图所 示执行“调试”→“开始执行 （不调试）菜单命令，这样可以不进行调试而直接运行 程序。

**调试**:F5

**停止调试**:可以按【Shift+F5】组合键

###### 第一个Windows窗口

**textBox**控件 输入框 password->passwordChar 密码输入隐藏 属性 * 号

事件

```C#
private void button1_Click(object sender， EventArgs e)
{
  MessageBox.Show(textBox1.Text+textBox2.Text+"，口令正确！欢迎您进入C#世界！");  //弹出提示框
 }
 private void button2_Click(object sender， EventArgs e)
 {
  textBox1.Text="";   //清空用户名
  textBox2.Text ="";  //清空密码
 }	
```

主方法Main的入口类Program。可双击Program.cs查看其全部代码

```C#
 static void Main()
  {
    Application.EnableVisualStyles();
 //此方法为应用程序启用可视样式，需在应用程序中创建任何控件之前调用
    Application.SetCompatibleTextRenderingDefault(false);
 //在应用程序范围内设置控件显示文本的默认方式，true表示以GDI+方式
//显示文本，false表示以GDI方式显示文本
    Application.Run(new Form1());
 //程序启动时首先加载Form1窗体
 }
```

###### 第一个WPF窗口

textbox 要设置名字 => 属性 名称

**创建** **WPF** **应用程序**

- MainWindow.xaml中存放系统自动生成的窗体和控件信息；

- MainWindow.xaml.cs中存放C#程序代码，这个文件中是用户编程常用的文件；

- App.xml和App.xml.cs文件是程序的入口。


```C#
MessageBox.Show("欢迎"+textBox1.Text+"进入WPF世界！");
```

### C#基础语法

###### 基础语言元素

标识符和保留字

- 常量、变量、类、方法等的名字，统称为标识符。以字母、下划线（_）或@开始的一个字符序列，后面可以跟字母、数字或下划线。
- **C#语言区分大小写**
- 一般情况下，**变量名首字母小写，后面各单词首字母大写**；常量、类名、方法、属性等首字母需大写

**保留字又称关键字，是指已经定义过的字符，具有专门的意义和用途，使用者不能将它们作为变量名或过程名使用。**C#语言中的保留字均用小写字母表示，若一定要用保留字作标识符，应使用@字符作为前缀

![图片1](C:\Users\Administrator\Desktop\大二下note\C#\photo\\图片1.png)

变量

变量代表了存储单元，每个变量都有一个类型。这决定了这个变量可以存储什么值。

变量必须先定义后使用

变量的声明采用如下的规则：

整个生命周期内值始终不变的量。在声明常量时，要**用到Const关键字**。常量在使用的过程中，不可以对其进行赋值的改变，否则系统会自动报错。

```
   <type>  <name>; int a;
```

常量

```
const [int/double/long/bool/string/......] <Name>;
const double PI = 3.14
```

表达式

C#中的表达式是由运算符、变量以及标点符号依据一定的法则组合创建起来的。



运算符

% 取余运算符

i++是先赋值，后进行自身的运算
++i先进行自身的运算，而后再赋值。 

赋值运算符

- 简单赋值运算符
- 复合赋值运算符

![图片2](C:\Users\Administrator\Desktop\大二下note\C#\photo\\图片2.png)

优先级

先乘除、后加减，有括号先算括号里面的
先运算再赋值

特殊运算符

|           运算符           | 作用                                                         |
| :------------------------: | ------------------------------------------------------------ |
|        点运算符“．”        | 点运算符指定类型或命名空间的成员。例如，**点运算符用于访问.NET Framework 类库中的特定方法**：System.Console.WriteLine("hello"); |
|       索引运算符“[]”       | **用于数组、索引器**，表示按[ ]内指定的索引去访问数组或索引器中的相应元素的内容。 |
|      转换运算符“( )”       | 除用于指定表达式中的运算顺序外，还用于**指定强制类型转换**   |
| checked 和unchecked 运算符 | 如果将一个代码块标记为checked，CLR就会执行溢出检查，若发生溢出，就抛出异常；如果要禁止溢出检查，可以把代码标记为unchecked。 |
|          is运算符          | 用于**检查对象是否与给定类型兼容**                           |
|          as运算符          | as运算符用于执行引用类型的显式类型转换，若不成功则返回null。常被用在以下形式的表达式中：**expression as type** **此表达式等效于****expression is type ? (type)expression : (type)null** |
|            new             | new运算符用于创建对象和调用构造函数： class MyClass = new Class() |
|           typeof           | typeof运算符用于获得系统原型对象的类型，即返回一个表示特定类型的System.Type对象。例如，typeof(int) 表示返回System.Int32类型的Type对象。 |



###### 基本编码规则

①    每条语句以**分号“;”结尾**（注意：需要在英文状态下输入）。
②    尽量每行只放置一条语句。
③    编写语句块时垂直对齐左括号和右括号，或者使用倾斜样式，即左括号出现在行尾，右括号出现在行首。
④    对同一级别的语句建立标准的缩进大小（如四个空格），并在整个文件中一致地使用此标准。C#语言在编译时将**忽略空行和缩进**。
⑤    为语句添加必要的注释，增加代码的可读性。

注释

```
//
/*

*/
/// XML注释或文档注释方式
```



###### 数据类型

数据类型

**内置类型和构造类型**

![图片3](C:\Users\Administrator\Desktop\大二下note\C#\photo\图片3.png)

值类型与引用类型

值类型变量存放的是数据本身
引用类型变量存储的是对数据的引用，即数据的地址。

![图片4](C:\Users\Administrator\Desktop\大二下note\C#\photo\图片4.png)

数据类型的装换

显式装换

将高精度数据转换为低精度数据，必须使用强制转换表达式将原类型转化为目标类型，这种数据类型转换方式称为显式转换，又叫强制转换

![图片5](C:\Users\Administrator\Desktop\大二下note\C#\photo\图片5.png)

三种显式转换方式

1. 通过圆括号

   ```
   (目标类型)  <表达式>
   long  i = 45;
   int j = (int) i;
   ```

2. 通过Convert

   Convert类位于System命名空间，可以通过“Convert.方法名(参数)”形式来使用，用于将一个值类型转换成另一种类型。

   ![图片6](C:\Users\Administrator\Desktop\大二下note\C#\photo\图片6.png)

3.  通过数据类型自身的Parse方法

   ​    在.NET Framework类库的System命名空间里，任何系统预定义的数据类型都有其同名的类，调用其Parse()方法就可以将给定的内容转换为相应的类类型数据。

   ```
   int32.Parse("数字字符串")或int.Parse("数字字符串")
   即表示将数字字符串转换为32位有符号整数
   ```

4. ToString()方法

   ```
   int i = 100;
   String str = i.Tostring();
   ```

   i.Tostring()和Convert.ToString的区别如下：当返回的数据类型中有可能出现null值时：
   若调用Tostring方法，会返回NullReferenceException异常；
   若使用Convert.ToString()方法，不会抛出异常而是返回空字符串。

   

隐式装换

**系统默认的不必加以说明就可以进行的转换，转换规则如下：**

 ①  字符类型可以隐式转换为整型或浮点型，但其他类型不能隐式转换为字符类型。

 ②  低精度的类型可以隐式转换成高精度的类型，反f之则不行。

 ③  浮点型和decimal类型之间不能进行隐式转换，而只能进行显式转换。



绘制梦幻曲线

```C#
private void button1_Click(object sender, EventArgs e)
{
   float A, E, M_PI, x1, y1, x2, y2;
   int D, i;
   D = 100;
   M_PI = 3.1415926535897932f;  //圆周率，以f结尾表示以float类型存储数据
   for (i = 0; i < 720; i++)              //绘制图形
   {
     A = i * M_PI / 360;
     E = (float)(D * (1 + System.Math.Sin(4 * A)));
     // (float)用于将数据进行强制数据类型转换
     x1 = (float)(320 + E * System.Math.Cos(A));	
     x2 = (float)(320 + E * System.Math.Cos(A + M_PI / 5));
     y1 = (float)(240 + E * System.Math.Sin(A));
     y2 = (float)(240 + E * System.Math.Sin(A + M_PI / 5));
     Pen pen = Pens.Red;                                 //设置画笔颜色为红色
     Graphics gdi = this.CreateGraphics();    //生成Graphics对象
     gdi.DrawLine(pen,x1,y1,x2,y2);
     //使用DrawLine方法在点(x1,y1)和点(x2,y2)间画一条直线
  }
}
```



###### 语句

###### 条件语句



###### 选择语句

if语句

```
if(){}
```

if....esle语句

```

```

switch语句

```

```



###### 循环语句

while语句

```
while（boolean expression）
{
   embeded-statement;
}
```

do.....while语句

```
do
{
      embeded-statement;
} while(boolean expression)；
```

for语句

```
for（initializer;condition;iterator）
{
statement;
}
```

Foreach语句是在C#中新引入的，C和C++中没有这个语句，它表示收集一个集合中的各元素，并针对各个元素执行内嵌语句。

```

```

break和continue

```

```

Goto语句

```

```

return语句

```

```





### 方法

### 程序调试与异常处理

### 类与对象

### 继承与多态

### 抽象类与接口

### 数组与集合

### 文件处理技术

### 委托与事件

### 泛型

### 数据处理







