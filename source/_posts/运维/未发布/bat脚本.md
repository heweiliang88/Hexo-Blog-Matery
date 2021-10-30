---
title: bat命令的学习
categories:
- window10
tags:
- bat
abbrlink: 12013
---

# Bat基础知识

> [批处理入门手册](https://www.w3cschool.cn/pclrmsc/)
>
> [《Windows 批处理(bat)语法大全》](https://www.bookstack.cn/read/zhaoqingqing-bat/copyright.md)
>
> [bat脚本的基本命令语法](https://www.cnblogs.com/lizm166/p/11132601.html)
>
> 如何在 Windows 10 上创建和运行批处理文件 - 帮助和操作方法 | 十月 2021
> https://zh.freax.be/how-create-run-batch-file-windows-10
>
> BAT批处理命令 - 知乎
> https://zhuanlan.zhihu.com/p/319975719
>
> 常用bat命令简介-阿里云开发者社区
> https://developer.aliyun.com/article/680608
>
> start 命令 - Bat 批处理教程
> https://www.hxstrive.com/subject/windows_bat.htm?id=80
>
> 批处理_百度百科
> https://baike.baidu.com/item/%E6%89%B9%E5%A4%84%E7%90%86/1448600
>
> bat脚本的基本命令语法 - 整合侠 - 博客园
> https://www.cnblogs.com/lizm166/p/11132601.html
>
> Windows批处理(cmd/bat)常用命令小结 - lsgxeva - 博客园
> https://www.cnblogs.com/lsgxeva/p/10694546.html

bat文件是dos下的批处理文件。 批处理文件是无格式的文本文件，它包含一条或多条命令。 它的文件扩展名为.bat 或.cmd。 

批处理(Batch)，也称为批处理脚本。顾名思义，批处理就是对某对象进行批量的处理。批处理文件的扩展名为bat。

## 基础语法

常见命令

```
@echo off
echo hello bat!!!
pause
```

```bash
@echo off　　　　　　　　　　  不显示后续命令行及当前命令行
dir c:\*.* >a.txt　　　　　　　       将c盘文件列表写入a.txt 
call c:\ucdos\ucdos.bat　　　　    调用ucdos 
echo 你好 　　　　　　　　　　  显示"你好" 
pause 　　　　　　　　　　　　 暂停,等待按键继续 
rem 准备运行wps 　　 rem和::　都是注释
cd ucdos　　　　　　　　　　　 进入ucdos目录 
wps 　　　　　　　　　　　　　 运行wps　
color [attr] 默认的控制台前景和背景颜色 [number]
// 0~7 A~F
find
start  运行程序 调用外部程序的命令
start explorer d:\
title cmd 窗口标题
mode 配置系统设备
mode con cols=17 lines=18 & color 9f // 配置窗口大小
goto  跳转
```

符号

```

```

循环

```
@echo off
for  %%I in (ABC) do echo %%I
pause  
```

# 常用的bat脚本

## 建立新文件或增加文件内容

```bash
echo 文件内容 > 文件名  // 添加内容
echo 文件内容 >> 文件名 // 追加内容
```

## 同时打开多个文件

```bat
@echo off 
start /D "D:\Program Files\redis\test1" start.bat
start /D "D:\Program Files\redis\test2" query.bat
start /D "D:\Program Files\redis\test3" update.bat
start /D "D:\Program Files\redis\test4" insert.bat
start /D "D:\Program Files\redis\test5" select.bat
start /D "D:\Program Files\redis\test6" delete.bat
```

## windows下.bat每5分钟运行一次python文件

```bat
@echo off  
set INTERVAL = 300
timeout %INTERVAL%
:Again  
echo Called000000000000000
python C:/test.py 
timeout %INTERVAL%
goto Again
```

```bat
@echo off  
set INTERVAL = 3000
timeout %INTERVAL%
:Again  
echo test
start /D "C:\Users\wade\Desktop" test.bat
timeout %INTERVAL%
goto Again
```

## 搜索当前目录下有哪些文件？

```bash
@echo off
for %%i in (*.*) do echo "%%i"
pause
```

## 搜索当前目录下所有的文本文件？

```bash
@echo off
for %%i in (*.txt) do echo "%%i"
pause
```

## VMware批处理开启服务器

```bash
cd D:\Program Files\VMware\VMware      
D:                        
vmrun start "F:\software\VMware\Centos10\CentOS10.vmx" nogui
vmrun start "F:\software\VMware\Centos11\CentOS11.vmx" nogui
vmrun start "F:\software\VMware\Centos12\CentOS12.vmx" nogui
vmrun start "F:\software\VMware\Centos13\CentOS13.vmx" nogui
vmrun start "F:\software\VMware\Centos14\CentOS14.vmx" nogui
vmrun start "F:\software\VMware\Centos15\CentOS15.vmx" nogui
```

## timeout命令延时操作

```bash
timeout /nobreak /t 5  //5s nobreak  不允许用户打断
// 批量处理命令
pause
```

## 实战

```

```

