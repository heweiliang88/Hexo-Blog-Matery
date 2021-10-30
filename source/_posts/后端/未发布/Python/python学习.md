---
title: Python学习
categories:
- Python
tags:
- python学习
abbrlink: 62540
---

# Python3.0学习

## Python基础篇

#### 概念

- python 是一种解释性、面向对象、动态数据类型的高级程序设计语言

- 1989年底发明，Gudio van Rossum ，第一个公开发行版本1991年

- 2020.1.1，停止python2 的更新，python2.7被确定为最后一个python2.x版本



CMD命令

python -v

python

编译 python 文件名.py

输出

```python
print("Hello Python!!!");
```

#### 安装

Windows环境变量

cmd检查

python -v

环境搭建

两种方式

方法一

path=%path%;目录

方法二

#### 语法

##### 基本语法

###### 编程类型

- 交互式编程

	交互式编程不需要创建脚本文件，是通过Python解析器的交互模式进来编写代码。

- 脚本式编程

	通过脚本参数调用解析器开始执行脚本，直到脚本执行完毕。当脚本执行完成后，解析器不再有效

###### 行与缩进

python最具特色的就是使用缩进来表示代码块，不需要使用大括号 **{}** 。

缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。

##### 多行语句

Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠(\ \)来实现多行语句

```python
total = item_one + \
        item_two + \
        item_three
```

在 [], {}, 或 () 中的多行语句，不需要使用反斜杠(\)，例如：

```python
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

###### 注释

```python
# 单行注释

'''
多行注释
'''

"""
多行注释
"""
```

###### 中文编码

Python中默认的编码格式是 ASCII 格式，在没修改编码格式时无法正确打印汉字，所以在读取中文时会报错。

```python
SyntaxError: Non-ASCII character '\xe4' in file test.py on line 2, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details
```

解决方法为只要在文件开头加入 **# -\*- coding: UTF-8 -\*-** 或者 **# coding=utf-8** 就行了

**注意：** **# coding=utf-8** *的* **=** *号两边不要空格。*

**注意：***Python3.X 源码文件默认使用utf-8编码，所以可以正常解析中文，无需指定 UTF-8 编码。*

Pycharm 设置步骤：

- 进入 **file > Settings**，在输入框搜索 **encoding**。
- 找到 **Editor > File encodings**，将 **IDE Encoding** 和 **Project Encoding** 设置为utf-8。

所有字符串都是unicode字符串

标识符和保留字

标识符

第一个字符必须是字母表中或下划线 _

大小写敏感

标识符地其他的部分由字母、数字和下划线组成。 

保留字

```
import keyword
print(keyword.kwlist)
```





###### 运算符

##### 语句

循环语句

for()

while()

do() while{

}

条件语句

if()

if(){}else{}

if(){}else if(){}else if{} else{}

##### 基本数据类型



Python 中的变量不需要声明。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。

在 Python 中，变量就是变量，它没有类型，我们所说的"类型"是变量所指的内存中对象的类型。

等号（=）用来给变量赋值。

等号（=）运算符左边是一个变量名,等号（=）运算符右边是存储在变量中的值。例如：

##### 多个变量赋值





Python允许你同时为多个变量赋值。例如：

```
a = b = c = 1
```

以上实例，创建一个整型对象，值为 1，从后向前赋值，三个变量被赋予相同的数值。

您也可以为多个对象指定多个变量。例如：

```
a, b, c = 1, 2, "runoob"
```



Python3 的六个标准数据类型中：

- **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）；
- **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）。



1. Number 数字

	内置的type()函数可以查询变量所指的对象类型

	print（type(a)）

	isinstance(a,int) 判断与后面的类型是不是相同

	- type()不会认为子类是一种父类类型。
	- isinstance()会认为子类是一种父类类型。

- int(整数)

- 只有一种整数类型int,表示为长整型i，没有python2中的Long

- bool(布尔)

- True或False

- float(浮点数)

- complex(复数)

- Python还支持复数，复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型

- 1+2j、1.1+2.2j

- 1、Python可以同时为多个变量赋值，如a, b = 1, 2。

- 2、一个变量可以通过赋值指向不同类型的对象。

- 3、数值的除法包含两个运算符：**/** 返回一个浮点数，**//** 返回一个整数。

- 4、在混合计算时，Python会把整型转换成为浮点数。

	当你指定一个值时，Number 对象就会被创建：

	```
	var1 = 1
	var2 = 10
	```

	您也可以使用del语句删除一些对象引用。

	del语句的语法是：

	```
	del var1[,var2[,var3[....,varN]]]
	```

	您可以通过使用del语句删除单个或多个对象。例如：

	```
	del var
	del var_a, var_b
	```

	\>>> 2 / 4  # 除法，得到一个浮点数 0.5 >>> 2 // 4 # 除法，得到一个整数 0 >>> 17 % 3 # 取余  2 >>> 2 ** 5 # 乘方 32

2. 字符串String(不能被改变)

- python中单引号和双引号使用完全相同。

- 加号 **+** 是字符串的连接符， 星号 ***** 表示复制当前字符串，与之结合的数字为复制的次数。实例如下：

- 使用三引号('''或""")可以指定一个多行字符串。

- 转义符 ' \ '

- 反斜杠可以用来转义，使用r可以让反斜杠不发生转义。。 如 r"this is a line with \n" 则\n会显示，并不是换行。

- 按字面意义级联字符串，如"this " "is " "string"会被自动转换为this is string。

- 字符串可以用 + 运算符连接在一起，用 * 运算符重复。

- Python 中的字符串有两种索引方式，从左往右以 0 开始，从右往左以 -1 开始。

- 索引值以 0 为开始值，-1 为从末尾的开始位置。

	```
	print(str[0:-2])  # 输出第一个到倒数第二个的所有字符
	```

- Python中的字符串不能改变。

- Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。

- 字符串的截取的语法格式如下：**变量[头下标:尾下标:步长]**

	```
	print(str[2:])  # 输出从第三个开始后的所有字符
	```

	```
	print(str[2:5])  # 输出从第三个开始到第五个的字符
	```

	```
	#可以将字符串输出任意次数
	print(str * 2)  # 输出字符串两次列表
	```

3. 字典(Dictionary) {}

	字典（dictionary）是python中另一个非常有用的内置数据类型

	列表是有序的对象集合，字典是无序的对象集合。两者之间的区别在于：字典当中的元素是通过键来存取的，而不是通过偏移存取。

	字典是一种映射类型，字典用 **{ }** 标识，它是一个无序的 **键(key) : 值(value)** 的集合。

	键(key)必须使用不可变类型。

	```
	tinydict = {'name': 'runoob','code':1, 'site': 'www.runoob.com'}
	```

	- 1、字典是一种映射类型，它的元素是键值对。

	- 2、字典的关键字必须为不可变类型，且不能重复。

	- 3、创建空字典使用 **{ }**。

		```
		dict = {}
		dict['one'] = "1 - 菜鸟教程"
		dict[2]     = "2 - 菜鸟工具"
		 
		tinydict = {'name': 'runoob','code':1, 'site': 'www.runoob.com'}
		 
		 
		print (dict['one'])       # 输出键为 'one' 的值
		print (dict[2])           # 输出键为 2 的值
		print (tinydict)          # 输出完整的字典
		print (tinydict.keys())   # 输出所有键
		print (tinydict.values()) # 输出所有值
		```

		构造函数 dict() 可以直接从键值对序列中构建字典如下：

		## 实例

		```
		>>>dict([('Runoob', 1), ('Google', 2), ('Taobao', 3)])
		{'Taobao': 3, 'Runoob': 1, 'Google': 2}
		 
		>>> {x: x**2 for x in (2, 4, 6)}
		{2: 4, 4: 16, 6: 36}
		 
		>>> dict(Runoob=1, Google=2, Taobao=3)
		{'Runoob': 1, 'Google': 2, 'Taobao': 3}
		```

		

4. 集合（Set） { } set()函数创建

	集合（Set）是由一个或者数个形态各异的大小整体形成的，构成集合的事物或对象称作元素或是成员。

	空集合必须用set(),而不是{ }，因为{ } 是用来创建一个空字典

	创建格式

	parme = { value01,value02,.....}

	或者

	set(value)

	```python
	# set可以进行集合运算
	a = set('abracadabra')
	b = set('alacazam')
	 
	print(a)
	 
	print(a - b)     # a 和 b 的差集
	 
	print(a | b)     # a 和 b 的并集
	 
	print(a & b)     # a 和 b 的交集
	 
	print(a ^ b)     # a 和 b 中不同时存在的元素
	```

	

	

	

	

5. 列表(List) 用[] 号

	List（列表） 是 Python 中使用最频繁的数据类型。

	列表可以完成大多数集合类的数据结构实现。列表中元素的类型可以不相同，它支持数字，字符串甚至可以包含列表（所谓嵌套）。

	列表是写在方括号 **[]** 之间、用逗号分隔开的元素列表。

	和字符串一样，列表同样可以被索引和截取，列表被截取后返回一个包含所需元素的新列表。

	列表截取的语法格式如下：

	```
	变量[头下标:尾下标] #尾标没有取到
	```

	索引值以 0 为开始值，-1 为从末尾的开始位置。

	加号 **+** 是列表连接运算符，星号 ***** 是重复操作。如下实例：

	与Python字符串不一样的是，列表中的元素是可以改变的：

	```
	a[2:5] = [13,14,15]
	a[2:5] = []
	```

	**注意：**

	- 1、List写在方括号之间，元素用逗号隔开。

	- 2、和字符串一样，list可以被索引和切片。

	- 3、List可以使用+操作符进行拼接。

	- 4、List中的元素是可以改变的。

	- Python 列表截取可以接收第三个参数，参数作用是截取的步长，以下实例在索引 1 到索引 4 的位置并设置为步长为 2（间隔一个位置）来截取字符串：

	- 如果第三个参数为负数表示逆向读取，

	- 如果第三个参数为负数表示逆向读取，以下实例用于翻转字符串：

		```
		实例
		
		**def** reverseWords(input):
		
		  \# 通过空格将字符串分隔符，把各个单词分隔为列表
		  inputWords = input.split(" ")
		
		  \# 翻转字符串
		  \# 假设列表 list = [1,2,3,4],  
		  \# list[0]=1, list[1]=2 ，而 -1 表示最后一个元素 list[-1]=4 ( 与 list[3]=4 一样)
		  \# inputWords[-1::-1] 有三个参数
		  \# 第一个参数 -1 表示最后一个元素
		  \# 第二个参数为空，表示移动到列表末尾
		  \# 第三个参数为步长，-1 表示逆向
		  inputWords=inputWords[-1::-1]
		
		  \# 重新组合字符串
		  output = ' '.join(inputWords)
		
		  **return** output
		
		**if** __name__ == "__main__":
		  input = 'I like runoob'
		  rw = reverseWords(input)
		  **print**(rw)
		```

		

6. 元组(Tuple) 用（）号

	元组（tuple）与列表类似，不同之处在于元组的元素不能修改。元组写在小括号 **()** 里，元素之间用逗号隔开。

	元组中的元素类型也可以不相同：

	元组与字符串类似，可以被索引且下标索引从0开始，-1 为从末尾开始的位置。也可以进行截取（看上面，这里不再赘述）。

	其实，可以把字符串看作一种特殊的元组。

	tup[0] = 11  # 修改元组元素的操作是非法的

	虽然tuple的元素不可改变，但它可以包含可变的对象，比如list列表。

	构造包含 0 个或 1 个元素的元组比较特殊，所以有一些额外的语法规则：

	```
	tup2 = (20,) # 一个元素，需要在元素后添加逗号
	```

	```
	tup1 = ()    # 空元组
	tup2 = (20,) # 一个元素，需要在元素后添加逗号
	```

	string、list 和 tuple 都属于 sequence（序列）。

	**注意：**

	- 1、与字符串一样，元组的元素不能修改。
	- 2、元组也可以被索引和切片，方法一样。
	- 3、注意构造包含 0 或 1 个元素的元组的特殊语法规则。
	- 4、元组也可以使用+操作符进行拼接。

python结束不用分号

数据类型转换

## Python数据类型转换

有时候，我们需要对数据内置的类型进行转换，数据类型的转换，你只需要将数据类型作为函数名即可。

以下几个内置的函数可以执行数据类型之间的转换。这些函数返回一个新的对象，表示转换的值。

| 函数                                                         | 描述                                                |
| :----------------------------------------------------------- | :-------------------------------------------------- |
| [int(x [,base\])](https://www.runoob.com/python3/python-func-int.html) | 将x转换为一个整数                                   |
| [float(x)](https://www.runoob.com/python3/python-func-float.html) | 将x转换到一个浮点数                                 |
| [complex(real [,imag\])](https://www.runoob.com/python3/python-func-complex.html) | 创建一个复数                                        |
| [str(x)](https://www.runoob.com/python3/python-func-str.html) | 将对象 x 转换为字符串                               |
| [repr(x)](https://www.runoob.com/python3/python-func-repr.html) | 将对象 x 转换为表达式字符串                         |
| [eval(str)](https://www.runoob.com/python3/python-func-eval.html) | 用来计算在字符串中的有效Python表达式,并返回一个对象 |
| [tuple(s)](https://www.runoob.com/python3/python3-func-tuple.html) | 将序列 s 转换为一个元组                             |
| [list(s)](https://www.runoob.com/python3/python3-att-list-list.html) | 将序列 s 转换为一个列表                             |
| [set(s)](https://www.runoob.com/python3/python-func-set.html) | 转换为可变集合                                      |
| [dict(d)](https://www.runoob.com/python3/python-func-dict.html) | 创建一个字典。d 必须是一个 (key, value)元组序列。   |
| [frozenset(s)](https://www.runoob.com/python3/python-func-frozenset.html) | 转换为不可变集合                                    |
| [chr(x)](https://www.runoob.com/python3/python-func-chr.html) | 将一个整数转换为一个字符                            |
| [ord(x)](https://www.runoob.com/python3/python-func-ord.html) | 将一个字符转换为它的整数值                          |
| [hex(x)](https://www.runoob.com/python3/python-func-hex.html) | 将一个整数转换为一个十六进制字符串                  |
| [oct(x)](https://www.runoob.com/python3/python-func-oct.html) | 将一个整数转换为一个八进制字符串                    |

##### 空行

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

空行与代码缩进不同，空行并不是Python语法的一部分。书写时不插入空行，Python解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

**记住：**空行也是程序代码的一部分。

##### 同一行显示多条语句

python可以在同一行中使用多条语句，语句之间使用分号; 分割

import sys; x = "runoob"; sys.stdout.write(x+"\n")

##### 多个语句构成代码组

缩进相同的一组语句构成一个代码块，就是代码组

##### 命令行参数

很多程序可以执行一些操作来查看一些基本信息

python -h 可以使用来查看各参数帮助信息

##### import与from...import

在python中用import或者from...import来导入相应的模块 函数

将整个模块(somemodule)导入，格式为： **import somemodule**

从某个模块中导入某个函数,格式为： **from somemodule import somefunction**

从某个模块中导入多个函数,格式为： **from somemodule import firstfunc, secondfunc, thirdfunc**

将某个模块中的全部函数导入，格式为： **from somemodule import  ***

路径

```python
import sys
# 路径
for i in sys.argv:
	print(i)
