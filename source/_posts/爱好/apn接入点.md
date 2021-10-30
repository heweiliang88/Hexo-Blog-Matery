---
title: 使用Apn接入点，来突破网速封锁
categories:
- 爱好
tags:
- 流量
abbrlink: 8492
---

#  使用Apn接入点，来突破网速封锁

## APN

> [Apn_百度百科](https://baike.baidu.com/item/apn/96667)

> 接入点名称（英語：APN, Access Point Name），是GPRS等移动网络和另一个计算机网络（通常来说是互联网）之间的网关的名称，用以定義移动设备上所有移动数据連線的網路路徑。 移动设备必须设置了运营商提供的接入点名称才能建立数据连接。
>
> APN指一种网络接入技术，是通过[手机上网](https://baike.baidu.com/item/手机上网/1996688)时必须配置的一个参数，它决定了手机通过哪种接入方式来访问网络。
>
> 对于手机用户来说，可以访问的外部网络类型有很多，例如：[Internet](https://baike.baidu.com/item/Internet/272794)、[WAP网站](https://baike.baidu.com/item/WAP网站/3419865)、集团企业内部网络、行业内部专用网络。而不同的接入点所能访问的范围以及接入的方式是不同的，网络侧如何知道手机激活以后要访问哪个网络从而分配哪个网段的IP呢，这就要靠APN来区分了，即APN决定了用户的手机通过哪种接入方式来访问什么样的网络。

## 电信APN

- ctwap 搭配5g nsa可以限速

```
// 配置一 
名称：ctwap
APN：ctwap 

// 配置二
名称：MMSC
Apn：ctwap
MMSC：
http://mmsc.vnet.mobi
MMS proxy：
10.0.0.200
port：80
Apn Type：mms

// 配置三
名称：Wap
APN：ctwap
Proxy：
10.0.0.200
port：80
Apn Type：default
```

- ctnet

```
// 配置一
名称：ctnet
APN：ctnet 
```


- ctlnet

```
// 配置一
名称：CTLTE 
APN：ctlte 
MCC：460 
MNC：01

// 配置二
名称：ctnet
接入点名称:ctnet
端口：80
用户名：vnet@mycdma.cn
密码：
http://vnet.mobi
服务器地址：
10.0.0.200 
MMSC :
http://mmsc.vnet.mobi
彩信代理：
10.0.0.200
端口：80
MCC:460
MNC:11
身份验证类型：pap或chap
APN类型：default,mms,supl,hirpi
APN协议：IPv4 APN漫游协议：IPv4
其它的不变（未设置）

// 配置三
名称：NET
APN：ctnet
Proxy：
10.0.0.200
port：80
Apn Type：default
其他的都不变
```

## 移动APN

- cmmet

```
CMNET
APN：cmnet
MCC:460
MNC:02
APN类型：default，supl，dun
```

- cmwap

```
CMWAP
APN：cmwap
代理：10.0.0.172
端口：80
MCC:460
MNC:02
APN类型：default,supl,dun
```

- cmwap

```
移动彩信：
名称：彩信
APN：cmwap
MMSC:mmsc.monternet.com
彩信代理：10.0.0.172
彩信端口：80
```

## 联通APN

- uninet

```
联通APN
名称:UNINET
APN:uninet
MCC:460
MNC:01
APN类型:default
承载系统：LET
保存选择就可以了
```

- scuiot

```
名称:SCUIOT
APN:scuiot
```

- cuiot

```
名称:CUIOT
APN:cuiot
```

- cmtds

```
名称：CMTDS
APN:cmtds
```

- wonet

```
名称:WONET
APN:wonet
MCC:460
MNC:01
身份验证：无
APN类型：default,supl,dun （这个自己测试）
```

- 3gnet

```
名称:3GNET
APN:3gnet
```

- 3gwap

```
各称:3GWAP
APN:3gwap
代理服务器地址:
10.0.0.172
端口:80
```

