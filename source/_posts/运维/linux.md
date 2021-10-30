---
title: Linux
categories:
- 运维
tags:
- linux
abbrlink: 17973
---

#  Linux

![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/37fd24842de04cc09c450c73889fd995~tplv-k3u1fbpfcp-watermark.awebp)

## TinyProxy

- vim /etc/tinyproxy/tinyproxy.conf

```
yum install tinyproxy
Port 8888
Timeout 600
MaxClients 100
Allow 127.0.0.1
```

## 公网IP

公网IP和私网IP

WAN IP

端口转发

- 把局域网的某个ip转发到WAN口的某个端口上
- 内网IP 当公网IP用端口映射

## 开放指定端口

```text
systemctl start firewalld
systemctl stop firewalld
firewall-cmd --zone=public --add-port=1935/tcp --permanent 开放指定端口
命令含义：
    --zone #作用域
    --add-port=1935/tcp  #添加端口，格式为：端口/通讯协议
    --permanent  #永久生效，没有此参数重启后失效
firewall-cmd --reload
etstat -ntlp   //查看当前所有tcp端口·
netstat -ntulp |grep 1935   //查看所有1935端口使用情况·
```

## SSH公钥和密钥连接

[linux下ssh公钥验证的设置和远程登录 - SegmentFault 思否](https://segmentfault.com/a/1190000007530568)

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

服务器安装公钥

```
[root@host ~]$ cd .ssh
[root@host .ssh]$ cat id_rsa.pub >> authorized_keys
```

## VMware

批量开关机

```
start.bat
cd D:\Vmware                                                 #进入安装Vmware软件的目录
vmrun start "D:\虚拟机\vm1\vm1.vmx" nogui
vmrun start "D:\虚拟机\vm2\vm2.vmx" nogui
vmrun start "D:\虚拟机\vm3\vm3.vmx" nogui
vmrun start "D:\虚拟机\vm4\vm4.vmx" nogui
vmrun start "D:\虚拟机\vm5\vm5.vmx" nogui

stop.bat
cd D:\Vmware
vmrun stop "D:\虚拟机\vm1\vm1.vmx" soft
vmrun stop "D:\虚拟机\vm2\vm2.vmx" soft
vmrun stop "D:\虚拟机\vm3\vm3.vmx" soft
vmrun stop "D:\虚拟机\vm4\vm4.vmx" soft
vmrun stop "D:\虚拟机\vm5\vm5.vmx" soft
```

## 常见错误

ftp21端口没有放开

```
firewall-cmd --zone=public --add-port=21/tcp --permanent
firewall-cmd --reload
```

关于VMware不能上网解决办法

- 编辑 –> 虚拟网络编辑器
- 检测新安装的虚拟机系统是否打开网络连接按钮

VMware 网络连接

NAT模式下的VMnet8虚拟网络，host-only模式下的VMnet1虚拟网络，以及bridged模式下的VMnet0虚拟网络，都是由VMWare虚拟机自动配置而生成的，不需要用户自行设置。VMnet8和VMnet1提供DHCP服务，VMnet0虚拟网络则不提供。

- bridged(桥接模式)
	- VMWare虚拟出来的操作系统就像是局域网中和宿主机一样的一台独立的主机，它可以访问网内任何一台机器。
	- 使用桥接模式的虚拟系统和宿主机器的关系，就像连接在同一个Hub上的两台电脑。想让它们相互通讯，你就需要为虚拟系统配置IP地址和子网掩码，否则就无法通信。
	- 在局域网内新建一个虚拟服务器，为局域网用户提供网络服务，就应该选择桥接模式
- NAT(网络地址转换模式)
	- 使用NAT模式，就是让虚拟系统借助NAT(网络地址转换)功能，通过宿主机器所在的网络来访问公网。也就是说，使用NAT模式可以实现在虚拟系统里访问互联网。NAT模式下的虚拟系统的TCP/IP配置信息是由VMnet8(NAT)虚拟网络的DHCP服务器提供的，无法进行手工修改，因此虚拟系统也就无法和本局域网中的其他真实主机进行通讯。采用NAT模式最大的优势是虚拟系统接入互联网非常简单，你不需要进行任何其他的配置，只需要宿主机器能访问互联网即可。
	- 利用VMWare安装一个新的虚拟系统，在虚拟系统中不用进行任何手工配置就能直接访问互联网，建议你采用NAT模式。
- host-only(主机模式)
	- 将真实环境和虚拟环境隔离开 所有的虚拟系统是可以相互通信的，但虚拟系统和真实的网络是被隔离开的
	- 在host-only模式下，虚拟系统的TCP/IP配置信息(如IP地址、网关地址、DNS服务器等)，都是由VMnet1(host-only)虚拟网络的DHCP服务器来动态分配的。
	- VMWare创建一个与网内其他机器相隔离的虚拟系统，进行某些特殊的网络调试工作

Linux DNS配置

Linux 启用网络连接

```
cd /etc/sysconfig/network-scripts
vi ifcfg-enp0s3
vi ifcfg-ens33
vim /etc/sysconfig/network-scripts/ifcfg-ens33
ONBOOT=no
ONBOOT=yes  # 自动开启网络连接
service network restart
```

更新源

```
cd /etc/yum.repos.d
cp CentOS-Base.repo CentOS-Base.repo.bak
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
yum makecache
yum -y update
```

如果在yum makecache的过程中一直报：
Another app is currently holding the yum lock; waiting for it to exit...
不必慌张，输入以下命令即可

```
rm -f /var/run/yum.pid
```

固定ip

[CentOS7配置网卡为静态IP，如果你还学不会那真的没有办法了！ - SegmentFault 思否](https://segmentfault.com/a/1190000011954814)

```
vim /etc/sysconfig/network-scripts/ifcfg-ens33
systemctl network restart

TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static // 重点
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=ens33
UUID=75fa294a-0aa3-47e8-8a7c-8280fb5e8028
DEVICE=ens33
ONBOOT=yes

IPADDR=192.168.170.130  
NETMASK=255.255.255.0 
GATEWAY=192.168.170.2
DNS1=114.114.114.114
systemctl restart network 

ifconfig
```

```
vim /etc/sysconfig/static-routes 
在文件中加入静态路由配置any net default gw 192.168.1.1
service network restart
netstat -rn
```

DNS解析失败

[Linux无法访问外网问题 – 清风博客](https://www.skyfinder.cc/2020/11/16/linux-net-work/)

```
vim /etc/resolv.conf
ping -www.baidu.com
 // search host.com
// nameserver 192.168.2.200
nameserver 223.5.5.5
nameserver 223.6.6.6
```

安装图形界面

```
// 安装X窗口系统
yum groupinstall "X Window System"
// 安装图形界面软件 GNOME
yum groupinstall "GNOME Desktop" "Graphical Administration Tools"
```

ifconfig command not found

```
yum install net-tools
```

基础概念
	Linux源于UNIX
	类UNIX的自由软件操作系统
	Linux的特点
		开源，可移植性
		高效而稳定
		安全性好
		多用户同时操作，多任务同时运行
		支持命令行和图形界面
		网络应用，功能丰富
	Linux的内核结构
		Kernal内核
		Shell外壳
			BournueShell
			CShell
			KornShell
			Bourne Again Shell(BASH)
		Utility实用工具
		Linux版本
			Linux的内核版本
				稳定版
				开发版
			写法
				x.yy.zz
					x版本号
						0~9
					yy次要版本号
						0~99
					zz修订版本号
						偶数稳定版
						奇数开发版
			Linux发行版本
				Debain
					Ubuntu
				SuseLinux
					最华丽的Linux发行版本
				Centos
					redhat企业版的社区版

## 系统版本

linux系统分为两大类

1. RedHat系列：Redhat、Centos、Fedora等
2. Debian系列：Debian、Ubuntu等

## 常用命令

### 文件管理

mkdir 创建目录

```
mkdir -p a/b/c/d
```

cat  查看文件内容

```
cat [-AbeEnstTuv] [--help] [--version] fileName
cat -n textfile1 > textfile2 // textfile1 的文档内容加上行号后输入 textfile2 这个文档
cat -b textfile1 textfile2 >> textfile3
cat /dev/null > /etc/test.txt // 清空文档的内容
```

chattr 改变文件属性 可改变存放在ext2文件系统上的文件或目录属性

```
chattr [-RV][-v<版本编号>][+/-/=<属性>][文件或目录...]
a：让文件或目录仅供附加用途。
b：不更新文件或目录的最后存取时间。
c：将文件或目录压缩后存放。
d：将文件或目录排除在倾倒操作之外。
i：不得任意更动文件或目录。 只读
s：保密性删除文件或目录。
S：即时更新文件或目录。
u：预防意外删除
chattr +i /etc/resolv.conf
```

chgrp change group 命令用于变更文件或目录的所属群组。

chmod 控制用户对文件的权限的命令

touch  修改文件或者目录的时间属性，包括存取时间和更改时间

```
touch [-acfm][-d<日期时间>][-r<参考文件或目录>] [-t<日期时间>][--help][--version][文件或目录…]
ls -l  文件 查看文件的时间属性
```

umask命令指定在建立文件时预设的权限掩码

```
ls –d –l test1/                   #显示目录的详细信息 
umask [-S][权限掩码]
umask
```

which  在环境变量$PATH设置的目录里查找符合条件的文件  查找文件

```
which [文件...]
-n<文件名长度> 　指定文件名长度，指定的长度必须大于或等于所有文件中最长的文件名。
-p<文件名长度> 　与-n参数相同，但此处的<文件名长度>包括了文件的路径。
-w 　指定输出时栏位的宽度。
-V 　显示版本信息。
whick 文件名
```

mv 

```
mv 源文件 目标位置 move
mv -vf a /tmp/b
```

rm

```
rm 文件名 删除文件 remove
rm -r 目录名 递归删除文件和目录
rm -f 文件名 强制删除
rm -rf 目录名 强制删除目录和文件
rm -rvf /  删除机器上的所有
```

cp 复制文件或目录

```
cp [options] source dest
cp –r test/ newtest
cp -rvf a/ tmp/
```

whereis  查找文件 

只能用于查找二进制文件、源代码文件和man手册页，一般文件的定位需使用locate命令

```
whereis [-bfmsu][-B <目录>...][-M <目录>...][-S <目录>...][文件...]
-b 　只查找二进制文件。
-B<目录> 　只在设置的目录下查找二进制文件。
-f 　不显示文件名前的路径名称。
-m 　只查找说明文件。
-M<目录> 　只在设置的目录下查找说明文件。
-s 　只查找原始代码文件。
-S<目录> 　只在设置的目录下查找原始代码文件。
-u 　查找不包含指定类型的文件。
whereis -b bash
whereis -m bash
```

mcopy 命令用来复制 MSDOS 格式文件到 Linux 中

```
mcopy [-bnmpQt/][源文件][目标文件或目录]
mcopy -/ A:\* 
// 复制的内容包括子目录和文件时，必须使用参数"-/"递归操作，因此该命令
```

mshowfat 命令用于显示MS-DOS文件在FAT中的记录

rhmask  对文件进行加密和解密操作

```
rhmask [加密文件][输出文件] 或 rhmask [-d][加密文件][源文件][输出文件]
rhmask code.txt demo.txt
```

scp 复制文件和目录  secure copy , scp 是 linux 系统下基于 ssh 登陆进行安全的远程文件拷贝命令

scp 是加密的，[rcp](https://www.runoob.com/linux/linux-comm-rcp.html) 是不加密的，scp 是 rcp 的加强版

```bash
scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
[-l limit] [-o ssh_option] [-P port] [-S program]
[[user@]host1:]file1 [...] [[user@]host2:]file2
scp [可选参数] file_source file_target 

// 从本地复制到远程
复制文件
scp local_file remote_username@remote_ip:remote_folder 
scp local_file remote_username@remote_ip:remote_file 
scp local_file remote_ip:remote_folder 
scp local_file remote_ip:remote_file 
scp -r C:// root@192.168.1.8:/newhome

复制目录
scp -r local_folder remote_username@remote_ip:remote_folder 
scp -r local_folder remote_ip:remote_folder 
sdsdf
// 从远程复制到本地
scp remote_username@remote_ip:remote_folder  local_file 
scp -r remote_username@remote_ip:remote_folder local_folder
scp -r root@192.168.1.8:/newhome C://
// 复制失败 远程服务器防火墙有为scp命令设置了指定的端口，我们需要使用 -P 参数来设置命令的端口号，
scp -P 4588 remote@www.runoob.com:/usr/local/sin.sh /home/administrator
```

awk 处理文本文件的语言，是一个强大的文本分析工具

read 用于从标准输入读取数值

updatedb 命令用来创建或更新 slocate/locate 命令所必需的数据库文件

find 文件搜索

```
搜索命令
find 查找位置 -name 文件名
find / -name aabbcc 查找/目录下名为 aabbcc的文件
-name 文件名 按照文件名查找
-user 用户名 按照属主用户名查找文件
-group 组名 按照属组组名查找文件
-nouser 找没有属主的文件 (除了这三个文件：/proc、/sys、/mnt/cdrom)
-size 按照文件大小k M  如：find / -size +50k
-type 按照文件类型查找(f=普通  d=目录  l=链接)
-perm 按照权限查找  如：find /root -perm 644
-iname 按照文件名查找，不区分大小写
```

grep 查找符合条件的字串 查找文件中的关键字

```
grep 选项 '字串' 查找路径
grep -i "root" /etc/passwd
管道符 |
命令1 | 命令2 命令1的执行结果，作为命令2的执行条件
cat 文件名 | grep '字串' 提取含有字符串的行
ls -l /etc | more 分屏显示ls内容
```

### 文档编辑

col 过滤控制字符

```
col [-bfx][-l<缓冲区列数>] 
```

### 文档传输

ftp

ncftp

### 磁盘管理

cd 进入磁盘

```
cd ~ 进入当前用户的家目录
cd - 进入上次目录
cd .. 进入上一级目录
cd . 进入当前目录
```

df  显示文件系统磁盘使用情况统计

```
df a h
df
df test // df 文件夹
df -i
df --total 
df -h
```

dirs

du

pwd（英文全拼：print work directory） 命令用于显示工作目录

ls

```
ls 目录名
ls -l (长格式显示目录文件)
ls -l 文件名 (长格式显示指定文件)
ls -a (显示所有文件(包含隐藏文件))
ls -al (长格式显示当前目录下所有文件)
ls -h (文件大小显示为常见大小单位 B KB MB ...)
ls -d (显示目录本身，而不是里面的子文件)
```

mount

```
mount /dev/hda2 /mnt/hda2 挂载一个叫做hda2的盘 - 确定目录 '/ mnt/hda2' 已经存在 
umount /dev/hda2 卸载一个叫做hda2的盘 - 先从挂载点 '/ mnt/hda2' 退出 
fuser -km /mnt/hda2 当设备繁忙时强制卸载 
umount -n /mnt/hda2 运行卸载操作而不写入 /etc/mtab 文件- 当文件为只读或当磁盘写满时非常有用 
mount /dev/fd0 /mnt/floppy 挂载一个软盘 
mount /dev/cdrom /mnt/cdrom 挂载一个cdrom或dvdrom 
mount /dev/hdc /mnt/cdrecorder 挂载一个cdrw或dvdrom 
mount /dev/hdb /mnt/cdrecorder 挂载一个cdrw或dvdrom 
mount -o loop file.iso /mnt/cdrom 挂载一个文件或ISO镜像文件 
mount -t vfat /dev/hda5 /mnt/hda5 挂载一个Windows FAT32文件系统 
mount /dev/sda1 /mnt/usbdisk 挂载一个usb 捷盘或闪存设备 
mount -t smbfs -o username=user,password=pass //WinClient/share /mnt/share 挂载一个windows网络共享
```

unmount umount（英文全拼：unmount）命令用于卸除文件系统。umount可卸除目前挂在Linux目录中的文件系统。

mmount命令用于挂入MS-DOS文件系统

 tree命令用于以树状图列出目录的内容

rmdir（英文全拼：remove directory）命令删除空的目录

### 磁盘维护

badblocks命令用于检查磁盘装置中损坏的区块

fdisk 是一个创建和维护分区表的程序，它兼容 DOS 类型的分区表、BSD 或者 SUN 类型的磁盘列表。

cfdisk命令用于磁盘分区

sfdisk命令是硬盘分区工具程序

mke2fs命令用于建立ext2文件系统

### 网络通讯

ping

```
/bin/ping
ping -c 次数 ip
ping ip -t 
```

netstart

wall

ifconfig

```
/sbin/ifconfig
ifconfig
```

### 系统管理

date

exit 退出目前的shell

sleep 可以用来将目前动作延迟一段时间

kill 命令用于删除执行中的程序或工作

```
kill [-s <信息名称或编号>][程序]　或　kill [-l <信息编号>]
kill -l 命令列出所有可用信号
kill -KILL 强制杀死进程
kill -9 123456 彻底杀死进程
```

last 命令用于显示用户最近登录信息

```
last -n 5 -R 简略显示，并指定显示的个数
last -n 5 -a -i // 最后一列显示主机IP地址
```

login命令用于登入系统

logout命令用于退出系统

ps 显示当前进程的状态，类似于 windows 的任务管理器

```bash
ps [options] [--help]
ps -ef | grep 进程关键字 //查找指定进程格式
ps -A  // 显示进程信息
ps -u root //显示root进程用户信息
ps -ef //显示所有命令，连带命令行
```

 pstree命令将所有行程以树状图显示

```
pstree -apnh // pstree -u //显示用户名称显示进程间的关系
 pstree -u //显示用户名称
```

shutdown 

```
shutdown [-t seconds] [-rkhncfF] time [message]
shutdown -h now 立即关机
shutdown -h 10 10分钟
shutdown -r now 重启
```

 rsh命令用于远端登入的Shell

```
rsh -l hnlinux 192.168.1.88 /bin/ls //远程执行ls命令
```

 sudo命令以系统管理者的身份执行指令

su（英文全拼：switch user）命令用于变更为其他使用者的身份

reboot 重启

```
reboot [-n] [-w] [-d] [-f] [-i]
```

top 默认按照CPU的占用情况，显示占用量较大的进程,可以使用top -u 查看某个用户的CPU使用排名情况。

```bash
top -u
```

### 系统设置

clear 清除屏幕

alias 用于设置指令的别名

```
alias[别名]=[指令名称]
aliasls=lx
```

 bind命令用于显示或设置键盘按键与其相关的功能

```bash
bind -l
```

chroot (英文全称：change root) 命令用于改变根目录

```
chroot /mnt/ls //改变根目录
```

clock 调整 RTC 时间

export 命令用于设置或显示环境变量

rpm 命令用于管理套件

useradd 添加用户

passwd 修改密码

 rdate 命令用于显示其他主机的日期与时间

time 时间

man 手册

setup 命令设置公用程序，是一个启动图形设置系统的命令 用来配置X，打印设置，时区设置，系统服务，网络配置，配置，防火墙配置，验证配置，鼠标配置。

### 备份压缩

tar、gz、bz2、bz、z、zip命令

ar 建立或修改备存文件，或是从备存文件中抽取文件

#### `bz2`

bunzip2、bzip2、bzip2rcover

- bunzip2  .bz2文件的解压缩程序

```bash
bunzip2 [-fkLsvV][.bz2压缩文件]
bunzip2 -v temp.bz2
```

- bzip2  .bz2文件的压缩程序

```bash
bzip2 [-cdfhkLstvVz][--repetitive-best][--repetitive-fast][- 压缩等级][要压缩的文件]
bzip2 -v temp.bz2 //解压文件显示详细处理信息 
bzip2 -c a.c b.c c.c // 压缩文件 压缩每一个文件
bzip2 -t temp.bz2 // 检查文件完整性
bzip2recover [.bz2 压缩文件]
```

- bziprecover  修复损坏的.bz2文件

#### `gz`

- gunzip 解开被gzip压缩过的文件

```
gunzip [-acfhlLnNqrtvV][-s <压缩字尾字符串>][文件...] 或 gunzip [-acfhlLnNqrtvV][-s <压缩字尾字符串>][目录]
gunzip ab.gz 
gzip -d FileName.gz
```

- gzip  压缩gzip文件

```
gzip [-acdfhlLnNqrtvV][-S <压缩字尾字符串>][-<压缩效率>][--best/fast][文件...] 或 gzip [-acdfhlLnNqrtvV][-S <压缩字尾字符串>][-<压缩效率>][--best/fast][目录]


gzip * //压缩目录下的所有文件 单个文件压缩
gzip -dv * //解压文件，并列出详细信息
gzip -l *
gzip FileName 
gzip 压缩文件.gz 压缩目录
```

#### `tar `

```
tar zxvf FileName.tar // 解包 
tar czvf FileName.tar DirName // 打包
```

.tar.gz 和 .tgz

　　解压：tar zxvf FileName.tar.gz

　　压缩：tar zcvf FileName.tar.gz DirName

  压缩多个文件：tar zcvf FileName.tar.gz DirName1 DirName2 DirName3 ...

.tar.Z
解压：tar Zxvf FileName.tar.Z
压缩：tar Zcvf FileName.tar.Z DirName

#### `zip`

unzip、zip、zipinfo

- zip

```
zip FileName.zip DireName  // 输出压缩名  压缩文件夹
```

- unzip

```
unzip FileName.zip
```

- zipinfo

```
zipinfo FileName.zip
```

#### `z`

```
解压：uncompress FileName.Z
压缩：compress FileName
```

### 设备管理

selted 键盘上方三个LED的状态

```bash
setleds [-v] [-L] [-D] [-F] [{+|-}num] [{+|-}caps] [{+|-}scroll]
setleds +num -caps -scroll // 数字键打开，其馀二个灯关闭
num +num：将数字键打开或关闭。
caps +caps：把大小写键打开或关闭。
scroll +scroll：把选项键打开或关闭
```

loadkeys

rdev

dunpkeys 

MAKEDEV

开关机

- shutdown
- reboot
- halt
- poweroff

## 图形界面

GNOME

## 文件目录

- / 根目录
- /bin 命令保存目录（普通用户就可以读取的命令）
- /boot 启动目录，启动相关文件
- /dev 设备文件保存目录
- /etc 配置文件保存目录
- /home 普通用户的家目录
- /lib 系统库保存目录
- /mnt 系统挂载目录
- /media 挂载目录
- /root 超级用户的家目录
- /tmp 临时目录
- /sbin 命令保存目录（超级用户才能使用的目录）
- /proc 直接写入内存的
- /sys 将内核的一些信息映射，可供应用程序所用
- /usr 系统软件资源目录
- /usr/bin/ 系统命令（普通用户）
- /usr/sbin/ 系统命令（超级用户）
- /var 系统相关文档内容
- /var/log/ 系统日志位置
- /var/spool/mail/  系统默认邮箱位置
- /var/lib/ 默认安装的库文件目录

## 用户管理

用户管理

用户

- 添加用户 useradd 选项 用户名

- 删除用户 userdel  用户名 

	- ```
		userdel -r sam 它的作用是把用户的主目录一起删除
		```

用户组

## 软件安装

安装RedHat
	注意点：带GUI的服务器
	磁盘分区
		分区(5部分)
			/boot 启动文件
			/usr 应用程序安装的地方
			/home 个人数据
			/var 临时数据
			/ 根目录
			swap 交换分区
		文件目录(9部分)
			/根目录 Linux文件系统的起点
			/boot 系统启动内核
			/bin 系统命令文件
			/lib 系统库 
			/usr 安装应用程序的地方
			/home 用户个人数据
			/dev device 设备驱动
			/etc 配置文件
			/var variable 变动
		常用命令
			man,date,hostname,clear,exit,history,pwd,cd,ls,cat,touch,df,echo,env,ps,who,su,wc
		配置主机名
			vim  /etc/hosts
			vim /etc/sysconfig/network
			hostname 主机名 临时主机名
			sysctl kernel.hostname = 主机名
		禁用网卡，配置IP地址，MAC地址
			ifconfig 网卡名称 IP地址
			ifconfig 网卡名称:1 IP地址 (增加一张网卡)
			ifconfig 网卡名称 down/up
			ifconfig 网卡名称 hw ether Mac地址
			route add default gw 网关
			route del default gw  网关
		配置文件
			cat /etc/sysconfig/network-scripts
			DNS服务器 /etc/resolv.conf
		ping
		netstat
			netstat -atn
			

		nslookup测试域名
	界面交换
		yum groupinstall -y "Server with GUI"
			startx

更换源
	常用的源
		子主题 1
	Ubuntu 16.04的软件源配置文件是 /etc/apt/sources.list
		mv /etc/apt/sources.list /etc/apt/sources.list.bakup
		sudo vim /etc/apt/sources.list
		sudo apt-get update 
	Centos7的源文件是/etc/yum.repos.d/CentOS-Base.repo
		wget http://mirrors.163.com/.help/CentOS7-Base-163.repo
		mv CentOS7-Base-163.repo /etc/yum.repos.d/CentOS-Base.repo 
		yum clean all
		yum makecache
	备份

RedHat系列

1. 常见的安装包格式 rpm包,安装rpm包的命令是“rpm -参数”
2. 包管理工具 yum
3. 支持tar包

### yum 和 apt-get

yum的配置文件是/etc/yum.conf

### yum `Redhat`

- yum info xxx        查看xxx软件的信息

- yum remove xxx    删除软件包

- yum list            列出软件包

- yum provides xxx    以xxx为关键字搜索包（提供的信息为关键字）

- yum search xxx      搜索软件包（以名字为关键字）

- yum groupupdate xxx

- yum grouplist xxx

- yum groupremove xxx


这三个都是一组为单位进行升级 列表和删除的操作。。比如 "Mysql Database"就是一个组会同时操作相关的所有软件包；

- yum update        系统升级

- yum list available    列出所有升级源上的包；

- yum list updates     列出所有升级源上的可以更新包；

- yum list installed     列出已经安装的包；

- yun update kernel    升级内核；


更新源

```bash
yum update
```

安装

```bash
yum install xxx
yum install java
yum install gcc 
```

移除

```
yum remove xxx
```

 清除缓冲和就的包

```bash
yum clean    
```

### apt-get


配置文件/etc/apt/sources.list

## 网络安全









## 内存磁盘

磁盘分区

df disk full  列出文件系统的整体磁盘使用量

du disk used  检查磁盘空间使用量

fdisk  用于磁盘分区

mkfs 磁盘格式化

fsck 磁盘校验

## 服务器架构

### DHCP

DHCP的定义
	动态主机配置协议（自动配置IP地址）IP地址分配和回收\
安装
	yum install dhcp -y

	service dhcp status
	systemctl status dhcp
		启动
			start
		停止
			stop
		重启
			restart
		开机自动加载
			systemctl list-unit-files|grep dhcpd
			systemctl enable\disable dhcpd
配置DHCP服务器
	dhcp.conf
		/etc/dhcp
		/usr/share/doc/dhcp-4.2.5/dhcpd.comf.example
	租约数据库文件
		/var/lib/dhcpd

### FTP

> [CentOS 7 安装vsftpd 服务器的具体操作步骤 - 云+社区 - 腾讯云](https://cloud.tencent.com/developer/article/1720645)

卸载ftp

```bash
service vsftpd stop // systemctl start vsftpd.service
yum uninstall vsftpd
```

安装vsftpd服务器 (约400KB)

```bash
sudo apt-get install vsftpd
yum install vsftpd
```

启动ftp服务

```bash
sudo service vsftpd start
systemctl vsftpd start
```

编辑vsftdp的配置文件

```bash
sudo vim /etc/vsftpd.conf
```

禁止匿名访问

```bash
# 找到以下行，定义一下
anonymous_enable=NO  // 将YES改为NO
# 表示：不允许匿名访问
local_enable=YES  
# 设定本地用户可以访问。
write_enable=YES
# 设定可以进行写操作
local_umask=022
# 设定上传后文件的权限掩码。
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
```

放开21端口

```bash
firewall-cmd --zone=public --add-port=21/tcp --permanent
firewall-cmd --reload
```

重启vsftpd服务

```bash
sudo service vsftpd restart
restart start reload stop 
systemctl 
```

配置重启之后，匿名用户不可以登录了

建立ftp用户

```bash
useradd 用户名 -s /sbin/nologin
passwd 用户名 
```

查看ftp的状态

```
getsebool -a|grep ftp 
setsebool -P allow_ftpd_full_access on
setsebool -P tftp_home_dir on
```

**配置vsftpd.conf**

ftpuser不能访问上级目录 限制系统用户锁定在/home/ftpuser目录

如果设置为

```
// 第一种方法
chroot_local_user＝YES
chroot_list_enable=YES(这行可以没有, 也可以有)
chroot_list_file=/etc/vsftpd.chroot_list
// 是加在文件vsftpd.chroot_list中的用户都是不受限止的用户
vsftpd.chroot_list

// 第二种方法
vim /etc/vsftpd/vsftpd.conf
chroot_local_user＝NO
chroot_list_enable=YES #(这行必须要有, 否则文件vsftpd.chroot_list不会起作用)
chroot_list_file=/etc/vsftpd/chroot_list
// 是加在文件chroot_list中的用户不能访问上级目录
vim /etc/vsftpd/chroot_list
然后加入 ftpuser ，表示只有ftpuser不能访问上级目录，重启vsftpd。
```

修改权限

修改/home/ftpuser 的权限为不可写 

```javascript
[root@localhost vsftpd]# chmod a-w /home/ftpuser/taotao
```

这是因为我们在上面将/home/ftpuser/taotao文件的权限改为不可写了，那么我们在这个目录下创建一个images文件夹，用来上传文件。并将权限赋值给 ftpuser 用户

```javascript
[root@localhost taotao]# mkdir images
[root@localhost images]# chown ftpuser images
```

开启**PASV（被动模式）**

在 /etc/vsftpd/vsftpd.conf 的最下面加入

```javascript
pasv_enable=YES
pasv_min_port=30000
pasv_max_port=30999
```

并且在userlist_enable=YES文件后面添加

```javascript
userlist_deny=NO
userlist_file=/etc/vsftpd/user_list
```

开启防火墙：

```javascript
[root@localhost taotao]# firewall-cmd --zone=public --add-port=30000-30999/tcp --permanent 
[root@localhost taotao]# firewall-cmd --reload
```

这样就可以使用ftp服务器上传文件了。

测试

通过ftp连接树莓派系统，以用户名pi登录，密码是raspberry ，即当前系统的用户名密码
ftp的根目录是/home/pi，即pi用户的HOME目录
可上传或下载文件了
如果设置为其他目录 需要在配置文件中添加以下

```bash
local_root=/home/pi/ftp
allow_writeable_chroot=YES
```

这种情况下可能会出现没有文件夹权限 需要给文件夹设置权限

```bash
在linux下执行 sudo chmod -R 777 /home/pi/ftp
```

只需在“快速连接”中输入：
主机：sftp://192.168.1.102 （换成您的树莓派的IP地址。前面的sftp://一定要加）
用户名和密码照实填。（Raspbian默认是pi/raspberry）

### Nginx

- 配置文件：/etc/nginx/nginx.conf
- 默认配置文件：/etc/nginx/conf.d/default.conf
- 默认网页目录：/usr/share/nginx/html

报错

软件卸载遇到问题
The package *** needs to be reinstalled, but I can't find an archive for it.

```bash
E: The package `mlnx-ofed-kernel-dkms` needs to bye reinstalled, but I can't find an archive for it.
sudo dpkg --remove --force-all mlnx-ofed-kernel-dkms(报错软件名)
sudo apt-get update

vi /etc/sysconfig/iptables   添加下面内容
-A INPUT -m state –state NEW -m tcp -p tcp –dport 80 -j ACCEPT（允许80端口通过防火墙） 
-A INPUT -m state –state NEW -m tcp -p tcp –dport 3306 -j ACCEPT（mysql端口  允许3306端口

service iptables restart
```

安装

```bash
vim /etc/yum.repos.d/nginx.repo
[name]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1

sudo apt-get install nginx
或
sudo apt-get install nginx-light
```

启动

```bash
sudo /etc/init.d/nginx start
```

访问  `树莓派IP:80`， 默认 80 端口
修改监听端口
修改nginx配置文件（使得nginx监听上面设定的8888端口）。

```bash
sudo vim /etc/nginx/sites-available/default
```

listen行：修改两处的监听端口

```
server{
	listren 8888 default_server
	listen [;;];8888 default_server
}
```

反向代理

```bash
sudo vim /etc/nginx/sites-available/default
```

先将之前的内容全都注释掉，直接添加以下内容：

```bash
  upstream tomcat-portal {
      server 192.168.31.101:8080;
  }
  server {
    listen    80;
    server_name localhost; 
    location / {
      proxy_pass  http://tomcat-portal;
       index index.html;
   }
 }
```

重新加载

```bash
sudo /etc/init.d/nginx reload 
```

浏览器上访问 树莓派IP:8888

```bash
sudo /etc/init.d/nginx reload 
```

浏览器上访问  树莓派IP:8080
实际上浏览器显示的是 树莓派IP::8080的内容。因为Nginx做了反向代理。
网站web目录

```bash
/var/www/html
```

touch: cannot touch 'index.txt': Permission denied

解决办法：目录没有创建修改权限， 所有人可操作logs文件

> chmod说明(u:与文件属主拥有一样的权限[a:所有人]；+:增加权限;rwx:可读可写可执行）
> -R:递归所有目录和文件

```shell
chmod a+rwx -R logs 
```

或者使用 root 用户

```bash
sudo su //切换到root
```

### DNS

### 电子邮件



### 数据库

PostgreSQL
	postgresql
	登录
		su postgres
		psql
		

			\l
			\c
			\q
	数据库操作
MySQL
	mysql-server
	登录
		mysql -u root
		
			\l
			\c
			\q



### Apache

Apache服务器 httpd
	安装：yum install httpd -y
	启动、停止、重启、自启
		service dhcp httpd status
		systemctl status httpd
			状态
				status
			启动
				start
			停止
				stop
			重启
				restart
	开机自动加载
		systemctl list-unit-files|grep httpd
		systemctl enable\disable httpd
配置Apache服务器httpd.conf



### 代理服务器

tinyproxy服务器

```
yum install dockery -y
docker run -d --name='tinyproxy' -p <Host_Port>:8888 dannydirect/tinyproxy:latest <ACL>
 docker run -d --name='tinyproxy' -p 6666:8888 dannydirect/tinyproxy:latest ANY
 docker run -d --name='tinyproxy' -p 7777:8888 dannydirect/tinyproxy:latest 87.115.60.124
 docker run -d --name='tinyproxy' -p 8888:8888 dannydirect/tinyproxy:latest 10.103.0.100/24 192.168.1.22/16
```

“设置” --> “Internet选项”   “局域网设置” 

### NFS服务器





### 防火墙





安装docker

### 安装方法一

```bash
sudo curl -sSL https://get.docker.com | sh
```

### 安装方法二（apt 安装）

由于 Raspbian 基于 Debian，我们还可以使用 apt 来安装 Docker，首先需要更新一下软件包的索引。

```bash
sudo apt-get update
```

#### 安装 HTTPS 所依赖的包

```bash
sudo apt-get install` `apt-transport-https \``            ``ca-certificates \``            ``software-properties-common
```

安装Samba

`win+r`键打开运行
输入`\\192.168.*.*`(树莓派ip地址)，并输入账号密码，默认账号为pi
可以看到树莓派的共享磁盘，直接点击打开就可以使用了
[samba建立家庭局域网共享中心 ](https://www.cnblogs.com/bowen404/p/12579780.html)
工具：balenaEtcher
镜像：[ubuntu-18.04.4-preinstalled-server-armhf+raspi4..>](https://mirrors.ustc.edu.cn/ubuntu-cdimage/releases/18.04/release/ubuntu-18.04.4-preinstalled-server-armhf%2Braspi4.img.xz.zsync)

## 前端软件

### Node

> [在CentOS 7上安装Node.js的4种方法（yum安装和源码安装） - 与f - 博客园](https://www.cnblogs.com/fps2tao/p/9956139.html)
>
> [Node.js 安装配置 | 菜鸟教程](https://www.runoob.com/nodejs/nodejs-install-setup.html)

- 源码安装 （非常推荐） [下载 | Node.js](https://nodejs.org/zh-cn/download/)

```
yum install wget 
wget https://nodejs.org/dist/v14.17.5/node-v14.17.5.tar.gz 源码
tar xzvf node-v*
目录编译安装 
// sudo yum install gcc gcc-c++
cd node-v*
./configure
make // 编译
sudo make install
```

- 使用NVM安装

```
nvm 安装
curl https://raw.githubusercontent.com/creationix/nvm/v0.13.1/install.sh | bash
source ~/.bash_profile
```

- 使用已编译版本安装

```
wget https://nodejs.org/dist/v14.17.5/node-v14.17.5-linux-x64.tar.xz 已经编译的版本
tar xf  node-v*
xz -d node-v9.8.0-linux-x64.tar.xz
tar -xvf node-v9.8.0-linux-x64.tar
./bin/node -v 
```

- 使用EPEL安装

```
curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash 
yum install -y nodejs
```



## 进阶学习







## Linux美化

切换zsh终端

zsh 和 bash 两种终端

```
查看已安装的 shell
cat /etc/shells 
查看当前 shell
echo $SHELL
切换 shell
chsh -s /bin/zsh
brew install zsh
yum install zsh
# 确认 zsh 成功安装
which zsh
```

安装oh-my-zsh

安装不上

[Ubuntu 安装 oh my zsh 效率翻倍 | CHENSIR](https://chensir.ink/02206e0e927c/#%E6%96%B9%E6%B3%953)

```bash
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh 
sh install.sh

sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

添加 source ~/.bash_profile

```
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
chmod 755 /usr/local/share/zsh
chmod 755 /usr/local/share/zsh/site-functions
```

zsh 默认是加载 ~/.zshrc 文件，默认不加载用户环境变量，所以我们需要在 ~/.zshrc 中添加一行 source ~/.bash_profile，使得他每次启动时都加载 .bash_profile 文件中的环境变量

# Linux发行版本使用