#
print(sys.path)
```

```
## 导入 sys 模块
print ('命令行参数为:')
for i in sys.argv:    
print (i) print ('\n python 路径为',sys.path)
```



```
## 导入 sys 模块的 argv,path 成员

from sys import argv,path  #  导入特定的成员  
print('================python from import===================================') 
print('path:',path) # 因为已经导入path成员，所以此处引用时不需要加sys.path


```



##### 解释器



##### 日期和时间

##### 函数

##### 模块

##### 文件I/O







## Python高级篇

面向对象

正则表达式

CGI

MySQL

网络编程

SMATP

多线程

XML解析

GUI编程

IDE

JSON

# 基础知识

## 概念

- python 是一种解释性、面向对象、动态数据类型的高级程序设计语言
- 1989年底发明，Gudio van Rossum ，第一个公开发行版本1991年
- 2020.1.1，停止python2 的更新，python2.7被确定为最后一个python2.x版本
- python 文件后缀`py`

## 安装

python版本

```cmd
py // python
```

设置环境变量

- 设置path的环境变量为python所在目录，而不是bin 目录

## Python 2.0  VS 3.0

python 3.0

- print 函数
- Unicode

## 彩蛋

```python
import this
```

## 语法

### 编程类型

- 交互式编程

	交互式编程不需要创建脚本文件，是通过Python解析器的交互模式进来编写代码。

- 脚本式编程

	通过脚本参数调用解析器开始执行脚本，直到脚本执行完毕。当脚本执行完成后，解析器不再有效

行与缩进

python最具特色的就是使用缩进来表示代码块，不需要使用大括号 **{}** 。

缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。

多行语句

Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠(\ \)来实现多行语句

```python
total = item_one + \
        item_two + \
        item_three
```

在 [], {}, 或 () 中的多行语句，不需要使用反斜杠(\)，例如：

```python
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

### 注释

```python
# 单行注释
'''
多行注释
'''
"""
多行注释
"""
```

###### 中文编码

Python中默认的编码格式是 ASCII 格式，在没修改编码格式时无法正确打印汉字，所以在读取中文时会报错。

```python
SyntaxError: Non-ASCII character '\xe4' in file test.py on line 2, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details
```

解决方法为只要在文件开头加入 **# -\*- coding: UTF-8 -\*-** 或者 **# coding=utf-8** 就行了

**注意：** **# coding=utf-8** *的* **=** *号两边不要空格。*

