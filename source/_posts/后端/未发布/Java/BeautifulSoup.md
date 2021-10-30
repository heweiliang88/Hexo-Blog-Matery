---
abbrlink: 52977
---
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

