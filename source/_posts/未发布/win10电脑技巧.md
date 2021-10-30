---
title: window10电脑技巧
categories：
- 操作系统
tags:
- window10
- 操作系统
abbrlink: 18123
---
## 电子书后缀

电子书格式， 是对使用电子书时的文件编码方式，文件结构的一种约定，便于区分。如同一把钥匙开一把锁，不同的文件要用不同的方法去读，去显示，去写，去打开或运行。分为PC电子书格式和手机电子书格式，PC电子书格式包括EXE、TXT、HTML、HLP等，手机电子书格式包括UMD、JAR等。

| 设备     | 格式                                                         |
| -------- | ------------------------------------------------------------ |
| PC格式   | EXE、TXT、HTML、HLP、CHM、LIT、PDF、WDL、CEB、ADM、PDG、EPUB、CAJ |
| 手机格式 | UMD、JAR                                                     |

> Kindle格式(后缀MOBI、.AZW) ,常用后缀 mobi 、azw3、epub
>
> Microsoft Word的文档格式(后缀DOC、.DOCX)

2.

3.

4.GIF格式 (后缀GIF)

5.

[mobi, azw, azw3, epub 格式有什么区别](https://bookfere.com/post/27.html)

### PDF

**PDF**（**Portable Document Format**的简称，意为“可携带文档格式”），是由Adobe Systems用于与应用程序、操作系统、硬件无关的方式进行文件交换所发展出的文件格式。PDF文件以[PostScript语言图象模型为基础，无论在哪种打印机上都可保证精确的颜色和准确的打印效果，即PDF会忠实地再现原稿的每一个字符、颜色以及图象。

### MOBI

mobi 和 azw 格式的推手主要是 Amazon，这两种电子书格式的发展很大程度上依靠 Amazon 这个巨大的内容提供商及其电子书阅读器 Kindle 的流行普及。它们同属亚马逊的私有格式，没有本质的区别，可以简单的这样理解，mobi 是比较老的一种格式，而 azw 只是 mobi 的另一种形式而已，也可以理解为 mobi 加了个壳，亚马逊利用它对电子书做 DRM 版权保护

### AZW3

亚马逊主推的电子书格式

主要说一下azw3——azw3的本质是KF8，是随着2011年Amazon推出Kindle Fire平板时一起推出的。它填补了Mobi对于复杂排版支持的缺陷，支持很多HTML5（尚不支持 HTML5 的视频和音频标签）和CSS3的语法，这就大大改善了原来mobi或azw内容排版上的一些缺陷，单纯从读者的角度来讲，是不输epub格式的。从 Amazon购买的书，大部分已经是azw3格式了，而以前主流的mobi格式则越来越少，``它正逐渐取代mobi成为Kindle电子书的主流格式``。

### EPUB

EPUB（Electronic Publication的缩写，电子出版）是一种电子图书标准，由国际数字出版论坛（IDPF）提出；其中包括3种文件格式标准（文件的附文件名为.epub），这个格式已取代了先前的Open eBook开放电子书标准。

### CHM

CHM 文件格式是微软于 1998 年推出的基于 HTML 文件特性的帮助文件系统，以替代早先的 WinHelp 帮助系统。它在 Windows 98 中把 CHM 类型文件称作“编译的 HTML 帮助文件”（Compiled HTML Help file）。



## 图片后缀

> JPEG格式(后缀JPEG、.JPG)
>
> GIF格式 (后缀GIF)
>
> PNG格式 (后缀PNG)

### WebP 图像格式

WebP图像格式是新的图像压缩格式。使用这个格式的图像的体积将比JPEG格式图像减小40%，与JPEG相同，WebP是一种有损压缩。但谷歌表示，这种格式的主要优势在于高效率。WebP图像格式源于Google的开源视频格式WebM。Google计划将推出WebP软件，让人们自己判断图片质量。Google表示将在未来几周让Chrome本地支持WebP图片。 并希望其它网页开发者也采用这种新格式。

### base64图片

[base64图片在线转换工具](http://tool.chinaz.com/tools/imgtobase/)

图片的base64编码就是可以将一张图片数据编码成一串字符串，使用该字符串代替图像地址url。





## 服务器

### 免费域名地址

[Client Area - Freenom](https://my.freenom.com/clientarea.php?managedns=heweiliang.tk&domainid=1095440288)

### 宝塔控制面板



### 服务器连接的方法

#### SSH 登陆

```bash
ssh –p端口号 用户名@IP地址
ssh -p22 root@47.115.35.13 
Aa15361134471
```

#### 密钥登录

每次登录SH都需要输入密码很麻烦，而且可能不太安全。SSH还能使用另外一种登录方式，也就是使用密钥登录。这种登录方式需要客户端（自已操作的电脑）生成一堆公钥私钥对，然后将公钥添加到服务器中，这样下次就可以直接登录了。

首先生成SSH密钥，依照提示输入信息即可。默认生成在用户主目录中的.ssh文件夹中。带pub的是公钥，接下来需要添加到服务器中。

```
ssh-keygen
```

然后将本地公钥添加到服务器中，需要使用另一个命令：

```
scp -P 端口号 本地文件路径 用户名@远程服务器地址:远程路径
```

然后登陆服务器，找到复制进去的公钥，将公钥名字改为authorized_keys并添加到对应的.ssh文件夹中。然后退出SSH重新登陆试试，成功的话不需要输入密码就会直接进入远程服务器。



## 软件安装版本

> noinstall 绿色版
>
> setup 安装版
>
> Source code  (zip)   win源代码 
>
> Source code (tar.gz) linux 源代码
>
> checksum 校验检查 



## Window 命令行工具

### Chocolatey 安装

Install with powershell.exe

[Chocolatey](https://chocolatey.org/) 是 Windows 上的包管理器

[Chocolatey Software | Installing Chocolatey](https://chocolatey.org/install)

Run `Get-ExecutionPolicy`. If it returns `Restricted`, then run `Set-ExecutionPolicy AllSigned` or `Set-ExecutionPolicy Bypass -Scope Process`.

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

Now run the following command:



### Scoop 安装

[Scoop](http://scoop.sh/) 是一个 Windows 的命令行安装程序



### wget 安装

Linux系统中的wget是一个下载文件的工具，它用在命令行下。 对于Linux用户是必不可少的工具，我们经常要下载一些软件或从远程服务器恢复备份到本地服务器。 wget支持HTTP，HTTPS和FTP协议，可以使用HTTP代理。



## Window 软件

### OneQuick

#### 屏幕边缘

![image-20200503161852450](https://i.loli.net/2020/05/03/NuzElHGRWMbaq6D.png)

#### 用指定的搜索引擎

按两下 Ctrl+C 复制文本，再按下自定义按键触发运行

`+ 指定搜索引擎的首字母`

#### 快捷键

`win + C` 打开 cmder

#### 替换

`, g和 , ps` 

### WOX

`WIn + 空格` mcd

  







   

## 环境变量

通过 cmd 命令行进入指定目录后如果想查看该目录下的文件需要输入 dir 命令，很不方便，我们可以在 cmd 下打开文件夹图形界面：

explorer 目录

### cmd打开应用

- notepad 打开记事本
- mspaint 打开画图
- calc 打开计算机
- write 写字板
- sysdm.cpl 打开环境变量设置窗口

### sysdm.cpl

## 完成google匿名邮箱注册VIP

http://www.emailondeck.com/

abdirahima37@kmonkeyd.com

自动获取匿名的邮箱

[chrome-extension://nonmafimegllfoonjgplbabhmgfanaka/options.html?/signup](chrome-extension://nonmafimegllfoonjgplbabhmgfanaka/options.html?/signup)

填写邮箱

var inp = document.querySelectorAll('input') for(var i = 0;i < inp.length;i++){ document.querySelectorAll('input')[i].value = 'hewatoh506@hubopss.com' } document.querySelector("body > div > form > button").click()

点击电脑邮箱的邮件发送来的地址





```bat
for` `/r` `%a ``in` `(*.rar,*.zip) ``do` `"%Program Files%\7-zip\7zFM.exe"` `x ``"%~a"` `"%~dpa"` `-ibck
//D:\Program Files
```



## 字体安装



各种电脑系统安装使用经典楷体拼音字体的方法如下： • Windows通用：打开“控制面板”->“外观”->“字体”，将下载到的字体文件“经典楷体拼音.ttf”拖动复制到这里即可。 • Win7/Win8/Win10: 鼠标右键单击字体文件“经典楷体拼音.ttf，在弹出菜单中选择 "Install" 即可。 • Windows XP: 把字体文件“经典楷体拼音.ttf”复制到“C:\Windows\Fonts”文件夹下，系统会自动完成安装。 • iOS：双击字体文件“经典楷体拼音.ttf”打开字体册，然后点击“安装字体”按钮即可。

http://www.win10xiazai.com/win10/128.html



## VSCode代码截图  f1 polacode

Windows+R 命令输入mstsc命令，按Enter键即可



F12 或 Ctrl + Shift + I 打开开发者工具，在任意tab上按 Ctrl + Shift + P ，在弹出的输入框里输入 full size screenshot （其实不需要输入完整，可以自动补全），然后按回车即可



##  **Windows** + PrintScreen



## 环境变量

开机自动启动的目录

```cmd
shell:startup		
```

在cmd窗口中set设置的环境变量为临时变量，如：

```vb
set PATH=%PATH%;D:\Program Files\
```


使用setx设置为永久环境变量,适用于bat中：

```vb
setx PATH "%PATH%;D:\Program Files\"
```





## 新建ftp快捷方式

转载[Victor_Lv_](https://me.csdn.net/Lv_Victor) 最后发布于2016-03-10 20:57:17 阅读数 629 收藏

展开

```
新建ftp快捷方式，用文件夹方式打开。
方法转自百度知道：
右键 新建快捷键方式 在 项目位置填写：
c:\windows\explorer.exe ftp://192.168.0.123，其中后面的IP改成你要访问的ftp服务器地址
```





google搜索

**搜索结果要****搜索结果至少包含多个关键字中的任意一个**

GOOGLE用大写的OR表示逻辑“或”操作。OR一定是大写，小写查询时会被忽略。**求包含两个或两个以上关键字**

用“+”或空格，如“围城钱钟书”和“围城+钱钟书”同效，搜索结果也是一样的。

**搜索结果要求不包含某些特定信息**

搜索：校园民谣（空格） –高晓松，注意第一个关键词后面要空格。

**搜索结果至少包含多个关键字中的任意一个**

GOOGLE用大写的OR表示逻辑“或”操作。OR一定是大写，小写查询时会被忽略。





**用“+”和“-”减少冗余信息**

通常情况下，用一个关键词查询，会得到很多和查询目的不相关的冗余信息。“+”和“-”能起到缩小搜索结果的范围，以提高查询结果的命中率。

例：查询天龙八部具体是哪八部

如果你不知道八部中的任何一部，但知道这与佛教相关，可以排除与金庸小说相关的记录。可以用“[天龙八部]()+佛教–金庸”，可以迅速找到需要的资料。

**用句子做关键字，必须加英文引号。**

**1、对搜索的网站进行限制**

“site”表示搜索结果局限于某个具体的网站或者网站频道，如“sina.com.cn”,如果要排除某个网站或者域名范围内网页，只需要“-网站/域名”。

示例：搜索中文教育科研网站（edu.cn）上所有包含“钱钟书”和“杨绛”的页面。

搜索：钱钟书杨绛site:edu.cn”

**2、查询某一类文件**

“filetype：”搜索需要的查询内容结果以怎么样的文件格式体现，用得最多的文档搜索是PDF搜索。

示例：搜索关于儿童教育的pdf文档。

搜索：儿童教育filetype:PDF

**搜索的关键词包含在URL链接中**

“inurl”语法返回的网页链接中包含第一个关键字，后面的关键字则出现在链接中或者网页文档中。INURL语法和基本搜索语法的最大区别在于，前者通常能提供非常精准的专题资料。

示例：查询mv曲沧海一声笑

搜索：intul:mv沧海一声笑

**搜索的关键词包含在网页标题中**

“intitle”对网页标题栏进行查询,查询标题栏,通常可以找到高相关率的专题页面。

示例：查询明星刘若英的照片集

搜索：”intitle:刘若英写真”

百度

黑洞、旋转、**流星雨**，**失重****嚼薯片**



cmd +r msinfo32.exe ===  系统信息

cmd +r dxdiag.exe ===  DirectX诊断工具

netsh wlan show profile
netsh wlan export profile folder=C:\ key=clear



Microsoft DiskPart 版本 10.0.18362.1

Copyright (C) Microsoft Corporation.
在计算机上: CODER

DISKPART> list disk

  磁盘 ###  状态           大小     可用     Dyn  Gpt

--------  -------------  -------  -------  ---  ---

  磁盘 0    联机              476 GB   257 MB        *
  磁盘 1    联机               57 GB      0 B        *

DISKPART> select disk 1

磁盘 1 现在是所选磁盘。

DISKPART> clean

DiskPart 成功地清除了磁盘。

DISKPART>



Win10使用技巧

 var reg = new RegExp( ' ' , "g" );

  var newstr = s.replace( reg , '%20' );

  return newstr;

var arr = document.querySelectorAll('a')
for(let i = 0;i< arr.length;i++){ 
    arr[i].target='black'
 }



## 虚拟窗口

> 1 win+ctrl+D 新建虚拟桌面
> 2 win+ctr+F4 关闭当前虚拟桌面
> 3 win+ctrl+方向左键或右键 虚拟桌面之间切换



## [win10NVIDIA设置图标怎么隐藏 - 软件无忧](https://www.kafan.cn/A/732gpplwvl.html)



![sdafsad](https://gitee.com/code-dream/web/blob/master/images/banner.png)





## [【教程】使用gitee搭建免费的图床 - 阿飞云 - 博客园](https://www.cnblogs.com/aflyun/p/10010319.html)



## [apk如何去除强制更新_百度知道](https://zhidao.baidu.com/question/141055547932801525.html)

## [微软 PowerToys 小工具合集 - 免费给 Win10 加装各种增强新功能的效率利器 - 异次元软件下载](https://www.iplaysoft.com/powertoys.html)



## DOS控制台命令

netsh wlan show profiles来获取所有用户配置文件

netsh wlan show profile name="wifi名称" key=clear来查看我们想要的结果，格式一定不要错误，

releases



F12 或 Ctrl + Shift + I 打开开发者工具，在任意tab上按 Ctrl + Shift + P ，在弹出的输入框里输入 full size screenshot  （其实不需要输入完整，可以自动补全），然后按回车即可

(7条消息)如何在右键新建菜单里添加新建xmind文件_运维_刘凯的博客-CSDN博客: https://blog.csdn.net/cliukai/article/details/103569241



vscode如何添加鼠标右键打开文件夹

https://blog.csdn.net/zzsan/article/details/79305952



win10 ubuntu

C:\Users\Administrator\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc\LocalState\rootfs



[不丶懂](https://www.cnblogs.com/baby-zhude/)

我们不生产代码 我们只是代码的搬运工

[阿里巴巴矢量图标库批量下载](https://www.cnblogs.com/baby-zhude/p/11577017.html)

F12输入——

var iconList = document.querySelectorAll('.icon-gouwuche1');
for (var i = 0; i < iconList.length; i++) {
iconList[i].click();
}

 

目前只支持一次最大下载20个,所以:

var iconList = document.querySelectorAll('.icon-gouwuche1');
for (var i = 0; i <20; i++) {
iconList[i].click();
}

下一批20个:

var iconList = document.querySelectorAll('.icon-gouwuche1');
for (var i = 20; i < 40; i++) {
iconList[i].click();
}

鼠标右键的快捷键
1、右边win键的右边的键；
2、Shift+F10。





C:\Users\Administrator\Desktop>





windows cmd 查看文件目录树
原创Inside_Zhang 最后发布于2017-04-14 11:00:46 阅读数 12683  收藏
 原创 3757   粉丝 5009   获赞 1771   评论 675   访问 1083万+  
展开
windows + R ⇒ 输入 cmd ⇒ 进入 windows 命令行界面：

tree/?：命令提示；
tree：不输入任何参数，输出一棵目录树
不显示文件，只显示目录；
tree/F：递归显示目录结构；
显示目录，也显示文件；
tree /F，在给出项目文件说明时，会十分有用；

1. 重定向到文本文件
   tree /f > info.txt
   tree > info.txt





echo.>c:/abc.txt （不完美。含有一个两空行）

type nul>c:/abc.txt （完美）

rem.>c:/abc.txt （完美）

cd.>c:/abc.txt （完美）

copy nul>c:/abc.txt（不完美，有多余的文字）

创建文件---------------------------------------------------

第一种方法：
echo ...... > A.txt 重定向输出，此时创建文本文件A.txt;
echo ...... >>A.txt 向A.txt文件中追加信息.....;


第二种方法：
copy con A.txt 创建A.txt文本文件;
.......^Z 　　　　　 　输入内容....;
　　　 按CTRL+Z键，之后再回车；

第三种方法：
edit A.txt 编辑A.txt文本文件，调用command.com中创建文本文件的命令，
如果A.txt文件不存在，则创建文件
........ 输入内容，保存。

第四种方法：

type nul>filename 可建立一个空文件中，在批处理中经常用。

copy nul A.txt 可建立一个空文件中，在批处理中经常用，也可清空一个文件。

mkdir 目录名；

删除目录：

rmdir 目录名；































```
 if (location.href.indexOf("preview/download_preview.jsp") > 0) {
            location.href = location.href.replace("preview/download_preview.jsp", "download.jsp")
        }
        
location.href = location.href.replace("preview/download_preview.jsp", "download.jsp")       
```





## CMD命令开启防火墙

**开启防火墙：**

```
netsh advfirewall set allprofiles state on
```

**关闭防火墙：**

```
netsh advfirewall set allprofiles state off
```





http://umooc.gdgm.cn/meol/common/script/

?fileid=96639&resid=28903&lid=12410

VSCode代码截图 f1 polacode





## F12 或 Ctrl + Shift + I 打开开发者工具，在任意tab上按 Ctrl + Shift + P ，在弹出的输入框里输入 full size screenshot （其实不需要输入完整，可以自动补全），然后按回车即可



 **Windows** + **PrintScreen** 





开机自动启动的目录

```cmd
shell:startup		
```



Windows linux:子系统



在cmd窗口中set设置的环境变量为临时变量，如：



```vb
set PATH=%PATH%;D:\Program Files\
```


使用setx设置为永久环境变量,适用于bat中：



```vb
setx PATH "%PATH%;D:\Program Files\"
```





## 新建ftp快捷方式

转载[Victor_Lv_](https://me.csdn.net/Lv_Victor) 最后发布于2016-03-10 20:57:17 阅读数 629 收藏

展开

```
新建ftp快捷方式，用文件夹方式打开。
方法转自百度知道：
右键 新建快捷键方式 在 项目位置填写：
c:\windows\explorer.exe ftp://192.168.0.123，其中后面的IP改成你要访问的ftp服务器地址
```





## google搜索

**搜索结果要****搜索结果至少包含多个关键字中的任意一个**

GOOGLE用大写的OR表示逻辑“或”操作。OR一定是大写，小写查询时会被忽略。**求包含两个或两个以上关键字**

用“+”或空格，如“围城钱钟书”和“围城+钱钟书”同效，搜索结果也是一样的。

**搜索结果要求不包含某些特定信息**

搜索：校园民谣（空格） –高晓松，注意第一个关键词后面要空格。

**搜索结果至少包含多个关键字中的任意一个**

GOOGLE用大写的OR表示逻辑“或”操作。OR一定是大写，小写查询时会被忽略。



**用“+”和“-”减少冗余信息**

通常情况下，用一个关键词查询，会得到很多和查询目的不相关的冗余信息。“+”和“-”能起到缩小搜索结果的范围，以提高查询结果的命中率。

例：查询天龙八部具体是哪八部

如果你不知道八部中的任何一部，但知道这与佛教相关，可以排除与金庸小说相关的记录。可以用“[天龙八部]()+佛教–金庸”，可以迅速找到需要的资料。

**用句子做关键字，必须加英文引号。**

**1、对搜索的网站进行限制**

“site”表示搜索结果局限于某个具体的网站或者网站频道，如“sina.com.cn”,如果要排除某个网站或者域名范围内网页，只需要“-网站/域名”。

示例：搜索中文教育科研网站（edu.cn）上所有包含“钱钟书”和“杨绛”的页面。

搜索：钱钟书杨绛site:edu.cn”

**2、查询某一类文件**

“filetype：”搜索需要的查询内容结果以怎么样的文件格式体现，用得最多的文档搜索是PDF搜索。

示例：搜索关于儿童教育的pdf文档。

搜索：儿童教育filetype:PDF

**搜索的关键词包含在URL链接中**

“inurl”语法返回的网页链接中包含第一个关键字，后面的关键字则出现在链接中或者网页文档中。INURL语法和基本搜索语法的最大区别在于，前者通常能提供非常精准的专题资料。

示例：查询mv曲沧海一声笑

搜索：intul:mv沧海一声笑

**搜索的关键词包含在网页标题中**

“intitle”对网页标题栏进行查询,查询标题栏,通常可以找到高相关率的专题页面。

示例：查询明星刘若英的照片集

搜索：”intitle:刘若英写真”

百度

黑洞、旋转、**流星雨**，**失重****嚼薯片**



## 破解wiff

Contents:

安装kail linux

WEP模式直接排除（淘汰）

默认使用WPA/WPA-PSK 的加密方式

第一步抓到握手包

查看无线适配器

```
sudo iwconfig
```

开启监听模式

```
sudo airmon-ng start wlan0
```

扫描周围的Wiff信号

```
sudo airodump-ng wlan0mon
```

Wireless Attacks

手动挡工具

自动挡工具



## cmd

定时自动关机
 shutdown -s -t 3600（秒）
 下滑关机
 slidetoshutdown
 取消关机
 shutdown -a
 要在 晚上23：00准时关机你可以输入如下命令
 at 23:00 shutdown -s
 重启
 shutdown -r
 设置关机倒计时
 shutdown -t 时间

 shutdown /help



http://markjour.com/article/cmd-create-file.html

cd.>a.text

Win10 cmd命令大全分享：打开系统组件

appwiz.cpl------------添加删除程序
control userpasswords2--------用户帐户设置
cleanmgr-------垃圾整理
CMD--------------命令提示符可以当作是 Windows 的一个附件，Ping，Convert 这些不能在图形环境下 使用的功能要借助它来完成。
cmd------jview察看Java虚拟机版本。
command.com------调用的则是系统内置的 NTVDM，一个 DOS虚拟机。它完全是一个类似 Virtual PC 的 虚拟环境，和系统本身联系不大。当我们在命令提示符下运行 DOS 程序时，实际上也 是自动转移到 NTVDM虚拟机下，和 CMD 本身没什么关系。
calc-----------启动计算器
chkdsk.exe-----Chkdsk磁盘检查
compmgmt.msc---计算机管理
conf-----------启动 netmeeting
control userpasswords2-----User Account 权限设置
devmgmt.msc--- 设备管理器
diskmgmt.msc---磁盘管理实用程序
dfrg.msc-------磁盘碎片整理程序
drwtsn32------ 系统医生
dvdplay--------启动Media Player
dxdiag-----------DirectX Diagnostic Tool
gpedit.msc-------组策略编辑器
gpupdate /target:computer /force 强制刷新组策略
eventvwr.exe-----事件查看器
explorer-------打开资源管理器
logoff---------注销命令
lusrmgr.msc----本机用户和组
msinfo32---------系统信息
msconfig---------系统配置实用程序
net start (servicename)----启动该服务
net stop (servicename)-----停止该服务
notepad--------打开记事本
nusrmgr.cpl-------同control userpasswords，打开用户帐户控制面板
Nslookup-------IP地址侦测器
oobe/msoobe /a----检查XP是否激活
perfmon.msc----计算机性能监测程序
progman--------程序管理器
regedit----------注册表编辑器
regedt32-------注册表编辑器
regsvr32 /u *.dll----停止dll文件运行
route print------查看路由表 
rononce -p ----15秒关机
rsop.msc-------组策略结果集
rundll32.exe rundll32.exe %Systemroot%System32shimgvw.dll,ImageView_Fullscreen----启动一个空白的Windows 图片和传真查看器
secpol.msc--------本地安全策略
services.msc---本地服务设置
sfc /scannow-----启动系统文件检查器
sndrec32-------录音机
taskmgr-----任务管理器（适用于2000／xp／2003）
tsshutdn-------60秒倒计时关机命令
winchat--------XP自带局域网聊天
winmsd---------系统信息
winver-----显示About Windows 窗口
wupdmgr-----------Windows Update 

Win10 cmd命令大全分享：对系统进行操作

AT 计划在计算机上运行的命令和程序。
ATTRIB 显示或更改文件属性。
BREAK 设置或清除扩展式 CTRL+C 检查。
CACLS 显示或修改文件的访问控制列表(ACLs)。
CALL 从另一个批处理程序调用这一个。
CD 显示当前目录的名称或将其更改。
CHCP 显示或设置活动代码页数。
CHDIR 显示当前目录的名称或将其更改。
CHKDSK 检查磁盘并显示状态报告。
CHKNTFS 显示或修改启动时间磁盘检查。
CLS 清除屏幕。
CMD 打开另一个 Windows 命令解释程序窗口。
COLOR 设置默认控制台前景和背景颜色。
COMP 比较两个或两套文件的内容。
COMPACT 显示或更改 NTFS 分区上文件的压缩。
CONVERT 将 FAT 卷转换成 NTFS。您不能转换当前驱动器。
COPY 将至少一个文件复制到另一个位置。
DATE 显示或设置日期。
DEL 删除至少一个文件。
DIR 显示一个目录中的文件和子目录。
DISKCOMP 比较两个软盘的内容。
DISKCOPY 将一个软盘的内容复制到另一个软盘。
DOSKEY 编辑命令行、调用 Windows 命令并创建宏。
ECHO 显示消息，或将命令回显打开或关上。
ENDLOCAL 结束批文件中环境更改的本地化。
ERASE 删除至少一个文件。
EXIT 退出 CMD.EXE 程序(命令解释程序)。
FC 比较两个或两套文件，并显示不同处。
FIND 在文件中搜索文字字符串。
FINDSTR 在文件中搜索字符串。
FOR 为一套文件中的每个文件运行一个指定的命令。
FORMAT 格式化磁盘，以便跟 Windows 使用。
FTYPE 显示或修改用于文件扩展名关联的文件类型。
GOTO 将 Windows 命令解释程序指向批处理程序中某个标明的行。
GRAFTABL 启用 Windows 来以图像模式显示扩展字符集。
HELP 提供 Windows 命令的帮助信息。
IF 执行批处理程序中的条件性处理。
LABEL 创建、更改或删除磁盘的卷标。
MD 创建目录。
MKDIR 创建目录。
MODE 配置系统设备。
MORE 一次显示一个结果屏幕。
MOVE 将文件从一个目录移到另一个目录。
PATH 显示或设置可执行文件的搜索路径。
PAUSE 暂停批文件的处理并显示消息。
POPD 还原 PUSHD 保存的当前目录的上一个值。
PRINT 打印文本文件。
PROMPT 更改 Windows 命令提示符。
PUSHD 保存当前目录，然后对其进行更改。
RD 删除目录。
RECOVER 从有问题的磁盘恢复可读信息。
REM 记录批文件或 CONFIG.SYS 中的注释。
REN 重命名文件。
RENAME 重命名文件。
REPLACE 替换文件。
RMDIR 删除目录。
SET 显示、设置或删除 Windows 环境变量。
SETLOCAL 开始批文件中环境更改的本地化。
SHIFT 更换批文件中可替换参数的位置。
SORT 对输入进行分类。
START 启动另一个窗口来运行指定的程序或命令。
SUBST 将路径跟一个驱动器号关联。
TIME 显示或设置系统时间。
TITLE 设置 CMD.EXE 会话的窗口标题。
TREE 以图形模式显示驱动器或路径的目录结构。
TYPE 显示文本文件的内容。
VER 显示 Windows 版本。
VERIFY 告诉 Windows 是否验证文件是否已正确写入磁盘。
VOL 显示磁盘卷标和序列号。
XCOPY 复制文件和目录树。

以上就是Win10 cmd命令大全分享！
相关资讯





微软从 Windows 8开始，为 Windows 增加了一项不需要第三方软件的快捷键屏幕截图功能，该功能被延续到了Windows 10 系统当中。当我们需要对屏幕进行截图时，只需按下 Windows + PrintScreen 键，屏幕会变暗一下以提示用户截图完成，并将截取到的 Windows 屏幕图片保存到 此电脑— 图片 — 屏幕截图 文件夹当中。



C:\Users\Administrator\Pictures\Screenshots





## 快捷键

Ctrl+Alt+Del 组合键可以调出windows任务管理器外，
Ctrl+Shift+Esc”组合键一样能启动任务管理器

主键盘区：
Esc 键：escape，退出键。
Tab 键：tabulator key，跳格键，在文本编辑软件中增加四个空格，Windows中可用于切换屏幕上的焦点。
Ctrl 键：control，控制键。
Shift 键：上档键。
Alt 键：换档键。
Caps Lock 键：大写锁定键，用于切换系统大写锁定。
Windows 键：键盘上画着一个Windows视窗图标的键。按这个键可以打开开始菜单。
BackSpace 键：退格键，用于删除当前光标前的字符；退格键 在Win资源管理器后退；打开、另存为界面表示返回上级。
Enter键：回车键，换行，在Windows资源管理器表示打开文件（夹）或选中菜单选项；在Cmd[DOS Mode]表执行命令。
Space：空格键 如果活动选项是单选或复选框，则选中或清除框中的√
功能键区：
F1 帮助
F2 重命名、部分主板开机时的BIOS快捷键
F3 查找
F4 地址栏
F5 刷新
F6 切换（到地址栏）
F9 部分主板开机引导
F7、8 自定义
F10 + Shift或Alt 右键菜单
F11全屏
F12 部分主板开机引导
系统键区：
PrintScreen键：打印屏幕。按下该键后系统会自动全屏截图并保存至剪切板中（无任何提示可Ctrl+V贴至画图、QQ、Word等，BIOS中截的图可以在Windows等OS中查看），配合Alt键使用可以截取当前焦点所在的活动窗口。
ScrollLock键：滚动条锁定键，配合ScrollLock指示灯来控制和显示当前滚动条锁定状态。常见的软件中只有Excel支持此功能，使用频率极低。
Pause|Break键：暂停/中断键。当需要查看主板自检信息时，可以在自检时按下该键，自检结束后将不会自动进入下一步启动过程，而是等待用户操作。VBS（按键精灵等）、VBA编程中为暂停脚本。
编辑键区：
Insert键：插入/改写键。使用该键可以切换当前文本输入状态是插入状态还是改写状态。Word、写字板、记事本等文字处理和某些程序编译器支持该功能。
Delete键：删除键，文本编辑可以删除光标后而不是前的字符，文件浏览可以删除选中的文件。部分主板通过该键进入BIOS。
Delete+Shift删除被选中的项目，如果是文件，将被直接删除而不是放入回收站
Home键：起始键，用于将光标移至行开头。浏览网页时，可以返回网页最上端。
End键：结尾键，用于将光标移至结尾。浏览网页时，可以将页面滚至最下方。
Page Up键：向上翻页键。
PageDown键：向下翻页键。
数字键盘区：
NumLock键：数字锁定键，与NumLock指示灯对应，按下该键可以控制NumLock指示灯的状态。当NumLock指示灯点亮时，小键盘区用于输入数字；当NumLock指示灯熄灭时，小键盘区可代替编辑键区使用。
107键键盘附加按键：
WakeUp键：唤醒键
Sleep键：睡眠键
Power键：电源键
Fn在Win中编辑
F1 显示帮助。
F2 重命名。
F3 焦点在桌面时打开“查找：所有文件” 对话框（WIN10不适用）；Win资源管理器中切至搜索栏。
F4+Alt关闭窗口【焦点在桌面时是关机界面，在网页则关闭当前标签或浏览器】。
F5 刷新。
F6切换。焦点切到任务栏或活动窗口中的地址栏。F6或TAB键在左右窗格、地址栏、搜索栏、间切换
F10+Shift =Alt+F10 Application键激活当前焦点的右键菜单。（word中Shift+F10出现右键快捷菜单）
F11全屏、Esc退出。【Windows Explorer（即“计算机”点开的窗口，下简称Win资源管理器）是隐藏地址栏和树状图；网页隐藏搜索、收藏、插件、侧边、状态栏；媒体播放界面同理】
F12在Excel 或Word文档是另存为；网页页面是打开调试环境（审查元素）。
Up、Down、Left、Right 方向键编辑
方向键本键如果活动选项是选项按钮或文件则为移动焦点；
方向键 + Win键（简称Win键）使窗口全屏、最小化、靠左半边、靠右半边（部分版本不支持）；
方向键+Shift键将连续的文字或文件选中
方向键（左右）+Ctrl键 在英文单词或中文词语间跳跃
方向键（上下）+Ctrl键 在段落开头间跳跃
Ctrl键编辑
系统类
Ctrl+Alt+Delete打开安全选项（XP及以下为任务管理器，DOS系统中为重启）
Ctrl+Shift+Esc打开任务管理器 （Win9x中打开开始菜单）
Ctrl+Shift+N 新建一个新的文件夹（Win XP不适用）
Ctrl+Shift切换中英文输入法。
Ctrl+Space（空格）的作用不一样，是切换输入法和非输入法
Ctrl+Tab焦点向下一项移动
Ctrl+Shift+Tab=Shift+Tab焦点向上一项移动
Ctrl+F4 Win资源管理器中切至地址栏；媒体播放中停止。
　　
文字处理类
Ctrl+a 全选All
Ctrl+b 粗体 Bold
Ctrl+c 或insert 拷贝 Copy
Ctrl+d 字体格式 Decorate
Ctrl+e 居中对齐 Encenter
Ctrl+f 查找 Find
Ctrl+g 定位 Get address
Ctrl+h 替换 Huan
Ctrl+i 斜体 italic
Ctrl+j 两端对齐 Justify
Ctrl+k 超级链接 King Link
Ctrl+l 左对齐 Left Ailgn
Ctrl+m 左缩进 M……
Ctrl+n 新建 New 或Ctrl+Shift+n
Ctrl+o 打开 Open
Ctrl+p 打印 Print
Ctrl+r 右对齐 Right Align
Ctrl+s 保存 Save
Ctrl+t 首行缩进 =Tab
Ctrl+u 下划线 Underline
Ctrl+v = Shift + Insert 粘贴 Paste （在c边上故随意赋键)
Ctrl+w关闭当前的窗口、标签页、工作、文件或停止媒体播放Work
Ctrl+x 剪切
Ctrl+y= Alt+Shift + Backspace重复 （反撤销）
Ctrl+z= Alt + Backspace撤销


Ctrl+F4 Word中关闭当前应用程序中的当前文件。
Ctrl+F6 Word中切换到当前应用程序中的下一个文本。
Alt + 双击超链接执行匹配的命令（或选择选项）
Ctrl + 双击超链接打开链接
Shift word等Micro Office系列软件中按下不放，可以跳过自启动的宏
WIN键编辑
WindowsF1帮助给出的Win快捷键
WindowsF1帮助给出的Win快捷键
可以使用 Microsoft自然键盘或含有 Windows徽标键的其他任何兼容键盘的以下快捷键。
Win键
Win键


Win键+ 向上键最大化窗口
Win键+ 向左键将窗口左移
Win键+ 向右键将窗口右移
Win键+ 向下键最小化窗口
Win键+ F1 显示“帮助”
Win键+PrintScreen键截取当前屏幕到剪贴板，并保存截屏图片文件到“图片”文件夹中。（WIN8/10）
Win键或Ctrl+Esc打开开始菜单
Win键+Break打开“系统属性”对话框
Win键+Pause显示“系统属性”对话框
Win键+Tab循环切换任务栏上的程序（win7、win8）（windowsXP不适用）
Win键 + Tab使用 Aero Flip 3-D 循环切换任务栏上的程（win7）（windowsxp不适用）
Win键 +Tab+Ctrl通过 Aero Flip 3-D 使用方向键循环切换任务栏上的程序 （win7）
Win键 + Space如果开启了AERO效果，预览桌面 （win7）（在win10此项是小界面切换输入法）
Win键+ Home最小化除活动窗口之外的所有窗口（win7）（windowsXP不适用
主键盘区上的数字
Win键+数字启动锁定到任务栏中的由该数字所表示位置处的程序。如果该程序已在运行，则切换到该程序
Win键+Shift+数字启动锁定到任务栏中的由该数字所表示位置处的程序的新实例
Win键+Alt+ 数字打开锁定到任务栏中的第该数字个程序的跳转列表(Jump List)）


Win键+B选中桌面右下方托盘栏或任务栏Progress Bar
Win键+D显示桌面Desktop
Win键+E打开Windows资源管理器Explorer【即我的电脑、计算机】
Win键+F打开“查找：所有文件”对话框（win10中为打开反馈中心）（Win资源管理器中为切至查找栏）
Win键+F+Ctrl搜索计算机（如果已连接到网络）
Win键+G循环切换小工具（win7）（win10打开xbox菜单）（windowsXP不适用）
Win键+I 打开“设置”（win10）
Win键+L 锁定计算机或切换用户
Win键+M最小化所有窗口
Win键+Shift+M将最小化的窗口还原到桌面
WIN键+P多荧幕\投影仪选项选择演示显示模式。（WIN7）出现菜单后再摁Win+P选择选项，放开Win即可 确定。也可摁一次然后方向键选择回车键确定。
Win键+R打开“运行”对话框
WIN键+T显示任务栏当前所用程序的任务栏缩略图，再按一次切换到其他缩略图。（QWIN7）
Win键+U打开辅助工具管理器、轻松访问中心
Win键+X打开 Windows 移动中心（win7）（win10唤起开始按钮右键菜单）（windowsXP不适用）


Alt键编辑
Alt+Space 打开活动窗口最左上角的菜单
Alt+Space+N 最小化活动窗口
Alt+Tab切换当前程序 （加Shift反向）
Alt+Esc 切换当前程序 （加Shift反向）
Alt+Enter 将windows下运行的MSDOS窗口在窗口和全屏幕状态间切换
Alt+Print Screen将当前活动程序窗口以图像方式拷贝到剪贴板（加shift 可以跳到前一个窗口）
向后移动到上一个视图 ALT+左箭头
向前移动到上一个视图 ALT+右箭头
Shift键编辑
关闭所选文件夹及其所有父文件夹
按住 Shift键再单击“关闭按钮（仅适用于“我的电脑”）
系统自带放大镜程序编辑
旧版放大镜
Windows+PRINT SCREEN 将屏幕复制到剪贴板（包括鼠标光标）
Windows+SCROLL LOCK 将屏幕复制到剪贴板（不包括鼠标光标）
Windows+PAGE UP 切换反色。
Windows+ PAGE DOWN 切换跟随鼠标光标
Windows+向上箭头 增加放大率
Windows+向下箭头 减小放大率
新版放大镜
Windows给出的放大镜快捷键
Windows给出的放大镜快捷键
Win+ 唤起放大镜；放大
Win- 缩小
（设置中单次按键倍率可调）
其余见图
小键盘编辑
NUM LOCK+负号(-)折叠所选的文件夹
NUM LOCK+乘号(*)展开所选的文件夹下的所有文件及文件夹
NUM LOCK+加号(+) 展开所选的文件夹
IE浏览器编辑
显示前一页（前进键） ALT+RIGHT ARROW
显示后一页（后退键） ALT+LEFT ARROW
在页面上的各框架中切换 （加shift反向）Ctrl+TAB
这个键用来打开IE中的地址栏列表，要关闭IE窗口，可以用Alt+F4组合键 F4
刷新 F5
强行刷新 Ctrl+F5
可以快速在资源管理器及IE中定位到地址栏 F6
激活程序中的菜单栏 F10
可以使当前的资源管理器或IE变为全屏显示 F11
执行菜单上相应的命令 ALT+菜单上带下划线的字母
关闭多文档界面程序中的当前窗口 Ctrl+ F4
关闭当前窗口或退出程序 ALT+ F4
添加当前页面到收藏夹 Ctrl+ D
显示所选对话框项目的帮助 F1
显示当前窗口的系统菜单 ALT+空格键
显示所选项目的快捷菜单 Shift+ F10
显示“开始”菜单 Ctrl+ ESC
显示多文档界面程序的系统菜单 ALT+连字号(-)
切换到上次使用的窗口 按住ALT然后重复按TAB，
切换到另一个窗口 ALT+ TAB
在后台打开一个页面 Ctrl+ 鼠标左键单击
在新窗口中打开一个页面 Shift+ 鼠标左键单击
Windows资源管理器编辑
插入光盘时不用“自动播放”功能 按住 Shift插入 CD-ROM
复制文件 按住Ctrl拖动文件
创建快捷方式按住 Ctrl+Shift拖动文件 或按住 ALT拖动文件
立即删除某项目而不将其放入回收站 Shift+DELETE
显示“查找：所有文件” F3
显示项目的快捷菜单 APPLICATION键
刷新窗口的内容 F5
重命名项目 F2
重命名项目 F2 重命名时按Tab键可重命名下一文件，不用按回车+向下+F2
选择所有项目 Ctrl+ A
查看项目的属性 ALT+ ENTER或 ALT+双击
辅助选项编辑
Num Lock 键五秒钟 切换“切换键”的开和关。
按住键盘右侧Shift 八秒 切换筛选键开关
Shift 键五次 切换“粘滞键”的开和关。
（以上三种可在“控制面板”选择是否开启。
左ALT+左Shift+PRINT SCREEN 切换高对比度开关
左ALT+左Shift+NUM LOCK 切换鼠标键开关
NUM LOCK 五秒切换切换键开关
右侧 Shift 键八秒钟 切换“筛选键”的开和关。
左 ALT + 左 Shift + PRINT SCREEN 切换“高对比度”的开和关。
左 ALT + 左 Shift + NUM LOCK 切换“鼠标键”的开和关。
WIN+ U 打开“辅助功能管理器”。
Win10编辑
Win键+字母：
Win键+A：激活操作中心
Win键+B：聚焦于右下角托盘区
Win键+C：通过语音激活Cortana
Win键+D：显示桌面
Win键+E：打开文件管理器
Win键+G：打开Xbox游戏录制工具栏，供用户录制游戏视频或截屏激活截屏功能
Win键+H：激活Windows10应用的分享功能
Win键+I：打开Windows10设置
Win键+K：激活无线显示器连接或音频设备连接
Win键+L：锁定屏幕
Win键+P：投影屏幕
Win键+R：运行
Win键+S：搜索、激活Cortana（微软小娜）
Win键+T：快速切换任务栏程序
Win键+V：打开云剪贴板
Win键+X：打开高级用户功能

　　Win键+非字母：
Win+Break：看配置
Win键+Space：快速显示桌面
Win键+Tab：激活任务视图
Win键+分号：调出 Emoji 表情
Win键+1/2/3：打开任务栏中固定的程序，1代表任务栏中第一个应用图标
Win键+左/右/上/下：移动应用窗口
Win键+Shift+左箭头：移动到左边屏幕。
Win键+Shift+右箭头：移动到右边屏幕。
Win键+Shift+S：Windows自带截图
Win键+Ctrl+D：创建一个新的虚拟桌面
Win键+Ctrl+F4：关闭虚拟桌面
Win键+Ctrl+左/右：切换虚拟桌面

　　Ctrl键
Ctrl+Shift+N：新建文件夹。
Ctrl+shift+左键：以管理员身份运行。
Ctrl+Shift+Esc：任务管理器
Ctrl+Shift+Del：安全选项列表
Ctrl+W：关闭当前窗口。
Ctrl+F：定位到搜索框。

　　Alt键
Alt+D：定位到地址栏。
Alt+向左键：查看上一个文件夹。
Alt+向右键：查看下一个文件夹。
Alt+向上键：查看父文件夹。

　　Shift键
Shift+右键点击目录：在此处打开命令行窗口选项。
Shift+右键点击文件：发送到菜单。
Shift+点击任务栏（已经打开的）图标打开新窗口

　　鼠标
在同一分区目录间拖曳，默认执行剪切操作，按下Ctrl+拖曳，执行拷贝操作。
在不同分区间进行拖曳，默认执行拷贝操作，按下Shift+拖拽，执行剪切操作。
Alt+拖曳，创建快捷方式。
[2] 
WinXP编辑
Ctrl + Shift + 任何箭头键 突出显示一块文本。
Shift + 任何箭头键 在窗口或桌面上选择多项，或者选中文档中的文本。
Ctrl + A 选中全部内容。
F3 搜索文件或文件夹。
Alt + Enter 查看所选项目的属性。
Alt + F4 关闭当前项目或者退出当前程序。
Alt + 空格键 为当前窗口打开快捷菜单。
Ctrl + F4 在允许同时打开多个文档的程序中关闭当前文档。
Alt + Tab 在打开的项目之间切换。
Alt + Esc 以项目打开的顺序循环切换。
F6 在窗口或桌面上循环切换屏幕元素。
F9+FN键是键盘锁定
F4 显示“我的电脑”和“Windows 资源管理器”中的“地址”栏列表。
Shift + F10 显示所选项的快捷菜单。
Alt + 空格键 显示当前窗口的“系统”菜单。
Ctrl + Esc 显示“开始”菜单。
ALT + 菜单名中带下划线的字母 显示相应的菜单。
在打开的菜单上显示的命令名称中带有下划线的字母 执行相应的命令。
F10 激活当前程序中的菜单条。
右箭头键 打开右边的下一菜单或者打开子菜单。
左箭头键 打开左边的下一菜单或者关闭子菜单。
F5 刷新当前窗口。
BackSpace 在“我的电脑”或“Windows 资源管理器”中查看上一层文件夹。
Esc 取消当前任务。
将光盘插入到 CD-ROM 驱动器时按 Shift 键 阻止光盘自动播放。
对话框编辑
取消当前任务 ESC
如果当前控件是个按钮，要单击该按钮。
如果当前控件是个复选框，要选择或清除该复选框
或者如果当前控件是个选项按钮，要单击该选项空格键
单击相应的命令 ALT+带下划线的字母
单击所选按钮 ENTER
在选项上向后移动 Shift+ TAB
在选项卡上向后移动 Ctrl+ Shift+ TAB
在选项上向前移动 TAB
在选项卡上向前移动 Ctrl+ TAB
如果在“另存为”或“打开”对话框中选择了某文件夹，要打开上一级文件夹
BACKSPACE
在“另存为”或“打开”对话框中打开“保存到”或“查阅” F4
刷新“另存为”或“打开”对话框 F5
自然键盘编辑
WIN 显示或隐藏"开始"菜单。
WIN+ BREAK 显示"系统属性"对话框。
WIN+ D 显示桌面。
WIN+ M 最小化所有窗口。
WIN+ Shift + M 还原最小化的窗口。
WIN+ E 打开"我的电脑"。
WIN+ F 打开windows反馈页面，F代表feedback。
Ctrl+WIN+ F 搜索计算机。
WIN+ F1 显示 Windows 帮助。
WIN+ L 如果连接到网络域，则锁定您的计算机，或者如果没有连接到网络域，则切换用户。
WIN+ R 打开"运行"对话框。
KEY 显示所选项的快捷菜单。
WIN+ U 打开"工具管理器"。
对话框编辑
Ctrl + Tab 在选项卡之间向前移动。
Ctrl + Shift +Tab 在选项卡之间向后移动。
Tab 在选项之间向前移动。
Shift + Tab 在选项之间向后移动。
ALT + 带下划线的字母 执行相应的命令或选中相应的选项。
Enter 执行活选项动或按钮所对应的命令。
空格键 如果活选项动是复选框，则选中或清除该复选框。
箭头键 活选项动是一组选项按钮时，请选中某个按钮。
F1 显示帮助。
F4 显示当前列表中的项目。
生僻快捷键编辑
Windows中的快捷键我们都很熟悉了，可是下面这些快捷键你平时用过吗？与普通的快捷键相比，它们的使用方法有些特别：这些键不能同时按下，而是要用两步或三步的连续操作，才能实现一项功能。虽然如此，使用这些快捷键也比使用鼠标方便。
Alt+空格→X 最大化当前窗口
Alt+空格→N 最小化当前窗口
提示：“Alt+空格→X”表示先按下“Alt+空格”组合键，然后松开组合键，再按下X键。下面“→”符号均表示先松开符号前按下的键，再按下符号后面的键。
在桌面或文件夹窗口中可使用以下快捷键（注意是文件夹窗口而不是具体的文件夹）：
右键→I→N 按名称排列图标
右键→I→T 按类型排列图标（呵呵，搞IT的应该记得住吧）
右键→I→Z 按大小排列图标
右键→I→D 按日期排列图标
右键→W→F 新建文件夹
右键→R 若在桌面则打开“显示属性”在文件夹则打开该文件夹的属性
右键→E 刷新当前窗口，效果等同F5
提示：这里的“右键”指的是主键盘区最下排右侧的Windows徽标键和Ctrl之间的那个键。
如果当前窗口是某个具体文件或文件夹：
右键→S 创建当前文件或目录的快捷方式
右键→R 查看当前文件或目录属性（相当于Alt+Enter）
右键→O 打开当前文件或目录（相当于回车）
右键→T→A 发送当前文件或目录到软盘
注意：有些软件可能会在右键里增加一些菜单，这些菜单的快捷键可能会与系统快捷键发生冲突。比如WinRAR会在文件或文件夹的右键菜单中增加一个“添加到”的菜单，该菜单的快捷键S会与系统右键菜单“创建快捷方式（S）”发生冲突。如果要去掉这些“外来”的右键菜单，我们可以打开WinRAR，在菜单栏上依次点击“选项→设置”，打开“设置”对话框，在“综合”选项卡中点击“选择关联菜单项目”按钮，在打开的对话框中清空所有选项前的复选框即可。
如果当前窗口是记事本：
右键→U 撤消操作，效果等同与Ctrl+Z
右键→P 粘贴，效果等同与Ctrl+V
右键→A 选中全部文字，效果等同于Ctrl+A
使用“我的电脑”和“Windows资源管理器”的快捷键
目的快捷键
关闭所选文件夹及其所有父
文件夹按住 Shift键再单击“关闭按钮（仅适用于“我的电脑”）
向后移动到上一个视图 ALT+左箭头
向前移动到上一个视图 ALT+右箭头
查看上一级文件夹 BACKSPACE
其实，这些快捷键大家都可以在相关程序的右键菜单中找到，在这里只是选择了几个比较实用的归纳了一下，你也可以自己研究。比如当前窗口是某个文件或文件夹，那么用“右键→M”就可以对该文件或文件夹进行重命名操作。不同的程序有不同的快捷键，大家可以自己研究试用，举一反三。
其他资料编辑
一、常见用法：
F1 显示当前程序或者windows的帮助内容。
F2 当你选中一个文件的话，这意味着“重命名”
F3 当你在桌面上的时候是打开“查找：所有文件” 对话框
F10或ALT 激活当前程序的菜单栏
Win键或Ctrl+ESC 打开开始菜单
Ctrl+ALT+DELETE 在win9x中打开关闭程序对话框
DELETE 删除被选择的选择项目，如果是文件，将被放入回收站
Shift+DELETE 删除被选择的选择项目，如果是文件，将被直接删除而不是放入回收站
Ctrl+N 新建一个新的文件
Ctrl+O 打开“打开文件”对话框
Ctrl+P 打开“打印”对话框
Ctrl+S 保存当前操作的文件
Ctrl+X 剪切被选择的项目到剪贴板
Ctrl+INSERT 或 Ctrl+C 复制被选择的项目到剪贴板
Shift+INSERT 或 Ctrl+V 粘贴剪贴板中的内容到当前位置
ALT+BACKSPACE 或 Ctrl+Z 撤销上一步的操作
Ctrl+Y 重做上一步被撤销的操作
ALT+Shift+BACKSPACE重做上一步被撤销的操作
Win键+M 最小化所有被打开的窗口。
Win键+Ctrl+M 重新将恢复上一项操作前窗口的大小和位置
Win键+E 打开资源管理器
Win键+F 打开“查找：所有文件”对话框
Win键+R 打开“运行”对话框
Win键+BREAK 打开“系统属性”对话框
Win键+Ctrl+F 打开“查找：计算机”对话框
Shift+F10或鼠标右击 打开当前活动项目的快捷菜单
Shift 在放入CD的时候按下不放，可以跳过自动播放CD。在打开word的时候按下不放，可以跳过自启动的宏
ALT+F4 关闭当前应用程序
ALT+SPACEBAR 打开程序最左上角的菜单
ALT+TAB 切换当前程序
ALT+ESC 切换当前程序
ALT+ENTER 将windows下运行的MSDOS窗口在窗口和全屏幕状态间切换
PRINT SCREEN 将当前屏幕以图象方式拷贝到剪贴板
ALT+PRINT SCREEN 将当前活动程序窗口以图象方式拷贝到剪贴板
Ctrl+F4 关闭当前应用程序中的当前文本（如word中）
Ctrl+F6 切换到当前应用程序中的下一个文本（加shift 可以跳到前一个窗口）
在IE中：
ALT+RIGHT ARROW 显示前一页（前进键）
ALT+LEFT ARROW 显示后一页（后退键）
Ctrl+TAB 在页面上的各框架中切换（加shift反向）
F5 刷新
Ctrl+F5 强行刷新
目的快捷键
激活程序中的菜单栏 F10
执行菜单上相应的命令 ALT+菜单上带下划线的字母
关闭多文档界面程序中的当
前窗口 Ctrl+ F4
关闭当前窗口或退出程序 ALT+ F4
复制 Ctrl+ C
剪切 Ctrl+ X
删除 DELETE
显示所选对话框项目的帮助 F1
显示当前窗口的系统菜单 ALT+空格键
显示所选项目的快捷菜单 Shift+ F10
显示“开始”菜单 Ctrl+ ESC
显示多文档界面程序的系统
菜单 ALT+连字号(-)
粘贴 CTR L+ V
切换到上次使用的窗口或者
按住 ALT然后重复按TAB，
切换到另一个窗口 ALT+ TAB
撤消 Ctrl+ Z
二、使用“Windows资源管理器”的快捷键
目的快捷键
如果当前选择展开了，要折
叠或者选择父文件夹左箭头
折叠所选的文件夹 NUM LOCK+负号(-)
如果当前选择折叠了，要展开
或者选择第一个子文件夹右箭头
展开当前选择下的所有文件夹 NUM LOCK+*
展开所选的文件夹 NUM LOCK+加号(+)
在左右窗格间切换 F6
三、使用 Win键
可以使用 Microsoft自然键盘或含有 Windows徽标键的其他任何兼容键盘的以下快捷键。
目的快捷键
在任务栏上的按钮间循环 WINDOWS+ TAB
显示“查找：所有文件” WINDOWS+ F
显示“查找：计算机” Ctrl+ WINDOWS+ F
显示“帮助” WINDOWS+ F1
显示“运行”命令 WINDOWS+ R
显示“开始”菜单 WINDOWS
显示“系统属性”对话框 WINDOWS+ BREAK
显示“Windows资源管理器” WINDOWS+ E
最小化或还原所有窗口 WINDOWS+ D
撤消最小化所有窗口 Shift+ WINDOWS+ M
四、使用“我的电脑”和“Windows资源管理器”的快捷键
目的快捷键
关闭所选文件夹及其所有父
文件夹按住 Shift键再单击“关闭按钮（仅适用于“我的电脑”）
向后移动到上一个视图 ALT+左箭头
向前移动到上一个视图 ALT+右箭头
查看上一级文件夹 BACKSPACE
五、使用对话框中的快捷键
目的快捷键
取消当前任务 ESC
如果当前控件是个按钮，要
单击该按钮或者如果当前控
件是个复选框，要选择或清
除该复选框或者如果当前控
件是个选项按钮，要单击该
选项空格键
单击相应的命令 ALT+带下划线的字母
单击所选按钮 ENTER
在选项上向后移动 Ctrl+ TAB
在选项卡上向后移动 Ctrl+ Shift+ TAB
在选项上向前移动 TAB
在选项卡上向前移动 Ctrl+ TAB
如果在“另存为”或“打开”
对话框中选择了某文件夹，
要打开上一级文件夹 BACKSPACE
在“另存为”或“打开”对
话框中打开“保存到”或
“查阅” F4
刷新“另存为”或“打开”
对话框 F5
六、使用“桌面”、“我的电脑”和“Windows资源管理器”快捷键
选择项目时，可以使用以下快捷键。
目的快捷键
插入光盘时不用“自动播放”
功能按住 Shift插入 CD-ROM
复制文件按住 Ctrl拖动文件
创建快捷方式按住 Ctrl+Shift拖动文件
立即删除某项目而不将其放入“回收站” Shift+DELETE
显示“查找：所有文件” F3
显示项目的快捷菜单 APPLICATION键
刷新窗口的内容 F5
重命名项目 F2
选择所有项目 Ctrl+ A
查看项目的属性 ALT+ ENTER或 ALT+双击
可将 APPLICATION键用于 Microsoft自然键盘或含有 APPLICATION键的其他兼容键
七、Microsoft放大程序的快捷键
这里运用Windows徽标键和其他键的组合。
快捷键目的
Windows徽标+PRINT SCREEN将屏幕复制到剪贴板（包括鼠标光标）
Windows徽标+SCROLL LOCK将屏幕复制到剪贴板（不包括鼠标光标）
Windows徽标+ PAGE UP切换反色。
Windows徽标+ PAGE DOWN切换跟随鼠标光标
Windows徽标+向上箭头增加放大率
Windows徽标+向下箭头减小放大率
八、使用辅助选项快捷键
目的快捷键
切换筛选键开关右Shift八秒
切换高对比度开关左ALT+左Shift+PRINT SCREEN
切换鼠标键开关左ALT+左Shift+NUM LOCK
切换粘滞键开关 Shift键五次
切换切换键开关 NUM LOC2000 快捷键
Windows 资源管理器”的快捷键
请按 目的
END 显示当前窗口的底端。
HOME 显示当前窗口的顶端。
NUM LOCK+ 数字键盘的星号 (*) 显示所选文件夹的所有子文件夹。
NUM LOCK+ 数字键盘的加号 (+) 显示所选文件夹的内容。
NUM LOCK+ 数字键盘的减号 (-) 折叠所选的文件夹
向左键 当前所选项处于展开状态时折叠该项，或选定其父文件夹。
向右键 当前所选项处于折叠状态时展开该项，或选定第一个子文件夹。
注意
如果在“辅助功能选项”中打开“粘滞键”，则有些快捷键可能不起作用。
如果您通过“Microsoft 终端服务客户”连接到 Windows 2000，则某些快捷键将会更改。详细信息，请参阅“Microsoft 终端服务客户”的联机文档。
f1－帮助
f2－重命名
f5－刷新
alt+f4－关闭窗口
ctrl+a=全部选中
ctrl+c=拷贝
ctrl+v=粘贴
ctrl+x=剪切
alt+enter(或ALT+双击鼠标左键)=属性





## 文件/文件夹批量重命名

### 重命名文件

获取需要修改的全部文件名，并写入rename.bat中(就是把当前目录的所有文件名称写入到一个文件中)

```bash
dir /b> rename.bat
```

rename.bat

```bash
rename.bat
文件
ren "旧文件名.jpg" “新文件名.jpg”
目录
ren "旧目录" “新目录”
```

通过excel 批量修改文件名称的号码

| 旧文件名 | 新文件名 | 新旧文件格式是否相同？                                | 重命名 | 旧文件名+引号    | 新文件名+引号    |
| -------- | -------- | ----------------------------------------------------- | ------ | ---------------- | ---------------- |
| 单元格A2 | 单元格B2 | =IF(RIGHT(A3,4)=RIGHT(B3,4),RIGHT(A3,4),"格式不一致") | ren    | ``=$G$1&A2&$G$1` | ``=$G$1&B2&$G$1` |



1. `win + r : shell:startup` 开机启动 



### cmd命令

- 新建一个指定的文件 名称

```cmd
echo on  >a.txt
echo 123 >a.txt
touch 124.qdfs
```

- 删除文件 del 文件名
- 查看文件 cat  文件名
- 写入文件

```cmd
echo 123asdfsadfdsf >> a.txt
cat >> a.txt
输入内容
```

- notepad 打开记事本
- mspaint 打开画图
- calc 打开计算机
- write 写字板
- sysdm.cpl 打开环境变量设置窗口
- md 创建目录
- rmdir(rd) 删除目录，目录内没有文档。
- rd /s/q 目录名 包含文件夹下的子目录
- echo on a.txt 创建空文件
- del 删除文件
- rm 文件名 删除文件
- cat 文件名 查看文件内容
- cat > 文件名 向文件中写上内容。

## DOS 内部命令

| 命令      | 作用                                                         |
| --------- | ------------------------------------------------------------ |
| `md`      | 建立子目录                                                   |
| `cd`      | 改变当前目录(CD命令不能改变当前所在的盘，CD..退回到上一级目录，CD\表示返回到当前盘的目录下，CD无参数时显示当前目录名) |
| `rd`      | 删除子目录命令                                               |
| `dir`     | 显示磁盘目录命令                                             |
| `path`    | 路径设置命令`path=路径`                                      |
| `copy` cp | 文件复制命令                                                 |
| `type`    | 显示文件内容命令                                             |
| `edit`    | 编辑文件内容命令                                             |
| `ren`     | 文件改名命令                                                 |
| `del`     | 删除文件命令                                                 |
| `cls`     | 清屏幕命令                                                   |
| `ver`     | 查看系统版本号命令                                           |
| `date`    | 设置日期                                                     |
| `time`    | 系统时钟设置命令                                             |
| `prompt`  | 更改命令提示符                                               |
| `pwd`     | 查询当前所在的目录位置                                       |
| mv        | 移动文件                                                     |

## DOS 外部命令

|            |                                                     |
| ---------- | --------------------------------------------------- |
| `deletree` |                                                     |
| `format`   | 格式化命令                                          |
| `diskcopy` | 磁盘复制                                            |
| `label`    |                                                     |
| `vol`      |                                                     |
| `sys`      |                                                     |
| `xcopy`    |                                                     |
| `fc`       |                                                     |
| `attrib`   |                                                     |
| `mem`      | 查看你的计算机内存有多少，以及内存的使用情况。      |
| `tree`     |                                                     |
| `color`    |                                                     |
| `fdisk`    | 分区命令                                            |
| `cat`      | 查看文件内容 cat >abc.txt 往abc.txt文件中写上内容。 |

## CMD命令

|                        |                  |
| ---------------------- | ---------------- |
| cmd                    | CMD命令提示符    |
| calc                   | 计算器           |
| notepad                | 打开记事本       |
| mspaint                | 画图             |
| regedit                | 注册表           |
| diskmgmt.msc           | 磁盘管理         |
| control                | 控制面板         |
| dxdiag                 | 检查DirectX信息  |
| mstsc                  | 远程桌面连接     |
| gpedit.msc             | 组策略           |
| devmgmt.msc\hdwwiz.cpl | 设备管理器       |
| services.msc           | 本地服务设置     |
| Firewall.cpl           | Windows防火墙    |
| Resmon                 | 资源监视器       |
| certmgr.msc            | 证书管理实用程序 |
| compmgmt.msc           | 计算机管理       |
| eventvwr               | 事件查看器       |
| secpol.msc             | 本地安全策略     |

2.：程序和功能
3.：
4.charmap：启动字符映射表
5.chkdsk.exe：Chkdsk磁盘检查(管理员身份运行命令提示符)
6.cleanmgr: 打开磁盘清理工具
7.cliconfg：SQL SERVER 客户端网络实用工具
8.cmstp：连接管理器配置文件安装程序
10.自动关机命令
　　Shutdown -s -t 600：表示600秒后自动关机
　　shutdown -a ：可取消定时关机
　　Shutdown -r -t 600：表示600秒后自动重启
　　rundll32 user32.dll,LockWorkStation：表示锁定计算机
11.colorcpl：颜色管理，配置显示器和打印机等中的色彩
12.CompMgmtLauncher：计算机管理
13.
14.credwiz：备份或还原储存的用户名和密码
15.comexp.msc：打开系统组件服务

17.dcomcnfg：打开系统组件服务
18.Dccw：显示颜色校准
19.20.desk.cpl：屏幕分辨率
21.dfrgui：优化驱动器 Windows 7→dfrg.msc：磁盘碎片整理程序
22.dialer：电话拨号程序
24.dvdplay：DVD播放器
25
26.eudcedit：造字程序
27.
28.explorer：打开资源管理器
29.
30.FXSCOVER：传真封面编辑器
31.fsmgmt.msc：共享文件夹管理器
32.
33.
34.inetcpl.cpl：Internet属性
35.intl.cpl：区域
36.iexpress：木马捆绑工具，系统自带
37.joy.cpl：游戏控制器
38.logoff：注销命令
39.lusrmgr.msc：本地用户和组
40.lpksetup：语言包安装/删除向导，安装向导会提示下载语言包
41.lusrmgr.msc：本机用户和组
42.main.cpl：鼠标属性
43.mmsys.cpl：声音
44.magnify：放大镜实用程序
45.mem.exe：显示内存使用情况(如果直接运行无效，可以先管理员身份运行命令提示符，在命令提示符里输入mem.exe>d:a.txt 即可打开d盘查看a.txt，里面的就是内存使用情况了。当然什么盘什么文件名可自己决定。)
46.MdSched:Windows内存诊断程序
47.mmc：打开控制台
48.mobsync：同步命令
49.mplayer2：简易widnows media player
50.Msconfig.exe：系统配置实用程序
51.msdt：微软支持诊断工具
52.msinfo32：系统信息
54.Msra：Windows远程协助
56.NAPCLCFG.MSC：客户端配置
57.ncpa.cpl：网络连接
58.narrator：屏幕“讲述人”
59.Netplwiz：高级用户帐户控制面板，设置登陆安全相关的选项
60.netstat : an(TC)命令检查接口
61.
62.Nslookup：IP地址侦测器
63.odbcad32：ODBC数据源管理器
64.OptionalFeatures：打开“打开或关闭Windows功能”对话框
65.osk：打开屏幕键盘
66.perfmon.msc：计算机性能监测器
67.perfmon：计算机性能监测器
68.PowerShell：提供强大远程处理能力
69.printmanagement.msc：打印管理
70.powercfg.cpl：电源选项
71.psr：问题步骤记录器
72.Rasphone：网络连接
73.Recdisc：创建系统修复光盘
74
75.Rstrui：系统还原
76.
77.regedt32：注册表编辑器
78.rsop.msc：组策略结果集
79.sdclt：备份状态与配置，就是查看系统是否已备份
80.
82.sfc /scannow：扫描错误并复原/windows文件保护
83.sfc.exe：系统文件检查器
84.shrpubw：创建共享文件夹
85.sigverif：文件签名验证程序
86.slui：Windows激活，查看系统激活信息
87.slmgr.vbs -dlv ：显示详细的许可证信息
　　slmgr.vbs -dli ：显示许可证信息
　　slmgr.vbs -xpr ：当前许可证截止日期
　　slmgr.vbs -dti ：显示安装ID 以进行脱机激活
　　slmgr.vbs -ipk ：(Product Key)安装产品密钥
　　slmgr.vbs -ato ：激活Windows