**注意：***Python3.X 源码文件默认使用utf-8编码，所以可以正常解析中文，无需指定 UTF-8 编码。*

Pycharm 设置步骤：

- 进入 **file > Settings**，在输入框搜索 **encoding**。
- 找到 **Editor > File encodings**，将 **IDE Encoding** 和 **Project Encoding** 设置为utf-8。

所有字符串都是unicode字符串

### 标识符和保留字

标识符

第一个字符必须是字母表中或下划线 _

大小写敏感

标识符地其他的部分由字母、数字和下划线组成。 

保留字

```
import keyword
print(keyword.kwlist)
```

### 运算符



### 语句



### 流程控制

顺序结构

选择结构

```python
if <表达式>:
    <语句>
    
if <表达式>:
    <语句>
else:
    <语句>
    
if <表达式>:
    <语句>    
else if <表达式>: 
    <语句>    
else if <表达式>: 
    <语句>
else:
```

循环语句

- pass：不做任何事情，空占位符，空语句
- break
- continue

```python
for <表达式>:
    <语句>
    
for <变量> in <序列>:
    <语句>
# 有限次遍历
for i in range(n): 
# 遍历文件    
for line in myfile:
# 遍历字符串
forch i in mystring:
# 遍历列表
for i in mylist:

while <表达式>:
    <语句>
    
# do <表达式>: while
```

### 变量

##### 多个变量赋值

Python 中的变量不需要声明。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。

在 Python 中，变量就是变量，它没有类型，我们所说的"类型"是变量所指的内存中对象的类型。

等号（=）用来给变量赋值。

等号（=）运算符左边是一个变量名,等号（=）运算符右边是存储在变量中的值

Python允许你同时为多个变量赋值。例如：

```
a = b = c = 1
```

以上实例，创建一个整型对象，值为 1，从后向前赋值，三个变量被赋予相同的数值。

您也可以为多个对象指定多个变量。例如：

```
a, b, c = 1, 2, "runoob"
```

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

空行与代码缩进不同，空行并不是Python语法的一部分。书写时不插入空行，Python解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

**记住：**空行也是程序代码的一部分。

##### 同一行显示多条语句

python可以在同一行中使用多条语句，语句之间使用分号; 分割

import sys; x = "runoob"; sys.stdout.write(x+"\n")

##### 多个语句构成代码组

缩进相同的一组语句构成一个代码块，就是代码组

##### 命令行参数

很多程序可以执行一些操作来查看一些基本信息

python -h 可以使用来查看各参数帮助信息

# 高级知识

## 数据类型

> Python3 的六个标准数据类型中：
>
> - **不可变数据（3 个）：**Number（数字）[整数、浮点]、String（字符串）、Tuple（元组）
> - **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）

### 基本数据类型：Number  数字 `整数+浮点`

#### 整数 `int`



#### 浮点 `float`



### 组合数据类型：`列表+元组+字典`

> 组合数据类型：
>
> - 序列类型：每个元素都分配数字、位置或者索引，``字符串、列表、元组``
> - 映射类型：用键值对表示数据，``字典``
> - 集合类型：元素是无序，不允许相同的元素存在，`集合`

#### 字符串`string`

##### 字符串表示

```python
# 单引号、双引号、三引号str1 = 'Hello str!!!'str2 = "Hello str2!!!"str3 = """Hello str3!!!"""
```

##### 转义字符

- `\\(续行符)、\‘(单引号)、\"(双引号)`
- `\a(响铃)、\b(退格)、\e(转义)、\000 空`
- `\n(换行)、\v(纵行制表符)、\t(横向制表符)、\r(换行)、\f(换页)`
- `\oyy(八进制)、\xyy(十六进制)、\other(其他的字符以普通格式输出)`

##### 格式化字符串

- 使用格式化操作符`%`
	- 字符串模板参数
	- `*` 宽度或者小数点精度、`m.n.` m最小总宽度，n小数点后位数
	- 字符串格式化控制符
	- `%c（字符）、%s（字符串）、%d（整数）、%u（无符号整数）、%f （浮点数字）`
	- `%o（八进制）、%x\%X（十六进制）、%e、%E、%g、%G、%p`

```python
print('%c %s %d %f'%('A','ABC',200,20.8))
```

- `str.format()`方法：str 称为模板字符串，`{}` 占位符
	- 位置参数匹配
	- 使用键值对的关键字参数匹配
	- 使用序列的索引作为参数匹配
- 模板字符串str的格式控制 `[[fill] align] [sign] [width] [,] [.precision] [type]`
	- fill：可选参数，空白符填充的字符
	- align：
	- sign：
	- width：
	- precision：
	- type：可选参数、指定格式化的类型

```python
# 位置参数匹配print('{0} ,{0} ,{1}, {2}'.format("Hello",1024,'world'))# 使用键值对的关键字参数匹配print('{name} {year} {age}'.format(name="Msg",age="30",year="2020"))# 使用序列的索引作为参数匹配student = ["Jack", '20'] school = ['YYUU', 'YYJD']print("{1[0]} {0[0]} {1[1]}".format(school,student))msg = ['hwl', 21]print('{0[0]} {0[1]}'.format(msg))print('{:* > 10}'.format('3.19'))  # 宽度10位，右对齐print('{:* < 10}'.format('3.19'))  # 宽度10位，左对齐
```

##### 字符串的比较

- 单字符字符串： `==`
- 多字符字符串：`‘’ is ‘’`、 ` is not`

```python
print('abc' == 'abc') // Trueprint(id('abc') == id('abc')) // Trueprint('abc' < 'ab') // Falseprint('hello' is not 'hello world') // False
```

##### 字符串输入/输出

```python
username = input("请输入用户名") #  输入
print(username)  # 输出
```

##### 字符串运算

| 操作符                 | 描述                                                         |
| ---------------------- | ------------------------------------------------------------ |
| `+(连接符)、*(重复符)` | 字符串连接、重复输出字符串                                   |
| `[]、[:]`              | 通过索引获取字符串中的字符、截取字符串中的一部分，遵循左闭右开原则 |
| `in、not in`           |                                                              |
| `r/R`                  | 原始字符串，替代转义字符表示的特殊字符                       |

```python
str = 'Hello Message'
print(str * 5 + 'Python')
print(str[2])
print(str[2:7])
print(r'\n')
print(R'\n')
```

##### 字符串方法

