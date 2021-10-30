---
title: Python爬虫
categories:
- Python
tags:
- python爬虫
abbrlink: 41902
---
# python爬虫 

## 基础知识

爬虫：爬虫就是模拟客户端（浏览器）发送网络请求，获取响应，按照规制提取数据的查询

数据处理

- 直接呈现：展现在网页或   者app中
- 进行分析：从数据中寻找一些规律

### 计算机网络

HTTP和HTTPS

HTTP协议

概念

- Hypertext Transer Protocol,超文本传输协议
- HTTP是一个基于“请求与响应模式的、无状态的应用层协议”
- HTTP协议采用URL作为定位网络资源的标识

例子：url = http://host: post /path

​		http/https 请求协议

​		host:internet主机域名或IP地址
​		port:端口号，缺省端口为80
​		path:请求资源的路径

​		url = 请求协议+网站域名+资源路径+参数

请求url地址

- 浏览器请求的url地址（网页）

  当前url对应的响应+js+css+图片+视频 ======》elements中的内容

- 爬虫请求的url地址（网页源码和相应的资源）

  当前url对应的响应

- element的内容和爬虫获取到的url地址的响应不同，爬虫中需要以当前url地址对应的响应为准提取数据

资源的操作

|                  |                                            |
| ---------------- | ------------------------------------------ |
| **GET**获取      | 请求获取URL位置的资源                      |
| **HEAD头部信息** | 获取该资源的头部信息                       |
| **POST**         | 向URL位置的资源附加新的数据                |
| **PUT**          | 向URL位置存储一个资源，覆盖原URL位置的资源 |
| **PATCH更新**    | 更新URL位置的资源<br/>		节省网络带宽 |
| **DELETE删除**   | 删除URL位置存储的资源                      |

HTTP协议之请求

- 请求行

- 请求头


​	User-Agent:用户代理 对方浏览器能通过user-agent知道当前请求对方资源的是什么浏览器

​	Cookie:用来存储用户信息的，每次请求会被携带上发送给对方的浏览器

​	要获取登录才能访问的页面

​	对方的服务器会通过Cookie来判断我们是是一个爬虫

- 请求体（post）


​	get请求没有请求体，post请求有请求体，

​	get请求把数据放在url地址中，post请求常用于登录注册，传输大文本的时候

6. HTTP协议之响应

- 响应头

   set-Cookie:对方服务器通过该字段设置cookie到本地

- 响应体

    url地址对应的响应   

**HTTPS协议** HTTP+SSL(安全套接字层)

传输之前先加密，之后解密获取内容

超文本加密协议

HTTP与HTTPS的区别

HTTP 以明文形式传输（不安全）、效率高、不安全

HTTPS SSL的方式加密，效率低、不安全

## Requests

爬取HTML页面自动网络请求提交

###### 概念

- 自动爬取HTML页面自动网络请求提交
- 小规模、数据量小、爬取速度不敏感
- Requests 是用**Python**语言编写，基于 urllib，采用 Apache2 Licensed 开源协议的 HTTP 库。
- 它比 urllib 更加方便，可以节约我们大量的工作，完全满足 HTTP 测试需求。

- Requests 的哲学是以 PEP 20 的习语为中心开发的，所以它比 urllib 更加 Pythoner。更重要的一点是它支持 Python3 哦！

###### 安装

```python
pip install requests
```

```git
$ git clone git://github.com/kennethreitz/requests.git
$ cd requests
$ python setup.py install
```

###### requests方法

**requests()**

**get(url)**

- 获取HTML网页的主要方法，HTTP的GET

  ```python
  import requests
  url = "http://baidu.com"
  response = requests.get(url)
  print(response.status_code)
  print(response)
  print(response.text)
  ```

**head()**

- 获取HTML网页头信息的方法，HTTP的head

**post(url,data={请求体的字典},headers=headers)**

- 向网页提交post请求，对应于HTTP的post

**put()**

- 向网页提交put请求，对应于HTTP的put

**patch()**

- 向网页提交局部修改请求，对应于HTTP的patch

**delete()**

- 向HTML页面提交删除请求，对应于HTTP的delete

**url**

返回网页的地址

**status_code**

- 状态码

###### response对象的属性

出现乱码：解码的使用方法

```python
response.encoding="utf-8"
response.text
```

```python
# 把响应的二进制字节转化为str类型
response.content.decode()
response.content.decode("gbk")
```

###### 发送带header的请求 post/get

headers

```python
# 复制内容位置Google控制台—>NetWork->Name->Request Headers
#手机headers
headers = {
    "user-agent":
    "Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 		(KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1",
    "referer":"https://fanyi.baidu.com/"
}
#电脑header2

headers = {
    "User-Agent": 
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36"
}

```

```python
response = requests.post(url,data=data_string,headers=headers)
```

```
response = requests.get(url,headers=headers)
```

response.request.url 发送请求的url地址

response.url     response响应的url地址

respone.request.headers 请求头

response.headers 响应请求

```python
from retrying import retry
@retry(stop_max_attempt_number=3)
def fun():
    print("this is func")
    reise ValueError("this is test error")
```

```python
import requests
url = "https://www.baidu.com/"
headers = {
    "User-Agent":
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36"
}
response = requests.get(url,headers=headers)
# print(response.content.decode())
print(response.request.headers)
print(response.headers)
print(response.url)
print(response.request.url)
# print(response.text)

{'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) \t   Chrome/80.0.3987.106 Safari/537.36', 'Accept-Encoding': 'gzip, deflate', 'Accept': '*/*', 'Connection': 'keep-alive'}
{'Bdpagetype': '1'.....}
https://www.baidu.com/
https://www.baidu.com/
```

百度翻译例子 

```python
import requests
url = "https://fanyi.baidu.com/basetrans"
data_string = {
   "query":"百度翻译",
   "from":"zh",
   "to":"en"}
headers = {
    "user-agent":
    "Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1",
    # "referer":"https://fanyi.baidu.com/"
}
response = requests.post(url,data=data_string,headers=headers)
print(response)
print(response.content.decode())
```

获取完整的源代码

```python
import requests
url = "https://www.baidu.com/"
headers = {
    "User-Agent":
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36"
}
response = requests.get(url,headers=headers)
# print(response.content.decode())
print(response.text)
```

###### 搜索引擎关键词提交接口

1. 百度

- https://www.baidu.com/s?wd=keyword

2. 360

- https://www.so.com/s?s?q=keyword

###### Retrying模块（解决超时请求问题的库）

1. 超时参数

```python
response = requests.get(url,headers=headers,timeout=3)   3秒内返回响应，否则会报错
```

2. 安装

```python
pip install retrying
```

3. 模板

```python
import requests
from retrying import retry

headers = {
    "User-Agent":
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36"
}
@retry(stop_max_attempt_number=3)
# 让被函数装饰的函数反复执行三次，中间有次正常则退出
def _parse_url(url):
    print("*"*10)
    response = requests.get(url,headers=headers,timeout=5)
    return response.content.decode()

def parse_url(url):
    try:
        html_str = _parse_url(url)
    except:
        html_str = None
    return  html_str

if __name__ == '__main__':
    # 正确的url地址
    url = "http://www.baidu.com"
    # 错误的url地址
    url2 = "www.baidu.com"
    print(parse_url(url)[:100])
    print(parse_url(url2))
```

###### Cookie的相关请求

1. 直接携带cookie请求url地址

   - cookie放在headers中

   ```
   headers={
   	"Uset-Ageng":" ",
   	"Cookie":" "
   }
   ```

   - cookie字典传输给cookies参数

   ```python
   requests.get(url,cookies=cookie_dict)
   ```

   ```python
   import requests
   url = "https://www.bilibili.com/"
   headers = {"User-Agent":
       "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, 		like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36",
       #第一种方法 headers
        "Cookie": "_uuid=D60C295E-EEF8-A0E4-B466C58C6D88E65A82945infoc; "
   }
   #第二种方法 字典
   cookie_dict = { 
       # _uuid=D60C295E-EEF8-A0E4-B466C58C6D88E65A82945infoc;
   	i.split("=")[0]:i.split("=")[-1] for i in cookie.split("; ")
   }
   
   response = requests.get(url,headers=headers)
   # response = requests.get(url,headers=headers,cookies=cookie_dict)
   with open("E01.html","w",encoding="utf-8") as f: 
       f.write(response.content.decode())
   ```

   2.先发送post请求，获取cookie,带上cookie请求登录后的页面

    Seesion参数

    方法

   ```python
   #session 具有的方法和requests一样
   seesion = requests.session()
   #服务器设置在本地的cookie会保存在session中
   session.post(url,data,headers)
   #会带上之前保存在session中的cookie
   sesion.get(url)
   ```

   例子

   ```python
   import requests
   #实例化session
   session = requests.session()
   #表单的form的action的url地址
   post_url = ""
   headers = {}
   post_data = {"email":"","password":""}
   session.post(post_url,header=headers,data=post_data)
   # 在使用session 请求登录后的页面
   #网页登录地址
   url = ""
   response = session.get(url,headers=headers)
   with open("文件","w",encoding="utf-8") as f:
       f.write(response.content.decode())
   ```
   
   解决：action url 地址在源代码中不可见的情况
   
   Google控制台功能：选项Preserver log功能解决网页跳转时响应文件的丢失
   
   可以找出login的action的url地址

###### 数据提取方法值json

json 是一种数据交换格式，像python类型（列表、字典）的字符串

json.loads

哪里会返回json的数据

​	流程器切换到手机版

​    抓包app

把json字符串转换为python类型：json.loads(json)字符串

```python
str = input("请输入中文：")
print(str)
```

```python
import requests
url = "https://fanyi.baidu.com/basetrans"

query_str = input("输入要翻译的中文：")
data_string = {
   "query":query_str,
   "from":"zh",
   "to":"en"}
headers = {
    "user-agent":
    "Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1",
    "cookie":"值"
    # "referer":"https://fanyi.baidu.com/"
}
response = requests.post(url,data=data_string,headers=headers)
json_str = response.content.decode()
jsons = json.loads(json_str)
print(jsons)  
print(type(jsons)) #查看类型 字典类型
ret = jsons["trans"][0]["dst"]
print("翻译结果：",ret)
```