- 字符串长度 `len()`
- 转换：`capitalize()` 首字母大写  、``swapcase()` 翻转大小写  `upper()` 全大写、`lower` 全小写
- 查找：`count(str,beg=0,end=len(string))` str 出现次数、`start\endsWith(obj,beg=0,end=len(string))` 以结尾、`find(str,beg=0,end=len(string))` 检测str是否包含在string、`index(str,beg=0,end=len(string))`
- 替换：`replace()`
- 判断：`isalnum()`（都是字母或数字）、`isalpha()`（都是数字）、`idecimal`（只包含十进制数字）、`isdigit`(只包含数字)、`isslower`（小写）、`isnumeric`(只包含数字字符)、`isspace`（空格）、`istitle`、`isupper`（大写）
- 特殊：、`max(str)\min(str) 最大\最小字母`、返回字符串中最大的值
	- 去空格： `lstrip()`去左边空格、`rstrip()`去右边空格、`strip()`去空格（去两边的空格）
	- 分配符`split()`
	- `find()`
	- `rjust()`
- 格式化：`format()`格式化、`join(req)` 分隔符、`center(width)` 原字符居中、`expandtabs(tabsize=8)` tab符号转空格，默认空格数8个
- 编码格式：`decode(encoding='UTF-8',error='strict'` 指定编码解码、`encode(encoding='UTF-8',error='strict')` 指定编码编码
- `partition(str)`
- `translate(str,del="")` str给出的表（包含256字符） 转换string 字符要管理掉的字符放在del参数中

#### 列表`list`

列表可以完成大多数集合类的数据结构实现。列表中元素的类型可以不相同，它支持数字，字符串甚至可以包含列表（所谓嵌套），和字符串一样，列表同样可以被索引和截取，列表被截取后返回一个包含所需元素的新列表。

- List（列表） 是 Python 中使用最频繁的数据类型。
- List写在方括号之间，元素用逗号隔开。
- 索引值以 0 为开始值，-1 为从末尾的开始位置。
- 加号 `+` 是列表连接运算符（进行拼接），星号 `* `是重复操作
- 和字符串一样，list可以被索引和切片
- List中的元素是可以改变的
- Python 列表截取可以接收第三个参数，参数作用是截取的步长，在索引 1 到索引 4 的位置并设置为步长为 2（间隔一个位置）来截取字符串

列表截取的语法格式如下：

```python
变量[头下标:尾下标:步长] # 尾标没有取到 步长 = -1 表示逆向  # 如果第三个参数为负数表示逆向读取
```

```python
List = [1,2,3,4,5]List2 = ['a','b','c','d','e']print("list",list)# 访问指定下标的元素的值,下标print("list[1]",list[1])print(list[1:5:2])# 删除列表元素del list[3]# 修改列表元素list[1] = 100# 读取列表元素print(list)  # 输出全部元素 == list[0:]list[2]list[-2] # 倒数第二个元素list[1:] # 从第二个元素开始截取# 遍历列表for item in list 	print(item)lst = list(range(2,15,2))i = 0result = []while i < len(lst):    result.append(lst[i])    i += 1print(result)     # 翻转字符串def reverseWords(input):    # 通过空格将字符串分隔符，把各个单词分隔为列表    inputWords = input.split(" ")    # 假设列表 list = [1,2,3,4],      # list[0]=1, list[1]=2 ，而 -1 表示最后一个元素 list[-1]=4 ( 与 list[3]=4 一样)    # inputWords[-1::-1] 有三个参数    # 第一个参数 -1 表示最后一个元素    # 第二个参数为空，表示移动到列表末尾    # 第三个参数为步长，-1 表示逆向    inputWords=inputWords[-1::-1]    # 重新组合字符串    output = ' '.join(inputWords)    return outputif __name__ == "__main__":    input = '输入一段英文文字'    rw = reverseWords(input)    print(rw)
```

列表方法

| 操作符                   | 描述                      |
| ------------------------ | ------------------------- |
| `del`                    | 删除列表元素`del list[3]` |
| `cmp(list1,list2)`       | 比较两个列表的元素        |
| `len(list)`              | 列表元素个数              |
| `max(list)`、`min(list)` | 最大值、最小值            |
| `list(seq)`              | 元组转换为列表            |
| `list.append(obj)`       | 列表末尾添加新的对象      |
| `list.count(obj)`        | 统计某个元素出现的次数    |
| `list.extend(seq)`       | 用新列表扩展旧列表        |
| `list.index(obj)`        | 值找索引                  |
| `list.insert(index.obj)` | 对象插入列表              |
| `list.pop(obj=list[-1])` | 移除列表的最后一个元素    |
| `list.remove(obj)`       | 移除指定的值              |
| `list.reverse()`         | 反转                      |
| `list.sort([func])`      | 排序                      |

#### 元组 `tuple`

元组(元素类型可以不相同)是包含0个或多个元素的不可变序列类型，元组生成后是固定的，其中任意类型都不能憋替换或删除。元组和列表类似，不同之处在于元组不能`替换和删除` 元组用`()`、列表用`[]`

- 元组与字符串类似，可以被索引且下标索引从0开始，-1 为从末尾开始的位置。也可以进行截取。可以把字符串看作一种特殊的元组。与字符串一样，元组的元素不能修改。

- 虽然tuple的元素不可改变，但它可以包含可变的对象，比如list列表。

- 元组也可以被索引和切片，方法一样。

元组运算符

- `len()` 个数
- `+` 连接
- `*` 复制
- `in ` 元素是否存在
- `迭代 for x in (1,2,3): print x` 

元组 <==> 列表

- tuple(lst)
- list(top)

```python
# 创建一个空元组
tup1 = ()    # 空元组
tup[0] = 11  # 修改元组元素的操作是非法的
tup2 = (20,23) # 一个元素，需要在元素后添加逗号

print(tup1)
# 删除元组
del tup1

# 修改元组 元组中的值是不允许修改的

# 元组与列表转换
tup = (1,2,4)
lst = list(tup)
tup = tuple(lst)
```

#### 字典`dict`

- 字典（dictionary）用 `{ }`标识，是python中另一个非常有用的内置数据类型，是一种映射类型，它是一个无序的 **键(key) : 值(value)** 的集合，字典的关键字必须为不可变类型，且不能重复。键(key)必须使用不可变类型。

- 列表是有序的对象集合，字典是无序的对象集合。两者之间的区别在于：字典当中的元素是通过键来存取的，而不是通过偏移存取。

```python
tinydict = {'name': 'web','code': 400, 'site': 'www.web.com'}
```

字典常用函数

| 操作符                                    | 描述                                                      |
| ----------------------------------------- | --------------------------------------------------------- |
| `dict.keys()、dict.values()、dict.item()` | 返回所有的键信息、值信息、键值对                          |
| `dict.get(key,default)`                   | 键存在则返回相应值，否则返回默认值                        |
| `dict.pop(key,default)`                   | 键存在则返回相应值，同时删除键值对，否则返回默认值        |
| `dict.popitem()`                          | 随机从字典中取出一个键值对，以元组（key,value）的形式返回 |
| `del dict[key]`                           | 删除字典中某个键值对                                      |
| `dict.clear()`                            | 删除所有的键值                                            |
| `dict.copy()`                             | 复制字典                                                  |
| `dict,update(dict2)`                      | 将字典中的值更新到另一个字典中                            |

```python
# 创建字典dict = {}dict = dirct({'键':'值','键':'值'})
```

```python
dict = {'name':'message','website':'hello','site': 'guangzhou'} d1 = dirct({'id':19,'name','hel','city';'guangdong'})dict['name'] = "Hello"print (dict['one'])       # 输出键为 'one' 的值print (dict[2])           # 输出键为 2 的值print (tinydict)          # 输出完整的字典print (tinydict.keys())   # 输出所有键print (tinydict.values()) # 输出所有值d1 = dirct({'id':19,'name':'hel','city';'guangdong'})# 查找与反向查找字典元素d1['id']d1['name']# 遍历字典for key in d1.keys():    print(key,d1[key])# 添加和修改字典元素d1['id'] = '132'd1['email'] = 'python@163.com'# 检索字典元素if 'id' in d1:    print('键 id 存在')else:    print('键 id 不存在')
```

#### 集合`Set`

- 创建集合
- 集合（Set） { } set()函数创建

- 集合（Set）是由一个或者数个形态各异的大小整体形成的，构成集合的事物或对象称作元素或是成员。

- 空集合必须用set(),而不是{ }，因为{ } 是用来创建一个空字典


```python
S = set('value01','value02')
```

集合运算

| 函数                                            | 描述                                           |
| ----------------------------------------------- | ---------------------------------------------- |
| `S.copy()`                                      | 复制集合                                       |
| `S.pop()`                                       | 随机返回S中的一个元素，并在集合中删除该元素。  |
| `S.isdisjoint(T)`                               | 判断集合是否存在相同元素，没有相同元素返回True |
| `len(S)`                                        | 元素个数                                       |
| `S & T 或 S.intersaction(T)`                    | 交集                                           |
| `S | T 或 S.union(T)`                           | 并集                                           |
| `S - T 或 S.difference(T)`                      | 差集                                           |
| `S ^ T 或 S.symmetric _ difference _ update(T)` | 补集                                           |
| `S <= T 或 S.issubset(T)`                       | 子集测试                                       |
| `S >= T 或 S.isuperset(T) `                     | 超集测试                                       |

```python
# 集合创建
a = set('python')
print(a)

# 删除集合元素 
# remove(key) 删除元素，元素不在报错
# discard(key) 删除元素，元素不在不会报错
# clear() 删除所有元素
a = set(['y,'python','b','o'])
a.remove('python')
print('a=',a)
a.discard('b')         
a.clear()         

# 添加集合元素 
# add()   把传入的元素作为一个整体添加到集合中
# update()  把要传入的元素拆分，作为个体添加到集合中
a = set('boy')
a.add('Python')
print('a=',a)
a.update('Python')
print('a=',a)

# 集合的遍历
a = set('python')
for x in a:
    print(x,end='')
    
# set可以进行集合运算
numSet = set()
a = set('abracadabra')
b = set('alacazam')
print(a)
print(a - b)     # a 和 b 的差集
print(a | b)     # a 和 b 的并集
print(a & b)     # a 和 b 的交集
print(a ^ b)     # a 和 b 中不同时存在的元素    
```

### 数据类型转换

有时候，我们需要对数据内置的类型进行转换，数据类型的转换，你只需要将数据类型作为函数名即可。

以下几个内置的函数可以执行数据类型之间的转换。这些函数返回一个新的对象，表示转换的值。

| 函数                                                         | 描述                                                |
| :----------------------------------------------------------- | :-------------------------------------------------- |
| [int(x [,base\])](https://www.runoob.com/python3/python-func-int.html) | 将x转换为一个整数                                   |
| [float(x)](https://www.runoob.com/python3/python-func-float.html) | 将x转换到一个浮点数                                 |
| [complex(real [,imag\])](https://www.runoob.com/python3/python-func-complex.html) | 创建一个复数                                        |
| [str(x)](https://www.runoob.com/python3/python-func-str.html) | 将对象 x 转换为字符串                               |
| [repr(x)](https://www.runoob.com/python3/python-func-repr.html) | 将对象 x 转换为表达式字符串                         |
| [eval(str)](https://www.runoob.com/python3/python-func-eval.html) | 用来计算在字符串中的有效Python表达式,并返回一个对象 |
| [tuple(s)](https://www.runoob.com/python3/python3-func-tuple.html) | 将序列 s 转换为一个元组                             |
| [list(s)](https://www.runoob.com/python3/python3-att-list-list.html) | 将序列 s 转换为一个列表                             |
| [set(s)](https://www.runoob.com/python3/python-func-set.html) | 转换为可变集合                                      |
| [dict(d)](https://www.runoob.com/python3/python-func-dict.html) | 创建一个字典。d 必须是一个 (key, value)元组序列。   |
| [frozenset(s)](https://www.runoob.com/python3/python-func-frozenset.html) | 转换为不可变集合                                    |
| [chr(x)](https://www.runoob.com/python3/python-func-chr.html) | 将一个整数转换为一个字符                            |
| [ord(x)](https://www.runoob.com/python3/python-func-ord.html) | 将一个字符转换为它的整数值                          |
| [hex(x)](https://www.runoob.com/python3/python-func-hex.html) | 将一个整数转换为一个十六进制字符串                  |
| [oct(x)](https://www.runoob.com/python3/python-func-oct.html) | 将一个整数转换为一个八进制字符串                    |

## 函数

### 自定义函数

定义、调用

```python
# 有无参数 def 函数名(参数1,参数2,...参数3):    函数体    return [返回值列表]函数名(实参1,实参2,...实参3)
```

参数、返回值

参数

- 形参与实参
	- 形参：使用def 语句来定义函数时，函数名后面的圆括号中的参数就是形式参数（简称形参），形参只能是变量，只能被函数调用时才分配内存单元，调用结束时释放所分配的内存单元
	- 实参：调用函数时，函数名后面的圆括号中的参数。实参可以是常数、变量、表达式，在实施函数调用时，实参必须有确定的值
- 必备参数
	- 输入的实参和形参的顺序要一致，实参数量必须和声明函数时形参的数量一样
- 关键字参数
	- 函数调用使用关键字参数来确定传入的参数值。使用关键字参数允许函数调用时参数的顺序与声明不一致。

```python
def fun(dis,price):fun(price=1000,dis=0.5)
```

- 默认参数
	- 定义函数时，可以为函数的某个形参赋予默认值，这个参数被称为默认值参数。带有默认值参数的函数定义
	- 在定义默认值参数的函数时，只能将默认值赋给最右端的参数

```python
def 函数名(...,形参 = 默认值)：	函数体
```

- 不定长参数

```python
def 函数名([形参列表 ,] * args)	函数体def f(x,y, * args):    print(args)f(10,2,34,4,5,34)    
```

返回值

```python
return [返回值列表]
```

递归函数

- 递归就是函数直接或间接的调用其本身。
- 递归是常用的编程方法，适用于把大型复杂的问题转化为一个与原问题性质相似，但规模较小的问题来求解的场景

```python
# 计算阶乘def f(n):    if n == 1:        return 1    else:        return f(n-1) * n    n = int(input('请输入一个数：'))print(f(n))
```

匿名函数`lambda函数`

- 匿名函数并非没有名字，而是将函数名作为函数结果返回，这种函数省略了用`def` 定义函数的标准步骤

```python
函数名 = lambda[参数列表]:表达式sum = lambal arg1,arg2:arg1+arg2;print(sun(20,50))    
```

变量的作用域：就是变量的适用范围

- 全局变量：函数值外定义的变量
- 局部变量：定义在函数内的变量，只能在函数内使用，作用范围仅在函数内部的变量

### 内置函数`内建函数`

- 数学运算：`abs() 绝对值 `、`max()、min()`、`pow() 乘方数`、`round(2.3434,3) 指定位数小数`、`divmod(9,2) 商和余数`、`round() 四舍五入`、`complex() 创建一个复数`、`eval() 计算字符串参数中的表达式的值`、`range() 生成一个指定的范围`
- 类型转换：`int()`、`float()`、`str()` 字符串、`bool()` 布尔、`hex()`十六进制、`bin()`二进制、`chr()`数字 ==>ASCII码字符、`ord()` ASCII  ==> 数字
- 字符串：
	- 大小写转换 `lower()` 小写、`upper()` 大写、`swapcase()` 大小写反转、`capitalize()` 首字母大写、`title()` 每一个单词首字母大写
	- 输出方式`print()`、`input()`
	- 搜索和替换字符串`find()`、`rfind()`、`index()`、`rindex()`、`replace()`
	- 分隔与组合`split()`、
- 相关操作函数：`type() ` 数据类型、`help()` 系统内置帮助  help(input)\help(print)

## 面向对象

### 概述

- 面向对象程序设计（Object Oriented Programming ，OOP）语言有三大特性：继承、多态、封装
- 对象`object`
- 类`class`
- 消息`message`
- 三大特性
	- 封装`encapsulation`
	- 继承`inheritance`
	- 多态`polymorphism`

### 类与对象

> 类
>
> - 属性（特性）
> - 方法（行为）

- 类是面向对象程序设计的基础，可以定义指定类的对象。类中可以定义属性（特性） 和方法（行为）

```python
# 定义类class 类名:	成员变量	成员方法    # 对象的创建和使用对象名.属性名对象名.函数名()class CC:    x = 10    y = 20    z = 30    def show(self):        print((self.x+self,y+self.z)/3)b = CC() # 创建实例对象bb.x = 30b.show()
```

### 属性和方法

#### 类属性和实例属性

##### 类属性

类属性（class attribute） 为所有类对象的实例属性所共有。类属性通常在类体中初始化·。对于公有的类属性，在类外可以通过类队对象和实例对象访问

```python
class Person:	name = 'Kity' # 公有的类属性    __age = 18 # 私有的类属性print(p.name) # 正确，不提倡print(Person.name) # 正确print(p.__age) # 错误，不能再类外通过实例对象访问私有的类属性print(Person.__age)  # 错误，不能再类外通过类对象访问私有的类属性
```

##### 实例属性

实例属性（instance attribuite）不需要在类中显式定义，而在`__init__`构造函数中定义，定义时以`self.`作为前缀，实例属性

```python
class student:	def __init__(self,name,age,grade):        self.name = name        self.age = age        self.grade = grade    def say_hi(self):        print('我是',self.name)s1 = Student('网站',23,34)s1.say_hi()print(s1.grade)s2 = Student('克隆',23,34)s2.say_hi()print(s2.grade)
```

#### 类的方法

> 类的方法
>
> - 实例方法
> - 类方法
> - 静态方法

##### 方法的声明和调用

```python
def 方法名 (self,[形参列表])	函数体方法调用的格式语法：对象.方法名([参数列表])
```

##### 实例方法

```python
def 方法名 (self,[形参列表])	函数体方法调用的格式语法：对象.方法名([实参列表])class Person:    place = 'ChangeSha'    def getPlace(self):		return self.placep = Person()print(p.getPlace)print(p.place)
```

##### 类方法

```python
@classmethoddef 类方法名(cls,[形参])	函数体类方法调用格式如下:类名.类方法([实参列表])class Person:    place = 'ChangeSha'    @classmethod  # 类方法，用 @classmathod 来进行修饰    def getPlace(cls):        return cls.placep = Person()print(p.getPlace())  # 可以通过实例对象引用print(Person.getPlace())  # 可以通过类对象引用
```

##### 静态方法

```python
@staticmethod class Person:	place = 'Changsha'    @ staticmethod    def getPlace():        return Person.placeprint(Person.getPlace())
```

#### 构造方法和折构方法

类中最常用的内置方法就是构造方法和折构方法

##### 构造方法

`__int__(self,...)`：在生成对象时调用，可以用来进行一些属性初始化操作，不需要显示去调用，系统默认执行。

```python
class Persion:    def __int__(self,name) # 构造方法    	self.PersonName = name    def sayHi(self):        print('我的名字叫做{}。'.format(self.PersonName))p = Person('Hello Messsage')    p.sayHi()
```

##### 折构方法

`__def__(self)`：在释放对象调用，支持重载，可以在其中进行一些释放资源的操作，不需要显示调用。

```python
class Test:    def __int__(self):        print('构造方法')    def __del__(self):        print('折构方法')    def myf(self):        print('调用自定义方法')obj = Test()obj = myf()del obj
```

#### 属性和方法的访问控制

##### 属性的访问控制

`name=''` 公有属性 `__name=''`私有属性

```python
class Person:	name=’萝莉‘	age= 20p = Person()print(p.name,p.age)
```

##### 方法的访问控制

`__name 和 __age 是类的私有属性`

```python
class Person:    __name='工作'    __age=16	def getName(self): # 类的方法        return self.__name    def getAge(self):        return self.__age p = Person()print(p.getName(),p.getAge())
```

### 继承

面向对象的编程带来的主要好处是代码的重用，实现这种重用的方法之一是通过继承机制。继承用于指定一个类将其父类获取其大部分或全部功能。用户对现有类进行修改，来创建一个新的类，称为子类或派生类，原有的类称为父类或基类

```python
class 子类名 (父类名):
	类体
```

```python
class Person(object):
    def __init__(self,name,gender)：
    	self.name = name
        self.gender = gender
        print('Person类__init()__','姓名'，’self.name‘)
        
class Student(Person):
    def __init__(self,name,gender,score):
        super(Student,self).__init__(name,gender)
        self.score = score
        print('student类__init__。','姓名:','self.name')
        
if __name__ == '__main__'
	person = Person('张三','男')
    student = Student('李四','男',1000)
```

多重继承

```python
class p1():
    def foo(self):
        print('p1-foo')
class p2():
    def foo(self):
        print('p2-foo')     
    def bar(self):
        print('p2-bar')
class C1(P1,P2):
    pass
class C2(P1,P2):
    def bar(self):
        print('C2-Bar')
class D(C1,C2):
    pass

if __name__ = '__main__':
    d = D()
    d.foo()
    d.bar()
```

### 多态

```python
class Dog(Object):    def work(self):        passclass ArmyDog(Dog):    def work(self):        print('追击敌人')class DrugDog(Dog):    def work(self):        print('追击毒品')class Person(object):    def work_with_dog(self,dog)    	dog.work()person = Person()person.work_with_dog(ArmyDog)person.work_with_dog(DrugDog)
```

### 封装（Encapsulation）

封装的主要原因是保护隐私

```python
class A:    def fm(self):        print('from A')    def test(self):        self.fm()class B:    def fm(self):        print('from B')b = B()b.test()# form Bclass A:    def __fm(self):        print('from A')    def test(self):        self.__fm()class B(A):    def __fm(self):        print('from B')b = B()b.test()# form A
```

### 单例模式

- 单例模式`Singleton Patten`是一种常用的软件设计模式，该模式的主要目的是确保某一个类只有一个实例存在
- 在某些系统中，节省内存资源，保证数据内容的一致性，对某些类要求只能创建一个实例，这就是所谓的单例实例

```python
class Earth(object):	__inistance = None    def __new__(cls):        if cls.__instance == None:            # 如果__instance 为空证明是第一次创建实例            # 通过父类的__new__(cls) 创建实例            cls.__instance = object.__new__(cls)            return cls.__instance        else:            # 返回上一个对象的引用 。            return cls.__instancea = Earth()        
```

## 文件操作

### 文件

文件分类

- 根据文件依附的介质不同
	- 普通文件：指驻留在磁盘或其他外部设备介质上的一个有序数据集
	- 设备文件：指与主机相连的各种外部设备，将外部设备当作文件来处理
- 根据文件的组织形式
	- 顺序读写文件`Sequential Access file`：是指按从头到尾的顺序读出或写入的文件
	- 随机读写文件`Random Access file`：一种跳跃式直接访问方式
- 按文件存储数据的形式
	- ASCII文件：称为文本文件，ASCII 码 文件中每一个字节存放一个ASCII代码，代表一个字符，此种存储形式
	- 二进制文件：二进制文件中的数据是按照在内存中的二进制存、储格式存放的，此种存储形式节省 存储单元。

| 文件对象属性 | 含义         |
| ------------ | ------------ |
| name         | 文件名称     |
| mode         | 打开模式     |
| closed       | 文件编码方式 |

文件的打开和关闭

```python
# open(filename[, mode][,encoding]) filename 文件名称 mode 打开模式 encoding 文件编码方式f1 = open('one.py', mode='r',encoding='utf-8')for line in f1:    print(line)f1.close()
```

文件关闭

```python
# 常规方法f1.close()#异常处理方法try:    f2 = open('studentinfo.txt')finally:    f2.close()    # 使用with语句方式with open('studentinfo.txt') as f3:    pass
```

`r` 读取、`w` 写入 、`a` 追加

| 访问模式 | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| `r`、    | 只读方式打开文件                                             |
| `w`      | 写入，文件存在覆盖                                           |
| `a`      | 追加                                                         |
| `b`      | 二进制模式                                                   |
| `t`      | 文本模式，系统默认的文件打开方式                             |
| `+`      | 打开一个用于更新（读取和写入）的文件                         |
|          |                                                              |
| `rb`     | 以二进制打开一个文件用于只读                                 |
| `wb`     | 以二进制打开一个文件用于写入                                 |
| `ab`     | 以二进制打开一个文件用于追加                                 |
|          |                                                              |
| `r+`     | 打开文件用于读写，指针放在文件的开头处                       |
| `w+`     | 打开文件用于读写，文件覆盖，不存在，创建                     |
| `a+`     | 打开文件用于读写，追加，指针将放在文件结尾                   |
| `rb+`    | 以二进制打开文件用于读/写，指针放在文件的结尾处              |
| `wb+`    | 以二进制打开文件用于读/写，文件存在覆盖，文件不存在，创建新文件 |
| `ab+`    | 以二进制打开文件用于追加，文件存在结尾追加，文件不存在，创建新文件 |

读/写操作

读：`read()、readline()、readlines()`

- read()  一次读取文件的所有内容，并存放在一个大字符串中、`文件对象.read([size])`
- readline()  逐行读取文本，结果是一个list、`文件读对象.readline()`
- readlines() 方法一次性读取文本的所有内容，结果是一个list `文件对象.readlines()`

```python
# read()with open('studentinfo.txt',mode='r',encoding='utf-8') as f1:	print(f1.read(2))    	print(f1.read(4))    # readline()with open('studentinfo.txt',mode='r',encoding='utf-8') as f1:    # line = f1.readline()    # while line:    while f1.readline()        line = line.rstrip('\n')        print(line)        line = f1.readline()# readlines()with open('studentinfo.txt',mode='r') as f1:    for line in f1.readlines():        line_str = line.rstrip('\n')        print(line_str)
```

写：`write()、writelines()`

- write 将参数的内容写入文件 `文件对象.write([size])`
- writelines() 把多行内容写入文件,参数 可以是一个可迭代的对象、列表、元组 等`文件对象.writelines()`

```python
# write 文件对象.write([size])with open('teacherinfo.txt',mode='w') as f1:    f1.write('我是一个teacher\n')    f1.write('我也是一个学生\n')with open('teacherinfo.txt',mode='r') as f1:    for line in f1.readlines():    	print(line.rstrip('\n'))        # writelines(参数可以是对象、列表、元组) 文件对象.writelines()list = ['My\n','You\n','Her\n']with open('teacherinfo.txt',mode='w') as f1:    f1.writelines(list)
```

### CSV 文件操作

- CSV`(Comma-Separated Values)` 文件用于纯文本存储表格数据
- CSV文件是一种通用的、相对简单、有特殊格式的文件格式，而不是一种独立的文件类型
- 数字表格大量使用Excel进行处理，所以也经常用Excel 处理 CSV 文件
- 根据数据的不同：数据组织可以分为一维数组、二维数组、高维数组

CSV文件的一维读写

```python
# 写list = ['苹果','香蕉','西瓜','葡萄']f1 = open('shuigo.csv','w') # 新建 .csv文件f1.write(','.join(list)+'\n')f1.close()# 读f2 = open('shuigo.csv','r')list = f2.read().strip('\n').split(',')f2.close()print(list)
```

CSV文件的二维读写

```python
# 写list = [    ['水果名称','单价','数量','金额'],    ['葡萄','30','34','67'],    ['苹果','50','90','125'],    ['香蕉','84','92','63']]f3_name = 'shuiguo.csv'f3 = open(f3_name,'w')for row in list:    f3.write(','.join(row)+'\n')print('数据写入成功',f3_name,'成功。')# 读f4_name = 'shuiguo.csv'f4 = open(f4_name,'r')list = []for line in f4:    list.append(line.strip('\n').split(','))f4.close()print(list)
```

### 目录

> 增： 新建目录
>
> 删： 删除目录
>
> 改：修改目录名字
>
> 查：查询目录内容

| 目录对象属性                         | 描述                                                         |
| ------------------------------------ | ------------------------------------------------------------ |
| `os.rmdir()`                         | 删除目录，删除目录必删除目录中的文件                         |
| `os.remove()`                        | 删除指定文件                                                 |
| `os.system()`                        | 执行操作系统命令，例如：清除屏幕、创建目录、复制文件`执行DOS中的文件` |
| `os.rename()`                        | 文件重命名                                                   |
| `os.walk(dirpath,dirname,filenames)` | `搜索指定目录及其子目录` 而不是文件                          |
| `os.mkdir()`                         | 创建目录                                                     |

```python
os.path.exists() # 文件/目录存在判断os.getcwd()  # 当前路径
```

```python
# os.remove() 删除文件
import os
fileName = 'test.txt'
if os.path.exits(fileName):
	os.remove(fileName)
    print(file_name++'文件删除成功')
else:
    print(fileName+'文件没有找到')

# os.mkdir()  创建目录
dir_str = os.getcwb()
my_dir = 'Pythonfile'
if not os.path.exists(my_dir)
	os.mkdir(my_dir)
    print('当前目录为'+dir_str+'。在该目录下，'+my_dir+'目录创建成功')
else:
    print('当前目录为'+dir_str+'。在该目录下，'+my_dir+'目录已存在')

# os.rmdir() 删除目录   
import os
dir_str = os.getcwd()
my_dir = ’PythonFile‘
if os.path.exists(my_dir):
    os.rmdir(my_dir)
    print(my_dir+'目录删除成功！')
else:
    print(my_dir+'目录未找到')
    
# os.system() 运行DOS命令
# cls mkdir 文件名 copy 文件名 文件名 notepad calc
os.system('cls')

# os.rename() 文件重命名
if os.path.exits(file_name)
	os.rename(file_name,file_name_new)
    print('文件重命名为'+file_name_new)
else
	print('文件没有找到')

# os.walk(dirpath,dirname,filename)
# dirpath：以字符串形式返回该目录下的所有的绝对路径
# dirnanme：以列表形式返回每一个绝对路径下的目录
# filename：以列表形式返回该路径下所有文件
import os
cur_path = os.path.dirname(__file__) # 当前pyw文件路径
cur_path += '/PythonFile'
sample_tree = os.walk(cur_path)
for dir_name,sub_dir,files in sample_tree
	print('文件路径：',dir_name)
    print('目录列表：',sub_dir)
    print('文件列表：',files)
```

## 正则表达式

### 概述

正则表达式：规则表达式，实际上是一个`文本模式`，通过一个字符序列来定义一种搜索模式，主要用于字符串模式匹配或字符串匹配（即查找和替换操作）。一个正则表达式 由字母，数字和一些特殊符号组成，这些符号的序列组成一个`规则字符串`，用来表示满足某种逻辑条件的字符串。

功能

- 测试字符串内的模式
- 替换文本
- 基于模式匹配从字符串中提取子字符串
- 可以查找文档内或输入域内特定的文本

### 语法

- 非打印字符`\cx(匹配x指明的控制字符) \f(换页符) \n(换行符) \r(回车符) \s(匹配任何空白符) \S(任何非空白字符) \t(制表符) \v(垂直制表符)`
- 特殊字符`$ () * + . [ ? \ ^ { |`
- 数量限定符`* (匹配前面的子表达式0次或多次) + (1次或多次) ? (0次或1次) {n} (匹配前面字符串n次) {n,} (至少匹配n次) {n,m} (至少n次，最多m次)`
- 定位符`^(开头位置) $(结尾) \b(匹配一个单词边界，即字与空间间的位置) \B(非单词边界匹配)`
- 特殊序列
	-  `\d(匹配一个数字字符[0-9]) \D(用来对数位类求反 [^0-9]) `
	-  `\w(匹配一个单词字符，包括字母、数字、下划线 [a-z A-Z 0-9]) \W(对字母、数字和下划线求反 [^a-z A-Z 0-9]) `
	-  `\s(匹配一个不可见字符（包括空格、制表符和换行符）) \S(用来匹配一个可见字符)`

### 函数

`re`模块：python `1.5起`增加了`re`模块，`re` 模块使 Python 语言有全部的正则表达式功能

| 函数             | 描述                                         |
| ---------------- | -------------------------------------------- |
| `compile()`      | 用来对正则表达式进行编译和处理正则表达式对象 |
| `match()`        | 匹配对象                                     |
| `search()`       | 搜索字符串                                   |
| `sub()、split()` | 搜索和替换\分隔符进行拆分                    |

```python
import rere.compile(pattern,flags=0)re.match(pattern,string,flags=0)re.search(pattern,string,flags=0)re.sub(pattern,rep1,string,flags=0)re.split(pattern,string,maxsplit=0,flags=0)
```

```python

```

### 捕获

### 贪婪与非贪婪模式

## 异常处理

### 语法错误和异常的概念

- 语法错误`syntax errors`解析错误：通常是由于没有正确掌握语法或输入代码过程中出错而造成的。
- 异常`exceptions`：是在程序执行过程中发生的一个事件，会影响程序的正常执行。异常是指因为程序出错而在正常控制流以外采取的行为

### 异常类

Python 内置很多异常类，可向用户准确反馈出错信息。python中，异常也是对象，可对它进行操作。`BaseException`是所有内置异常类的基类，但用户定义的类并不直接继承`BaseException`，所有的异常类都是从`Exception`继承，且都在`exceptions`模块中定义。自动将所有的异常名称放在内建命名空间中，不必导入`exceptions`模块即可使用异常。

- TypeError (类型错误)
- IndentainError(缩进错误)
- IndexError(索引错误)
- SyntaxError(语法错误)
- ValueErorr(值错误)
- AttibuteError(属性错误)
- KeyError(key键错误)

### 异常处理                                             

程序设计中经常需要考虑对程序各种异常情况进行预判和处理

- else、finally、最后一个except语句都是可选项

```python
try: # 开始监测异常	<代码块>except <Exception Type1>: # Exception Type 是具体的异常类型 可以使系统内置异常或用户自定义异常	<异常处理代码块1>  # 异常代码块except:	<异常处理代码块2>else:    <异常处理代码块3>finally:  #     <异常处理代码块4>    try:    f1 = open('test.txt','r')    readstr = f1.read(20)exceptIOError	print('没有找到文件或读取文件失败')else:    print(readstr)    f1.close()try:    <代码块>else:    print('')finally:    print('')
```

### 抛出异常`raise 强制抛出指定异常`

可以自动引发异常，也可以通过raise显示地抛出异常。一旦执行了raise语句，raise后面的语句将不能执行（raise允许在任何时候强制抛出一个指定的异常，而不必等python引发）。

```python
raise exceptionName
```

```python
data = input('请输入一个整数：')try:    if data.isdigit():        data_int = int(data)    else：    	raiseValueError exceptValueError:    print('数据转换成整数时出错',data)
```

### 断言`assert`

断言是用来检查非法情况而不是程序发生某种错误情况的工具，用来帮助开发者快速定位问题的位置。异常处理用于对程序发生异常情况的处理，增强程序的健壮性和容错性

断言用于检查函数输入的合法性，要求输入满足一定的条件才能继续输入执行，在含数字hi行过程中出现的异常情况使用异常捕获

用来声明某个条件是真的。其作用是测试一个条件(condition)是否成立，如果不成立，则抛出异常。

```python
assert condition[,exception]v1 = 1v2 = 2assert (v1 < v2)assert (v1 > v2),'{0} is not bigger than {1}'.format(v1.v2)
```

### 用户自定义异常

创建自定义异常类就是创建一个异常子类。通过继承，用户可以命名它们自已的异常

Exception 类是常规异常的基类，也是`BaseException`类的子类之一

```python
class MyException(Exception)
pass

class MyFirstError(Exception)
	def __init__(self,value):
        self.value = value
        def __str__(self):
            returnrepr(self.value)
            
try:
    raiseMy FirstError(2*2)
except MyFirstError as mfe:
    print('发生用户自定义异常',mfe.value)
```

### 上下文管理

with 是一种上下文管理协议，目的在于从流程图中把try、except和finally 关键字和资源分配释放相关代码统统去掉，简化`try...except...finally`的处理流程。with 通过 enter 方法初始化，然后在exit 中做善后以及处理异常

```python
with expression[as target] 
# expression:是一个需要执行的表达式   
# target:是一个变量或者元组，存储的是expression表达式执行返回的结果，可选参数 
with body

filename = 'test.txt'
mode = 'w'
with open(filename,mode) as writer
	writer.write('Hello')
```

## 模块使用与程序打包

### 模块的概述

- 面向对象开发时抽象为类的过程实际已经是一层封装
- 模块则是由变量、语句、函数或类的定义的程序文件组合而成，文件名字就是模块名加上`.py`模块名
- 模块的优点
	- 提高代码的可维护性
	- 提高代码的可重用性
	- 有利于避免函数名和变量名冲突
- 模块三个视角
	- 代码的重用
	- 系统命名空间的划分
	- 服务和数据的共享

```python
模块名.函数名(参数列表)
模块名.变量
```

### 模块导入的三种方法

`import`、` from...import` 和 `from modname import *`

```python
# 导入模块
import module1[,module2[,...moduleN]]
# 导入模块 函数
from modname import name1[,nam2[,...nameN]]
from modname import *
```

在python中用import或者from...import来导入相应的模块 函数

- 将整个模块(somemodule)导入，格式为： **import somemodule**

- 从某个模块中导入某个函数,格式为： **from somemodule import somefunction**

- 从某个模块中导入多个函数,格式为： **from somemodule import firstfunc, secondfunc, thirdfunc**

- 将某个模块中的全部函数导入，格式为： **from somemodule import  **


```python
## 导入 sys 模块import sysfor i in sys.argv:	print(i)  print(sys.path)# 导入 sys 模块的 argv,path 成员from sys import argv,path #  导入特定的成员  print('path:',path) # 因为已经导入path成员，所以此处引用时不需要加sys.path
```

```python
# printdemo.py 要在根目录下def print_func(par):    print('printdemo文件中的内容',par)# maindemoimport printdemoprintdemo.print_func('maindem参数')
```

### 常用模块

#### syc模块

syc模块实现从程序外部向程序传递参数的功能，也可以获取程序路径和当前系统平台等信息

```python
import sysprint(sys.platform)print(sys.path)
```

#### platform模块

platform 模块获取操作系统的信息

| 函数                      | 作用                       |
| ------------------------- | -------------------------- |
| `system()`                | 操作系统类型               |
| `version()`               | 操作系统版本号             |
| `platform()`              | 系统名称及版本号           |
| `machine()`               | 计算机类型信息             |
| `node()`                  | 计算机网络名称             |
| `processor()`             | 计算机的处理器信息         |
| `uname()`                 | 计算机的综合信息           |
| `python_build()`          | Python版本信息             |
| ``python_version()``      | Python主版本信息           |
| `python_compiler()`       | Python 编译器信息          |
| `python_branch()`         | Python分支信息             |
| `python_implementation()` | Python解析器的实现版本信息 |

```python
import platformprint(platform.system())print(platform.version())print(platform.platform())print(platform.machine())print(platform.python_version())print(platform.python_branch())print(platform.python_compiler())
```

#### math模块

- e、pi
- pow(x,y) x的y次方 
- sqrt(x) x的平方
- ceil(x)  不小于 x的整数
- floor(x)  不大于x的整数

```python
import math print(math.pi)print(math.pow(2,3))
```

#### random

| 方法                                  | 说明                                                         |
| ------------------------------------- | ------------------------------------------------------------ |
| `random()`                            | 生成0到1的随机浮点数                                         |
| `uniform(a,b)`                        | 生成一个指定范围内的随机浮点数                               |
| `randint(a,b)`                        | 生成一个指定范围内的整数                                     |
| `randrange([start],stop[,step])(y,x)` | 从指定范围内，按指定基数递增的集合中获取一个随机数           |
| `choice(sequence)`                    | 从序列中获取一个随机元素。参数sequence表示一个有序类型，可以是列表、元组或字符串 |
| `shuffle(x[,random])`                 | 用于将一个列表中的元素打乱                                   |
| `sample(sequence,k)`                  | 从指定序列中随机获取指定长度（k）的判断。原有序列不会被改变  |

```python
import random print(random.randint(0,100))list = [12,34,546,67,68,798]print(random.choice(list))print(random.randrange(1,10,2))
```

#### time模块

使用时间戳和`struct_time`数组两种方法表示时间

- `time.strftime (格式化字符串)`
	- `1%y 两位数的年份表示`
	- `1%Y 四位数的年份表示`
	- `1%m 月份`
	- `1%d 月内中的一天`
	- `1%H 24小时制小时数`
	- `1%I 12小时制小时数`
	- `1%M 分钟数`
	- `1%S 秒`
	- `1%a 本地简化星期名称`

```python
import time print(time.time())print(time.localtime(time.time()))# 将时间数据结构转换为格式字符串进行输出print(time.strftime('%Y-%m-%d',time.localtime(time.time())))
```

### 创建自定义模块

- 自建模块的后缀名是`py`
- 创建的模块得放到同一文件里面

编写模块

```python
# mymodule.py
def PrintString(str):
	print(str)
def Sum(num1,num2):
    print(num1 + num2)
    
# main.py
import mymodule
mymodule.PrintString('Hello Message')
mymodule.Sum(10,20) 
```

用`__name__` 防止模块被错误地执行

问题：分清执行模块的语境到底是导入的还是直接执行，模块中的语句如果不被定义在函数中，只要在导入模块时，该语句都将被执行。

import的时候当作模块解析而不是直接执行

解决方法：定义全局变量`__name__`

```python
# mymodule.py 当前文件运行__main__
if __name__ == '__main__':
    print('这个执行是从自定义模块直接启动')
    print('直接将自定义模块当作main启动')
elif __name__ ==  'mymodule':
    print('这个执行是从其他模块导入mymodule后调用的')
else:
    print(__name__)

def PrintString(str):
    print(str)
    
def sum(num1,num2):
    print(num1 + num2)

# main.py
import mymodule
mymodule.PrintString('Hello String')
mymodule.sum(1,223)
```

重载模块

导入模块的过程实际就是解释器去执行一遍的过程，若导入的模板代码是热修改的，重新导入这个模块，此时不能静态地调用`import`，要通过函数`reload `来实现模块的重载

```python
reload(mymodule)
```

```python
import mymodulefrom imoportlib import reload # imp从Python3.4之后弃用，importlib 代替mymodule.PrintString('Hello Message')mymodule.sum(12,34)reload(mymodule)
```

### 程序打包

安装

```bash
pip install pyinstaller 
```

使用`pyinstaller`模块，将Python代码打包成`exe` 文件

```bash
pyinstaller [opt]  yourprogram.py
pyinstaller -F - W  文件名.py
```

| 参数 | 含义                                                         |
| ---- | ------------------------------------------------------------ |
| `-F` | `--onefile` 打包成一个`exe`文件                              |
| `-D` | `--onefile` 创建一个目录，包含exe文件，但会依赖很多文件（默认选项） |
| `-c` | `--console,--noWindowed` 使用控制台，无窗口（默认）          |
| `-w` | `--Windowed,--noconsole` 使用窗口，无控制台                  |

## CGI



## MySQL



## 网络编程



## SMATP



## 多线程



## XML解析



## GUI编程



## IDE



## JSON

 



# 第三方库

> - wxpy微信模块库
> - 图表类库
> - 数据分析类库
> - 网络爬虫库

## wxpy 微信模块

[youfou/wxpy: 微信机器人 / 可能是最优雅的微信个人号 API ✨✨](https://github.com/youfou/wxpy)

[wxpy: 用 Python 玩微信 — wxpy 0.3.9.8 文档](https://wxpy.readthedocs.io/zh/latest/)

- 微信WebAPI的库
- wxpy 在 itchat 的基础上，通过大量接口优化提升了模块的易用性，并进行丰富的功能扩展

```bash
pip install -Uwxpy
```

向文件助手发送信息

```python
from wxpy import *
bot = Bot()
myself = bot.self
bot.file_helper.send('Hello from wxpy')
```

统计微信好友数、微信群、公众号

```python
from wxpy import *
bot = Bot()
myself = bot.self
t0 = bot.friends(update=False)
print('我的好友数：'+str(len(t0))-1 )
t1 = bot.groups(update=False)
print('我的微信群聊数：'+str(len(t1)) )
t2 = bot.mps(update=False)
print('我的公众号数：'+str(len(t2)) )
embed()
bot.join
```

分析好友男女比例

```python
# 分析好友男女比例
# 添加 matplotlib 库 图标库
from wxpy import *
import matplotlib.pyplot as plt
# 新建第一次登陆的缓存路径文件 use.pkl
bot = Bot(cache_path=r"D:\GitRepository\VsWorkSpace\Python\wx\use.pkl")
myself = bot.self
friends = bot.friends(update=False)
male = female = other = 0
for i in friends[1:]:
    sex = i.sex
    if sex == 1:
        male += 1
    elif sex == 2:
        female += 1
    else:
        other += 1
total = len(friends[1:])
# 绘制图形
labels = '男','女','其他'
sizes = [male,female,other]
colors = ['red','green','blue']
explode = (0,0,0.1)
plt.rcParams['font.sans-serif'] = ['SimHei']
plt.title('微信中好友男女比例',size = 16)
plt.pie(sizes,explode= explode,labels= labels,colors= colors,autopct='% 1.1f% %',shadow=True,startangle= 90)
plt.axis('equal')
plt.legend(loc= 'upper right')
plt.show()
print("男性好友的数量：",male)
print("女性好友的数量：",female)
print("其他好友的数量：",other)
```

给指定朋友发送消息

```python
from wxpy import *bot = Bot(cache_path=r"D:\GitRepository\VsWorkSpace\Python\wx\use.pkl")myself = bot.selffriend = bot.friends().search("陀东澎")[0]for i in range(1,100):    friend.send("Hello Message")
```

关键字聊天机器人

基于图灵机器人

```python
# [个人中心](http://www.tuling123.com/member/robot/2296304/center/frame.jhtml?page=0&child=0)
from wxpy import *
bot = Bot(cache_path=r"D:\GitRepository\VsWorkSpace\Python\wx\use.pkl")
myself = bot.self
my_friends = bot.friends().search("陀东澎")[0]
tuling = Tuling(api_key='53ca09daa9ca4659b30395e157f6818f')
print("图灵机器人已经启动")
@bot.register(my_friends)
def reply_my_frined(msg):
    ret = tuling.do_reply(msg)
    print('[发送]'+str(ret))
embed()
```

## Excel 表格