把python类型转换为json字符串：json。dumps("a:"a",b:"b")字符串

json.dumps({ })

json.dumps(ret1,ensure_ascii=False,indent=2)

​	ensure_ascil:让中文显示成中文

​	indent:能够让下一行在上一行的基础上空格



###### 数据提取方法值xpath和xml模块的学习

**一门从html中提取数据的语言**

xpath语法:

xpath helper插件：帮助我们从elements中定位数据

使用

 选择节点

1. /html/head/meta :能够选中html下的所有的meta标签

2. //：能够从任意节点开始

3. //li ：当前页面上的所有的li标签

4. /html/head//link:head下所有的link标签

5. @符号的用途  选择具体的某个元素

6. //div[@class='class值']/ul/li 选择  class=''的div下的ul下的li标签

   a/@href：选择a的href的值

7. 获取文本  /a/text() text()方法  

8. 获取a下的所有文本  /a//text()

9. ./当前节点


lxml 

安装

```python
 pip install lxml
```

使用

```python
from lxml import etree
element = etree.HTML("html字符串（ response.content.decode()）")
element.xpath("xpath地址")
```

基础知识

1. 列表推导式

- 帮助我们快速的生成包含一堆数据的列表

```python
[i+10 for i in range(10)] 
# ---->[10,11,12,......,19]

["10月{}日".format(i) for i in range(1,10)] 
# ------>['"10月1日","10月2日"......."10月9日"]
```

format:字符串格式化的一种方式

使用："百度{}网盘".format("1")

"百度{}网盘".format([1,2,3,4])

"百度{}网盘{}".format({1,2,3,4},[1,2,3,4])

"百度{}网盘{}".format({1,2,3,4},1)

2. 字典推导式

- 帮助我们快速生成包含一堆数据的字典

```python
{i+10:i  for i in range(10)}
#{10:0,11:1,.....19:9}
{"a{}".format(i):10 for i in range(2)}
#{"a0":10,"a1":10,"a2":10}
```

3. 三元运算符

- if 后面的条件成立，就把if前面的结果赋值给a,否则把else后面的结果赋值给a

```python
a = 10 if 4>3 else 20 	#a = 10
a = 10 if 4<3 else 20   #a = 20
```

###### 写爬虫的讨论

1. url（知道url地址的规律和总得页码数）:构造url地址地列表

   start_url

2. 发送请求，获取响应

   requests

3. 提取数据

   返回json字符串:json模块

   返回的是html字符串：lxml模块配合xpath提取数据

4. 保存

###### Python中self用法

https://blog.csdn.net/CLHugh/article/details/75000104

self.xx是类里面的全局变量.

如果你知道java或者javascript中的this，那么self的作用和他们是一样的，不过我猜你可能也没接触过这两门语言。





## Beautiful Soup

bs4 是解析、遍历、维护标签树的功能库,对应一个HTML/XML文档的全部内容

###### 概念

- 解析HTML页面信息标记与提取方法
- 解析、遍历、维护标签树的功能库,对应一个HTML/XML文档的全部内容

###### 安装

```cmd
pip install beautifulsoup4
```

###### 使用

```python
# 引用方式：
from bs4 import BeautifulSoup||import bs4
soup = BeautifulSoup("<html>data</html>",'html.parser')
soup = BeautifulSoup(open("D://demo.html"),'html.parser')
soup.prettify()
```

###### 基本元素

###### 遍历方法

**上行遍历**

- .parent 父亲标签
- .parents  迭代类型 先辈

**下行遍历**

**平行遍历**

- .next_sibling 文本顺序的平行节点的下一个节点
- .previous.sibling 文本顺序的平行节点的上一个节点
- .next_siblings 迭代类型，文本顺序的平行节点的遍历后续节点
- .previous.siblings 迭代类型，文本顺序的平行节点的遍历前续节点

**扩展方法**

**简便写法**

**信息的标记**

**信息的提取**



###### 解析器

安装

```cmd
pip install lxml
pip install html5lib
```

分类

```python
bs4的HTML解析器
BeautifulSoup(mk,'html.parser')
lxml的HTML解析器
BeautifulSoup(mk,'lxml') 
**lxml的XML解析器**
BeautifulSoup(mk,,'xml')
**html5lib的HTML解析器** 
BeautifulSoup(mk,'html5lib')
```



## robots.txt

### robots.txt

- 网络爬虫排除标准

### 来源审查

- 判断User-Agent进行限制
- 检查来访HTTP协议头的User-Agent域，响应浏览器或友好爬虫的访问

### 分布公告

- Robots协议、Rebot Exclusion Standard、网络爬虫排除标准
- robots.txt文件、告知所有爬虫网站的爬取策略

## Scrapy





## 实例

```python
import requests
r = requests.get("https://www.baidu.com/")
print(r.status_code)     #获取网页状态码
print(r.url)             #获取网址
print(r.text)            #获取网页源代码
```

IDE安装

爬取源代码

```python
import requests
url = "http://www.baidu.com"
headers = {
    "User-Agent":
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36"
}
respones = requests.get(url,header=header)
print(respones.content.encode())
# print(response.text())
```

爬取指定文字

```python
# coding=utf-8

import urllib2
import urllib
import re
import thread
import time
from bs4 import BeautifulSoup

url="http://toutiao.sogou.com/?fr=qqxwtt"
page = urllib.urlopen(url)#打开网址
html = page.read()        #读取网页内容，保存到htlm中
bs0bj=BeautifulSoup(html) #创建一个beautifulsoup的类
namelist=bs0bj.findAll("a")#通过标签筛选文字信息

for name in namelist:
    print (name.get_text())
```

爬取单张图片

```python
# 爬取图片
import requests
import os
root = "D:/Downloads/"
url = "http://b-ssl.duitang.com/uploads/item/201305/26/20130526140022_5fMJe.jpeg"
path = root +url.split('/')[-1]
try:
    if not os.path.exists(root):
        os.mkdir(root)
    if not os.path.exists(path):
        r = requests.get(url)
        with open(path,'wb') as f:
            f.write(r.content)
            f.close()
            print("成功")
    else:
        print("已保存")
except:
    print("失败")
```

爬取多张图片



爬取一个视频



爬取多个视频



百度翻译

[百度翻译API注册入口]:http://api.fanyi.baidu.com/

（python3）

```python
# coding: utf8
'''
    @Author: LCY
    @Contact: lchuanyong@126.com
    @blog: http://http://blog.csdn.net/lcyong_
    @Date: 2018-01-15
    @Time: 19:19
    说明： appid和secretKey为百度翻译文档中自带的，需要切换为自己的
           python2和python3部分库名称更改对应如下：
           httplib      ---->    http.client
           md5          ---->    hashlib.md5
           urllib.quote ---->    urllib.parse.quote
    官方链接：
           http://api.fanyi.baidu.com/api/trans/product/index
           
'''
 
import http.client
import hashlib
import json
import urllib
import random
 
def baidu_translate(content):
    #appid api id 密钥 我的翻译地址myurl
    appid = '20151113000005349'
    secretKey = 'osubCEzlGjzvw8qdQc41'
    httpClient = None
    myurl = '/api/trans/vip/translate'
    
    q = content
    fromLang = 'zh' # 源语言
    toLang = 'en'   # 翻译后的语言
    salt = random.randint(32768, 65536)
    sign = appid + q + str(salt) + secretKey
    sign = hashlib.md5(sign.encode()).hexdigest()
    myurl = myurl + '?appid=' + appid + '&q=' + urllib.parse.quote(
        q) + '&from=' + fromLang + '&to=' + toLang + '&salt=' + str(
        salt) + '&sign=' + sign
 
    try:
        httpClient = http.client.HTTPConnection('api.fanyi.baidu.com')
        httpClient.request('GET', myurl)
        # response是HTTPResponse对象
        response = httpClient.getresponse()
        jsonResponse = response.read().decode("utf-8")# 获得返回的结果，结果为json格式
        js = json.loads(jsonResponse)  # 将json格式的结果转换字典结构
        dst = str(js["trans_result"][0]["dst"])  # 取得翻译后的文本结果
        print(dst) # 打印结果
    except Exception as e:
        print(e)
    finally:
        if httpClient:
            httpClient.close()
 
if __name__ == '__main__':
    while True:  #死循环
        print("请输入要翻译的内容,如果退出输入q")
        content = input()
        if (content == 'q'):
            break  #q退出
        baidu_translate(content)
```

官方（python2）

```python
#/usr/bin/env python
#coding=utf8
 
import httplib
import md5
import urllib
import random
 
appid = '20151113000005349'
secretKey = 'osubCEzlGjzvw8qdQc41'
 
 
httpClient = None
myurl = '/api/trans/vip/translate'
q = 'apple'
fromLang = 'en'
toLang = 'zh'
salt = random.randint(32768, 65536)
 
sign = appid+q+str(salt)+secretKey
m1 = md5.new()
m1.update(sign)
sign = m1.hexdigest()
myurl = myurl+'?appid='+appid+'&q='+urllib.quote(q)+'&from='+fromLang+'&to='+toLang+'&salt='+str(salt)+'&sign='+sign
 
try:
    httpClient = httplib.HTTPConnection('api.fanyi.baidu.com')
    httpClient.request('GET', myurl)
 
    #response是HTTPResponse对象
    response = httpClient.getresponse()
    print response.read()
except Exception, e:
    print e
finally:
    if httpClient:
        httpClient.close()
```

```python
import requests
from lxml import etree
import json

class BiliBiliSpider:
    def __init__(self):
        self.url_temp ="https://www.bilibili.com/v/dance/otaku/#/all/default/0/{}/"
        self.headers = {
            "User-Agent":
                "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko)     Chrome/80.0.3987.106 Safari/537.36"
        }

    # 1.根据url地址的规律，构造url list
    def get_url_list(self):
        url_list = [self.url_temp.format(i) for i in range(1,10)]
        return url_list

    # 2.发送请求，获取响应
    def parse_url(self,url):
        response = requests.get(url,headers=self.headers)
        return  response.content.decode()

    # 3.提取数据
    def get_content_list(self,html_str):
        html = etree.HTML(html_str)
        #1.分组
        div_list = html.xpath("//*[@class=vd-list-cnt]")
        print(div_list)
        content_list = []
        for div in div_list:
            item = []
            # //*[@id="videolist_box"]/div[2]
            item[""] = div.xpath(".//ul/li[1]/div/div[2]/a[@title]")
            content_list.append(item)
        print(content_list)
        return  content_list

    # 4.保存
    def save_content_list(self,content_list):
        with open("bilibili.txt","w",encoding="UTF-8") as f:
            for content in content_list:
                f.write(json.dumps(content,ensure_ascii=False))
                f.write("\n")

        print("保存成功")

    def run(self):#实现主要逻辑
        #1.根据url地址的规律，构造url list
        url_list = self.get_url_list()
        #2.发送请求，获取响应
        for url in url_list:

            html_str = self.parse_url(url)
        # 3.提取数据
            content_list = self.get_content_list(html_str)
        #4.保存
            print(url)
            self.save_content_list(content_list)

# 主函数
if __name__ == '__main__':
   bilibili = BiliBiliSpider()
   bilibili.run()
```

https://zhuanlan.zhihu.com/p/73742321





```
import threading
import time
import requests
from bs4 import BeautifulSoup
import os
import random

url = "http://www.mzitu.com/all"
''' 获取html页面'''

def downHtml(url):
    headers = {
        'User-Agent': "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/42.0.2311.135 Safari/537.36 Edge/12.10240",
        'Connection': 'Keep-Alive',
        'Referer': "http://www.mzitu.com/99566"
    }
    return requests.get(url, headers=headers).text

''' 解析获取所有的妹子url  '''

def parseHtml(html):
    soup = BeautifulSoup(html, "lxml")
    list = soup.select("a[target='_blank']")
    mylist = [];
    count = 0  # 添加一个统计链接的数量
    for a in list:
        # print(a["href"], a.get_text())
        # print(a["href"])
        mylist.append(a["href"])
    return mylist
    # print(count)
    #     print(mylist)
    # print(len(mylist))


''' 获取妹子所有图片的数量 '''

def get_pic_num(html):
    soup = BeautifulSoup(html, "lxml")
    list = soup.find("div", class_="pagenavi").find_all("span")
    # print(list)
    # list [<span>«上一组</span>, <span>1</span>, <span>2</span>, <span>3</span>, <span>4</span>, <span class="dots">…</span>, <span>65</span>, <span>下一页»</span>]
    return int(list[-2].string)  # ？

''' 获取妹子的图片 '''


# 获取所有妹子的url
def get_pic(html):
    soup = BeautifulSoup(html, "lxml")
    img = soup.find("div", class_="main-image").find_all("img")
    print(img[0]["src"], img[0]["alt"])
    download_pic(img[0]["src"], img[0]["alt"])
    
''' 下载妹子的图片 '''
def download_pic(url, himg):
    headers = {
        'User-Agent': "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/42.0.2311.135 Safari/537.36 Edge/12.10240",
        'Connection': 'Keep-Alive',
        'Referer': "http://www.mzitu.com/99566"
    }
    img = requests.get(url, headers=headers)

    t = time.time()
    nowTime = lambda: int(round(t * 1000))

    # soup = BeautifulSoup(html, "lxml")
    # img = soup.find("div", class_="main-image").find_all("img")
    # pname = img[0]["src"]
    print(himg)
    folder = os.path.exists("H:\mztu\\" + himg)
    if not folder:  # 判断是否存在文件夹如果不存在则创建为文件夹
        os.makedirs("H:\mztu\\" + himg)
    with open("H:\mztu\{}\{}.jpg".format(himg, nowTime()), 'ab') as f:
        f.write(img.content)

# 创建文件夹
html = downHtml(url)
list = parseHtml(html)
# print(list)

for url in list:
    # print(src)
    # 获取妹子所有的图片
    html = downHtml(url)
    num = get_pic_num(html)
    print(num)
    for i in range(num):
        str = "{}{}{}".format(url, "/", i + 1)
        html = downHtml(str)
        t = threading.Thread(target=get_pic, args=(html,))
        t.start()
        t.join()
```

### WebMagic

19/11/06-19/11/09

#### 开源爬虫分类：  

1. 分布式爬虫：Nutch  

2. JAVA单机爬虫：Crawler4j、WebMagic、WebCollector  

3. 非JAVA单机爬虫：scrapy  

##### 各种网络爬虫

网络爬虫有两个基本的任务，发现包含有效信息的URL和下载网页



#### Jsoup



## Beautiful Soup 4.4.0 **文档** https://beautifulsoup.readthedocs.io/zh_CN/v4.4.0/

Beautiful Soup](http://www.crummy.com/software/BeautifulSoup/) 是一个可以从HTML或XML文件中提取数据的Python库

安装Beautiful Soup

```
pip install BeautifulSoup
```

安装解析器 lxml /html5lib

Beautiful Soup支持Python标准库中的HTML解析器,还支持一些第三方的解析器,其中一个是 [lxml](http://lxml.de/) .根据操作系统不同,可以选择下列方法来安装lxml:

```
pip install lxml
```

另一个可供选择的解析器是纯Python实现的 [html5lib](http://code.google.com/p/html5lib/) , html5lib的解析方式与浏览器相同,可以选择下列方法来安装html5lib:

```
pip install html5lib
```

主要的解析器,以及它们的优缺点:



使用BeautifulSoup解析这段代码,能够得到一个 `BeautifulSoup` 的对象,并能按照标准的缩进格式的结构输出



```

```



简单浏览数据的方法

```python
# 标题带标签
soup.title
<title>The Dormouse's story</title>
# 标题标签	
soup.title.name
'title'
# 标题
soup.title.string
'The Dormouse's story'
#
soup.p
#
soup.p['class']
<p class="title"><b>The Dormouse's story</b></p>
#
soup.a
#
soup.find_all('a')
#
soup.find(id="link3")
```

## python爬虫 （2020.2.25-2.28）

#### 基础知识

**爬虫**

- 爬虫就是模拟客户端（浏览器）发送网络请求，获取响应，按照规制提取数据的查询

**数据处理**

- 直接呈现：展现在网页或   者app中
- 进行分析：从数据中寻找一些规律

**浏览器的请求**

**HTTP和HTTPS**

**HTTP协议**

1. 概念

- Hypertext Transer Protocol,超文本传输协议
- HTTP是一个基于“请求与响应模式的、无状态的应用层协议”
- HTTP协议采用URL作为定位网络资源的标识

2. 例子：url = http://host: post /path

​		http/https 请求协议

​		host:internet主机域名或IP地址
​		port:端口号，缺省端口为80
​		path:请求资源的路径

​		url = 请求协议+网站域名+资源路径+参数

3. 请求url地址

- 浏览器请求的url地址（网页）

	当前url对应的响应+js+css+图片+视频 ======》elements中的内容

- 爬虫请求的url地址（网页源码和相应的资源）

	当前url对应的响应

- element的内容和爬虫获取到的url地址的响应不同，爬虫中需要以当前url地址对应的响应为准提取数据

4. 资源的操作
	**GET**获取
			请求获取URL位置的资源
	**HEAD头部信息**
			获取该资源的头部信息
	**POST**
			向URL位置的资源附加新的数据
	**PUT**
			向URL位置存储一个资源，覆盖原URL位置的资源
	**PATCH更新**
			更新URL位置的资源
			节省网络带宽
	**DELETE删除**
				删除URL位置存储的资源

5. HTTP协议之请求

- 请求行

- 请求头


​	User-Agent:用户代理 对方浏览器能通过user-agent知道当前请求对方资源的是什么浏览器

​	Cookie:用来存储用户信息的，每次请求会被携带上发送给对方的浏览器

​	要获取登录才能访问的页面

​	对方的服务器会通过Cookie来判断我们是是一个爬虫

- 请求体（post）


​	get请求没有请求体，post请求有请求体，

​	get请求把数据放在url地址中，post请求常用于登录注册，传输大文本的时候

6. HTTP协议之响应

- 响应头

	set-Cookie:对方服务器通过该字段设置cookie到本地

- 响应体

	url地址对应的响应   

**HTTPS协议** HTTP+SSL(安全套接字层)

传输之前先加密，之后解密获取内容

超文本加密协议

HTTP与HTTPS的区别

HTTP 以明文形式传输（不安全）、效率高、不安全

HTTPS SSL的方式加密，效率低、不安全



#### Requests + Beautiful Soup + robots.txt(初级)

#### Requests	爬取HTML页面自动网络请求提交

###### 概念

- 自动爬取HTML页面自动网络请求提交
- 小规模、数据量小、爬取速度不敏感
- Requests 是用**Python**语言编写，基于 urllib，采用 Apache2 Licensed 开源协议的 HTTP 库。
- 它比 urllib 更加方便，可以节约我们大量的工作，完全满足 HTTP 测试需求。

- Requests 的哲学是以 PEP 20 的习语为中心开发的，所以它比 urllib 更加 Pythoner。更重要的一点是它支持 Python3 哦！

###### 安装

```python
pip install requests
```

```git
$ git clone git://github.com/kennethreitz/requests.git
$ cd requests
$ python setup.py install
```



###### requests方法

**requests()**

**get(url)**

- 获取HTML网页的主要方法，HTTP的GET

	```python
	import requests
	url = "http://baidu.com"
	response = requests.get(url)
	print(response.status_code)
	print(response)
	print(response.text)
	```

**head()**

- 获取HTML网页头信息的方法，HTTP的head

**post(url,data={请求体的字典},headers=headers)**

- 向网页提交post请求，对应于HTTP的post

**put()**

- 向网页提交put请求，对应于HTTP的put

**patch()**

- 向网页提交局部修改请求，对应于HTTP的patch

**delete()**

- 向HTML页面提交删除请求，对应于HTTP的delete

**url**

返回网页的地址

**status_code**

- 状态码



###### response对象的属性

出现乱码：解码的使用方法

```python
response.encoding="utf-8"
response.text
```

```python
# 把响应的二进制字节转化为str类型
response.content.decode()
response.content.decode("gbk")
```

###### 发送带header的请求 post/get

headers

```python
# 复制内容位置Google控制台—>NetWork->Name->Request Headers
#手机headers
headers = {
    "user-agent":
    "Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 		(KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1",
    "referer":"https://fanyi.baidu.com/"
}
#电脑header2

headers = {
    "User-Agent": 
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36"
}

```

```python
response = requests.post(url,data=data_string,headers=headers)
```

```
response = requests.get(url,headers=headers)
```

response.request.url 发送请求的url地址

response.url     response响应的url地址

respone.request.headers 请求头

response.headers 响应请求

```python
from retrying import retry
@retry(stop_max_attempt_number=3)
def fun():
    print("this is func")
    reise ValueError("this is test error")
```

```python
import requests
url = "https://www.baidu.com/"
headers = {
    "User-Agent":
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36"
}
response = requests.get(url,headers=headers)
# print(response.content.decode())
print(response.request.headers)
print(response.headers)
print(response.url)
print(response.request.url)
# print(response.text)

{'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) \t   Chrome/80.0.3987.106 Safari/537.36', 'Accept-Encoding': 'gzip, deflate', 'Accept': '*/*', 'Connection': 'keep-alive'}
{'Bdpagetype': '1'.....}
https://www.baidu.com/
https://www.baidu.com/
```

百度翻译例子 

```python
import requests
url = "https://fanyi.baidu.com/basetrans"
data_string = {
   "query":"百度翻译",
   "from":"zh",
   "to":"en"}
headers = {
    "user-agent":
    "Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1",
    # "referer":"https://fanyi.baidu.com/"
}
response = requests.post(url,data=data_string,headers=headers)
print(response)
print(response.content.decode())
```

获取完整的源代码

```python
import requests
url = "https://www.baidu.com/"
headers = {
    "User-Agent":
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36"
}
response = requests.get(url,headers=headers)
# print(response.content.decode())
print(response.text)
```



###### 搜索引擎关键词提交接口

1. 百度

- https://www.baidu.com/s?wd=keyword

2. 360

- https://www.so.com/s?s?q=keyword

3. 实例



###### Retrying模块（解决超时请求问题的库）

1. 超时参数

```python
response = requests.get(url,headers=headers,timeout=3)   3秒内返回响应，否则会报错
```

2. 安装

```python
pip install retrying
```

3. 模板

```python
import requests
from retrying import retry

headers = {
    "User-Agent":
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36"
}
@retry(stop_max_attempt_number=3)
# 让被函数装饰的函数反复执行三次，中间有次正常则退出
def _parse_url(url):
    print("*"*10)
    response = requests.get(url,headers=headers,timeout=5)
    return response.content.decode()

def parse_url(url):
    try:
        html_str = _parse_url(url)
    except:
        html_str = None
    return  html_str

if __name__ == '__main__':
    # 正确的url地址
    url = "http://www.baidu.com"
    # 错误的url地址
    url2 = "www.baidu.com"
    print(parse_url(url)[:100])
    print(parse_url(url2))
```



###### Cookie的相关请求

1. 直接携带cookie请求url地址

	- cookie放在headers中

	```
	headers={
		"Uset-Ageng":" ",
		"Cookie":" "
	}
	```

	- cookie字典传输给cookies参数

	```python
	requests.get(url,cookies=cookie_dict)
	```

	```python
	import requests
	url = "https://www.bilibili.com/"
	headers = {"User-Agent":
	    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, 		like Gecko) 	   Chrome/80.0.3987.106 Safari/537.36",
	    #第一种方法 headers
	     "Cookie": "_uuid=D60C295E-EEF8-A0E4-B466C58C6D88E65A82945infoc; "
	}
	#第二种方法 字典
	cookie_dict = { 
	    # _uuid=D60C295E-EEF8-A0E4-B466C58C6D88E65A82945infoc;
		i.split("=")[0]:i.split("=")[-1] for i in cookie.split("; ")
	}
	
	response = requests.get(url,headers=headers)
	# response = requests.get(url,headers=headers,cookies=cookie_dict)
	with open("E01.html","w",encoding="utf-8") as f: 
	    f.write(response.content.decode())
	```

	2.先发送post请求，获取cookie,带上cookie请求登录后的页面

	 Seesion参数

	 方法

	```python
	#session 具有的方法和requests一样
	seesion = requests.session()
	#服务器设置在本地的cookie会保存在session中
	session.post(url,data,headers)
	#会带上之前保存在session中的cookie
	sesion.get(url)
	```

	例子

	```python
	import requests
	#实例化session
	session = requests.session()
	#表单的form的action的url地址
	post_url = ""
	headers = {}
	post_data = {"email":"","password":""}
	session.post(post_url,header=headers,data=post_data)
	# 在使用session 请求登录后的页面
	#网页登录地址
	url = ""
	response = session.get(url,headers=headers)
	with open("文件","w",encoding="utf-8") as f:
	    f.write(response.content.decode())
	```

	解决：action url 地址在源代码中不可见的情况

	Google控制台功能：选项Preserver log功能解决网页跳转时响应文件的丢失

	可以找出login的action的url地址



###### 数据提取方法值json

json 是一种数据交换格式，像python类型（列表、字典）的字符串

json.loads

哪里会返回json的数据

​	流程器切换到手机版

​    抓包app

把json字符串转换为python类型：json.loads(json)字符串

```python
str = input("请输入中文：")
print(str)
```

```python
import requests
url = "https://fanyi.baidu.com/basetrans"

query_str = input("输入要翻译的中文：")
data_string = {
   "query":query_str,
   "from":"zh",
   "to":"en"}
headers = {
    "user-agent":
    "Mozilla/5.0 (iPhone; CPU iPhone OS 13_2_3 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/13.0.3 Mobile/15E148 Safari/604.1",
    "cookie":"值"
    # "referer":"https://fanyi.baidu.com/"
}
response = requests.post(url,data=data_string,headers=headers)
json_str = response.content.decode()
jsons = json.loads(json_str)
print(jsons)  
print(type(jsons)) #查看类型 字典类型
ret = jsons["trans"][0]["dst"]
print("翻译结果：",ret)
```

把python类型转换为json字符串：json。dumps("a:"a",b:"b")字符串

json.dumps({ })

json.dumps(ret1,ensure_ascii=False,indent=2)

​	ensure_ascil:让中文显示成中文

​	indent:能够让下一行在上一行的基础上空格



###### 数据提取方法值xpath和xml模块的学习

**一门从html中提取数据的语言**

xpath语法:

xpath helper插件：帮助我们从elements中定位数据

使用

 选择节点

1. /html/head/meta :能够选中html下的所有的meta标签

2. //：能够从任意节点开始

3. //li ：当前页面上的所有的li标签

4. /html/head//link:head下所有的link标签

5. @符号的用途  选择具体的某个元素

6. //div[@class='class值']/ul/li 选择  class=''的div下的ul下的li标签

	a/@href：选择a的href的值

7. 获取文本  /a/text() text()方法  

8. 获取a下的所有文本  /a//text()

9. ./当前节点

	

lxml 

安装

```python
 pip install lxml
```

使用

```python
from lxml import etree
element = etree.HTML("html字符串（ response.content.decode()）")
element.xpath("xpath地址")
```



基础知识

1. 列表推导式

- 帮助我们快速的生成包含一堆数据的列表

```python
[i+10 for i in range(10)] 
# ---->[10,11,12,......,19]

["10月{}日".format(i) for i in range(1,10)] 
# ------>['"10月1日","10月2日"......."10月9日"]
```

format:字符串格式化的一种方式

使用："百度{}网盘".format("1")

"百度{}网盘".format([1,2,3,4])

"百度{}网盘{}".format({1,2,3,4},[1,2,3,4])

"百度{}网盘{}".format({1,2,3,4},1)

2. 字典推导式

- 帮助我们快速生成包含一堆数据的字典

```python
{i+10:i  for i in range(10)}
#{10:0,11:1,.....19:9}
{"a{}".format(i):10 for i in range(2)}
#{"a0":10,"a1":10,"a2":10}
```

3. 三元运算符

- if 后面的条件成立，就把if前面的结果赋值给a,否则把else后面的结果赋值给a

```python
a = 10 if 4>3 else 20 	#a = 10
a = 10 if 4<3 else 20   #a = 20
```



###### 写爬虫的讨论

1. url（知道url地址的规律和总得页码数）:构造url地址地列表

	start_url

2. 发送请求，获取响应

	requests

3. 提取数据

	返回json字符串:json模块

	返回的是html字符串：lxml模块配合xpath提取数据

4. 保存



###### Python中self用法

https://blog.csdn.net/CLHugh/article/details/75000104

self.xx是类里面的全局变量.

如果你知道java或者javascript中的this，那么self的作用和他们是一样的，不过我猜你可能也没接触过这两门语言。





#### Beautiful Soup(bs4)	是解析、遍历、维护标签树的功能库,对应一个HTML/XML文档的全部内容

###### 概念

- 解析HTML页面信息标记与提取方法
- 解析、遍历、维护标签树的功能库,对应一个HTML/XML文档的全部内容

###### 安装

```cmd
pip install beautifulsoup4
```

###### 使用

```python
# 引用方式：
from bs4 import BeautifulSoup||import bs4
soup = BeautifulSoup("<html>data</html>",'html.parser')
soup = BeautifulSoup(open("D://demo.html"),'html.parser')
soup.prettify()
```

###### 基本元素

###### 遍历方法

**上行遍历**

- .parent 父亲标签
- .parents  迭代类型 先辈

**下行遍历**

**平行遍历**

- .next_sibling 文本顺序的平行节点的下一个节点
- .previous.sibling 文本顺序的平行节点的上一个节点
- .next_siblings 迭代类型，文本顺序的平行节点的遍历后续节点
- .previous.siblings 迭代类型，文本顺序的平行节点的遍历前续节点

**扩展方法**

**简便写法**

**信息的标记**

**信息的提取**

###### 解析器

- 安装

	```cmd
	pip install lxml
	pip install html5lib
	```

- 分类

	**bs4的HTML解析器**

	BeautifulSoup(mk,'html.parser')

	**lxml的HTML解析器**

	BeautifulSoup(mk,'lxml') 

	**lxml的XML解析器**

	BeautifulSoup(mk,,'xml')

	**html5lib的HTML解析器** 

	BeautifulSoup(mk,'html5lib')

#### robots.txt(网络爬虫排除标准)

###### 	robots.txt

- 网络爬虫排除标准

###### 	来源审查

- 判断User-Agent进行限制
- 检查来访HTTP协议头的User-Agent域，响应浏览器或友好爬虫的访问

###### 分布公告

- Robots协议
	Rebot Exclusion Standard
	网络爬虫排除标准
- robots.txt文件
	告知所有爬虫网站的爬取策略

### Scrapy（中级）

 





## 实例

```python
import requests
r = requests.get("https://www.baidu.com/")
print(r.status_code)     #获取网页状态码
print(r.url)             #获取网址
print(r.text)            #获取网页源代码
```

IDE安装

爬取源代码

```python
import requests

url = "http://www.baidu.com"
respones = requests.get(url)
print(respones.content.encode())
```

爬取指定文字

```python
# coding=utf-8

import urllib2
import urllib
import re
import thread
import time
from bs4 import BeautifulSoup

url="http://toutiao.sogou.com/?fr=qqxwtt"
page = urllib.urlopen(url)#打开网址
html = page.read()        #读取网页内容，保存到htlm中
bs0bj=BeautifulSoup(html) #创建一个beautifulsoup的类
namelist=bs0bj.findAll("a")#通过标签筛选文字信息

for name in namelist:
    print (name.get_text())
```

爬取单张图片

```python
# 爬取图片
import requests
import os
root = "D:/Downloads/"
url = "http://b-ssl.duitang.com/uploads/item/201305/26/20130526140022_5fMJe.jpeg"
path = root +url.split('/')[-1]
try:
    if not os.path.exists(root):
        os.mkdir(root)
    if not os.path.exists(path):
        r = requests.get(url)
        with open(path,'wb') as f:
            f.write(r.content)
            f.close()
            print("成功")
    else:
        print("已保存")
except:
    print("失败")
```

爬取多张图片



爬取一个视频



爬取多个视频





百度翻译

[百度翻译API注册入口]:http://api.fanyi.baidu.com/

（python3）

```python
# coding: utf8
'''
    @Author: LCY
    @Contact: lchuanyong@126.com
    @blog: http://http://blog.csdn.net/lcyong_
    @Date: 2018-01-15
    @Time: 19:19
    说明： appid和secretKey为百度翻译文档中自带的，需要切换为自己的
           python2和python3部分库名称更改对应如下：
           httplib      ---->    http.client
           md5          ---->    hashlib.md5
           urllib.quote ---->    urllib.parse.quote
    官方链接：
           http://api.fanyi.baidu.com/api/trans/product/index
           
'''
 
import http.client
import hashlib
import json
import urllib
import random
 
def baidu_translate(content):
    #appid api id 密钥 我的翻译地址myurl
    appid = '20151113000005349'
    secretKey = 'osubCEzlGjzvw8qdQc41'
    httpClient = None
    myurl = '/api/trans/vip/translate'
    
    q = content
    fromLang = 'zh' # 源语言
    toLang = 'en'   # 翻译后的语言
    salt = random.randint(32768, 65536)
    sign = appid + q + str(salt) + secretKey
    sign = hashlib.md5(sign.encode()).hexdigest()
    myurl = myurl + '?appid=' + appid + '&q=' + urllib.parse.quote(
        q) + '&from=' + fromLang + '&to=' + toLang + '&salt=' + str(
        salt) + '&sign=' + sign
 
    try:
        httpClient = http.client.HTTPConnection('api.fanyi.baidu.com')
        httpClient.request('GET', myurl)
        # response是HTTPResponse对象
        response = httpClient.getresponse()
        jsonResponse = response.read().decode("utf-8")# 获得返回的结果，结果为json格式
        js = json.loads(jsonResponse)  # 将json格式的结果转换字典结构
        dst = str(js["trans_result"][0]["dst"])  # 取得翻译后的文本结果
        print(dst) # 打印结果
    except Exception as e:
        print(e)
    finally:
        if httpClient:
            httpClient.close()
 
if __name__ == '__main__':
    while True:  #死循环
        print("请输入要翻译的内容,如果退出输入q")
        content = input()
        if (content == 'q'):
            break  #q退出
        baidu_translate(content)
```

官方（python2）

```python
#/usr/bin/env python
#coding=utf8
 
import httplib
import md5
import urllib
import random
 
appid = '20151113000005349'
secretKey = 'osubCEzlGjzvw8qdQc41'
 
 
httpClient = None
myurl = '/api/trans/vip/translate'
q = 'apple'
fromLang = 'en'
toLang = 'zh'
salt = random.randint(32768, 65536)
 
sign = appid+q+str(salt)+secretKey
m1 = md5.new()
m1.update(sign)
sign = m1.hexdigest()
myurl = myurl+'?appid='+appid+'&q='+urllib.quote(q)+'&from='+fromLang+'&to='+toLang+'&salt='+str(salt)+'&sign='+sign
 
try:
    httpClient = httplib.HTTPConnection('api.fanyi.baidu.com')
    httpClient.request('GET', myurl)
 
    #response是HTTPResponse对象
    response = httpClient.getresponse()
    print response.read()
except Exception, e:
    print e
finally:
    if httpClient:
        httpClient.close()
```

```python
import requests
from lxml import etree
import json

class BiliBiliSpider:
    def __init__(self):
        self.url_temp ="https://www.bilibili.com/v/dance/otaku/#/all/default/0/{}/"
        self.headers = {
            "User-Agent":
                "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko)     Chrome/80.0.3987.106 Safari/537.36"
        }

    # 1.根据url地址的规律，构造url list
    def get_url_list(self):
        url_list = [self.url_temp.format(i) for i in range(1,10)]
        return url_list

    # 2.发送请求，获取响应
    def parse_url(self,url):
        response = requests.get(url,headers=self.headers)
        return  response.content.decode()

    # 3.提取数据
    def get_content_list(self,html_str):
        html = etree.HTML(html_str)
        #1.分组
        div_list = html.xpath("//*[@class=vd-list-cnt]")
        print(div_list)
        content_list = []
        for div in div_list:
            item = []
            # //*[@id="videolist_box"]/div[2]
            item[""] = div.xpath(".//ul/li[1]/div/div[2]/a[@title]")
            content_list.append(item)
        print(content_list)
        return  content_list

    # 4.保存
    def save_content_list(self,content_list):
        with open("bilibili.txt","w",encoding="UTF-8") as f:
            for content in content_list:
                f.write(json.dumps(content,ensure_ascii=False))
                f.write("\n")

        print("保存成功")

    def run(self):#实现主要逻辑
        #1.根据url地址的规律，构造url list
        url_list = self.get_url_list()
        #2.发送请求，获取响应
        for url in url_list:

            html_str = self.parse_url(url)
        # 3.提取数据
            content_list = self.get_content_list(html_str)
        #4.保存
            print(url)
            self.save_content_list(content_list)

# 主函数
if __name__ == '__main__':
   bilibili = BiliBiliSpider()
   bilibili.run()
```

https://zhuanlan.zhihu.com/p/73742321





```
import threading
import time
import requests
from bs4 import BeautifulSoup
import os
import random

url = "http://www.mzitu.com/all"
''' 获取html页面'''

def downHtml(url):
    headers = {
        'User-Agent': "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/42.0.2311.135 Safari/537.36 Edge/12.10240",
        'Connection': 'Keep-Alive',
        'Referer': "http://www.mzitu.com/99566"
    }
    return requests.get(url, headers=headers).text

''' 解析获取所有的妹子url  '''

def parseHtml(html):
    soup = BeautifulSoup(html, "lxml")
    list = soup.select("a[target='_blank']")
    mylist = [];
    count = 0  # 添加一个统计链接的数量
    for a in list:
        # print(a["href"], a.get_text())
        # print(a["href"])
        mylist.append(a["href"])
    return mylist
    # print(count)
    #     print(mylist)
    # print(len(mylist))


''' 获取妹子所有图片的数量 '''

def get_pic_num(html):
    soup = BeautifulSoup(html, "lxml")
    list = soup.find("div", class_="pagenavi").find_all("span")
    # print(list)
    # list [<span>«上一组</span>, <span>1</span>, <span>2</span>, <span>3</span>, <span>4</span>, <span class="dots">…</span>, <span>65</span>, <span>下一页»</span>]
    return int(list[-2].string)  # ？

''' 获取妹子的图片 '''


# 获取所有妹子的url
def get_pic(html):
    soup = BeautifulSoup(html, "lxml")
    img = soup.find("div", class_="main-image").find_all("img")
    print(img[0]["src"], img[0]["alt"])
    download_pic(img[0]["src"], img[0]["alt"])
    
''' 下载妹子的图片 '''
def download_pic(url, himg):
    headers = {
        'User-Agent': "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/42.0.2311.135 Safari/537.36 Edge/12.10240",
        'Connection': 'Keep-Alive',
        'Referer': "http://www.mzitu.com/99566"
    }
    img = requests.get(url, headers=headers)

    t = time.time()
    nowTime = lambda: int(round(t * 1000))

    # soup = BeautifulSoup(html, "lxml")
    # img = soup.find("div", class_="main-image").find_all("img")
    # pname = img[0]["src"]
    print(himg)
    folder = os.path.exists("H:\mztu\\" + himg)
    if not folder:  # 判断是否存在文件夹如果不存在则创建为文件夹
        os.makedirs("H:\mztu\\" + himg)
    with open("H:\mztu\{}\{}.jpg".format(himg, nowTime()), 'ab') as f:
        f.write(img.content)

# 创建文件夹
html = downHtml(url)
list = parseHtml(html)
# print(list)

for url in list:
    # print(src)
    # 获取妹子所有的图片
    html = downHtml(url)
    num = get_pic_num(html)
    print(num)
    for i in range(num):
        str = "{}{}{}".format(url, "/", i + 1)
        html = downHtml(str)
        t = threading.Thread(target=get_pic, args=(html,))
        t.start()
        t.join()
```

