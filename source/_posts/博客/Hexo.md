---
title: Hexo静态博客搭建 
categories:
- 博客
tags:
- Hexo
abbrlink: 2439
---
# Hexo博客基础知识

> [配置文件 | Hexo](https://hexo.io/zh-cn/docs/configuration)

hexo概念

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](https://link.zhihu.com/?target=http%3A//daringfireball.net/projects/markdown/)（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

hexo目录结构

```bash
├── _config.yml 博客配置文件
├── public：存放的是生成的页面
├── scripts：脚本文件 
├── package.json // 应用程序的信息 下面有修改，从而运行脚本命令 项目所需模块项目的配置信息
├── scaffolds  //模版 文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件。命令生成文章等的模板
├── db.json：source解析所得到的
├── source //资源文件夹是存放用户资源的地方。
|   ├── _drafts //文件夹中的草稿文章
|   └── _posts // 博客的md文件存放的地方
└── themes  // 主题文件
```

基本配置

要安装好 `git` 和`node.js`的环境

安装Hexo

```bash
npm install -g hexo-cli
```

进阶安装和使用

对于熟悉 npm 的进阶用户，可以仅局部安装 `hexo` 包

```bash
npm install -g hexo
```

添加到环境变量 如果不添加则要，在hexo目录下运行cmd命令

```bash
将 Hexo 所在的目录下的 node_modules 添加到环境变量之中即可直接使用 hexo <command>：
echo 'PATH="$PATH:./node_modules/.bin"' >> ~/.profile
HEXO_HOME : hexo 文件的目录
path 添加 %HEXO_HOME%
```

新建项目

```bash
hexo init blog // blog 是项目名称
cd blog // 进入blog的文件夹
```

生成静态文件

```bash
hexo g //generate
```

启动本地服务器

```bash
hexo s //server
```

| 选项          | 描述                           |
| ------------- | ------------------------------ |
| -p,- - port   | 重设端口                       |
| -s， --static | 只使用静态文件                 |
| -l，- - log   | 记录日记记录，使用覆盖记录格式 |

发表文章

```bash
hexo new "文章名称" // 注意文件的名称不用带.md 后缀名
hexo new "这是一篇文章的name"
hexo clean
hexo g // 重新生成静态网页
hexo s // 启动本地服务器
```

| 参数           | 表述                                          |
| -------------- | --------------------------------------------- |
| -p,- - path    | 自定义新文章的路径                            |
| -r,- - replace | 如果存在同名文章，将其替换                    |
| -s, - - slug   | 文章的 Slug，作为新文章的文件名和发布后的 URL |

```bash
hexo new page --path about/me "About me" // 指定 source 文件夹下新建一个目录
```

清除缓存文件(db.json) 和已经生产的静态文件（public）

在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令。

```bash
hexo clean
```

列出网站资料

```bash
hexo list <type>
```

Hexo 版本

```bash
hexo version
```

Hexo Node script脚本

```bash
"local": "hexo clean & hexo generate & hexo server",
"cloud": "hexo clean & hexo generate & hexo server & hexo deploy"
```

草稿模式

发表草稿

```bash
hexo publish [layout] <filename>
```

显示草稿

```bash
hexo --draft 
```

显示 `source/_drafts` 文件夹中的草稿文章。

配置文件 `_config.yml`

> .yml配置文件
>
> 每个参数的：后都要加一个空格

# Hexo主题以及配置文件

SITE设置

- `title:` 填写标题 `subtitle:` 填写副标题 `description:` 简介 `keywords:` 关键词 `author:` 作者，文章中显示的作者名称 `language:` 设置语言，`zh-CN`是简体中文，`en`是英语



## hexo-theme-next 版本5.3

[hexo-theme-next/README.md at master · theme-next/hexo-theme-next](https://github.com/theme-next/hexo-theme-next/blob/master/docs/zh-CN/README.md)

[Hexo-NexT主题添加评论功能（来必力、Hypercomments、畅言、友言）_请别抢我的狗熊-CSDN博客_hexo安装来必力评论插件next主题](https://blog.csdn.net/qq_32454537/article/details/79482879)

next 版本 v 7.8

# Hexo编辑md文件

使用typora打开md文件;

解决github图片不能加载的问题

DNS 污染

复制 `raw.githubusercontent.com` 去 [https://www.ipaddress.com](https://www.ipaddress.com/) 搜索,把给出的IP地址存储到 **host** 文件中: 如 `199.232.28.133 raw.githubusercontent.com`

host :

C:\Windows\System32\drivers\etc

问题

最新版本

[(29条消息)next7.6版本关于设置阅读全文_CHENGXUYUAN09的博客-CSDN博客_next7.6](https://blog.csdn.net/CHENGXUYUAN09/article/details/103408380)

[Hexo使用攻略-添加分类及标签 - 简书](https://www.jianshu.com/p/e17711e44e00)

[给Hexo Next设置阅读全文 - 简书](https://www.jianshu.com/p/d335569a6238)he

代码复制按钮

[hexo-next 添加代码块复制功能 | YouForever](https://www.zhyong.cn/posts/ca02/)

- 本地搜索(需要npm安装denpendency)

```yml
# Local search
# Dependencies: https://github.com/theme-next/hexo-generator-searchdb
local_search:
  enable: true
  # if auto, trigger search by changing input
  # if manual, trigger search by pressing enter key or search button
  trigger: auto
  # show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # unescape html strings to the readable one
  unescape: false
```

https://www.jianshu.com/p/6e150379093b

## 修改标签图标

修改模板 `/themes/next/layout/_macro/post.swig`，搜索 `rel="tag">#`，将 # 换成 `<i class="fa fa-tag"></i>`

## 点击出现桃心效果

在 `/themes/next/source/js/src` 下新建 `love.js`, 写入以下内容

```
!function(e,t,a){function n(){c(".heart{width: 10px;height: 10px;position: fixed;background: #f00;transform: rotate(45deg);-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);}.heart:after,.heart:before{content: '';width: inherit;height: inherit;background: inherit;border-radius: 50%;-webkit-border-radius: 50%;-moz-border-radius: 50%;position: fixed;}.heart:after{top: -5px;}.heart:before{left: -5px;}"),o(),r()}function r(){for(var e=0;e<d.length;e++)d[e].alpha<=0?(t.body.removeChild(d[e].el),d.splice(e,1)):(d[e].y--,d[e].scale+=.004,d[e].alpha-=.013,d[e].el.style.cssText="left:"+d[e].x+"px;top:"+d[e].y+"px;opacity:"+d[e].alpha+";transform:scale("+d[e].scale+","+d[e].scale+") rotate(45deg);background:"+d[e].color+";z-index:99999");requestAnimationFrame(r)}function o(){var t="function"==typeof e.onclick&&e.onclick;e.onclick=function(e){t&&t(),i(e)}}function i(e){var a=t.createElement("div");a.className="heart",d.push({el:a,x:e.clientX-5,y:e.clientY-5,scale:1,alpha:1,color:s()}),t.body.appendChild(a)}function c(e){var a=t.createElement("style");a.type="text/css";try{a.appendChild(t.createTextNode(e))}catch(t){a.styleSheet.cssText=e}t.getElementsByTagName("head")[0].appendChild(a)}function s(){return"rgb("+~~(255*Math.random())+","+~~(255*Math.random())+","+~~(255*Math.random())+")"}var d=[];e.requestAnimationFrame=function(){return e.requestAnimationFrame||e.webkitRequestAnimationFrame||e.mozRequestAnimationFrame||e.oRequestAnimationFrame||e.msRequestAnimationFrame||function(e){setTimeout(e,1e3/60)}}(),n()}(window,document);
```

复制

打开 `\themes\next\layout\_layout.swig` 文件，在末尾添加：
`<script type="text/javascript" src="/js/src/love.js"></script>`

音乐插件

添加 文件末尾链接

[(29条消息)Hexo持续优化-在文章尾部添加版权声明_王西文的博客-CSDN博客_next版权声明](https://blog.csdn.net/wangxw725/article/details/100148601)

```
# Declare license on posts
post_copyright:
  enable: false
  license: CC BY-NC-SA 3.0
  license_url: https://creativecommons.org/licenses/by-nc-sa/3.0/
```

[(29条消息)Hexo添加小部件(Butterfly主题) 添加卡通人物（看板娘）_超逸の学习技术博客-CSDN博客_matery博客主题添加卡通人物](https://blog.csdn.net/weixin_42429718/article/details/105626385)

# Hexo中创建YAML模板文件问题

目录`.\scaffolds文件下`

```
title: {{ title }}
date: {{ date }}
categories:
- 分类
tags:
- 标签1
- 标签2
```

经常要写同一类型的文章，懒得每篇文章都添加同样的`tags`和`categories`，因此可使用`scaffolds`创建模板，每次只需要`hexo new layout "标题"`即可生成相同样式的文章。
 但近期使用时发现一些问题，如下图所示，我创建了一个名为`Hexo`的模板，并正确放到`scaffolds`中：

> 在scaffolds中创建模板时，模板标题`不能为大写`，中文也可以，但就是不能大写。

# HexoNew时使用Markdown编辑器

方法一：

Tommy 指出，可以在 Hexo 目录下的 `scripts` 目录（若没有，则新建一个blog/scripts）中创建一个 JavaScript （openNewFile）脚本，监听 `hexo new` 这个动作。并在检测到 `hexo new` 之后，执行编辑器打开的命令。

openNewFile.js中的代码

```js
var spawn = require('child_process').spawn;
hexo.on('new', function(data){
    spawn('C:/Program Files/Typora/Typora.exe ', [data.path]);
});
//C:/Program Files/Typora/Typora.exe  自已 Typora 的目录
```

[在 hexo new 新建文件之后立即打开新建的 Markdown 文稿_天心天地生的博客-CSDN博客_hexo新建文件](https://blog.csdn.net/tianxintiandisheng/article/details/102381391)

方法二：

安装`shell.js模块`，实现自动部署加载JS脚本

```
npm install --save shelljs
```

可以在 Hexo 目录下的 `scripts` 目录（若没有，则新建一个blog/scripts）中创建一个 JavaScript （openNewFile）脚本，监听 `hexo new` 这个动作。并在检测到 `hexo new` 之后，执行编辑器打开的命令。

```js
var exec = require('child_process').exec;
 
hexo.on('new', function(data){
    exec('open -a "/Applications/Typora.app"  ' + [data.path]);
    // open 或者 start  /Applications/Typora.app 目录位置
});
```

# Hexo热更新



# Hexo部署到远程仓库

blog部署

### 部署到github

[将 Hexo 部署到 GitHub Pages | Hexo](https://hexo.io/zh-cn/docs/github-pages)

[部署 | Hexo](https://hexo.io/zh-cn/docs/one-command-deployment)

- 创建GItHub项目 
- 安装插件

```bash
npm install --save hexo-deployer-git
```

- 修改 vim ——config.yml

```bash
#Deployment
deploy
	type: git
	repo: #.git地址  https://github.com/LonelyDreamCatcher/heweiliang.git
	branch:master
```

- 部署

```bash
hexo d
```

- 输入账号和密码

```bash
要等待1omin
解决方法
设置Gitee page|| Giteehub page  
服务  
```

### 部署到gitee上

### 部署优化

每次都要执行 hexo clean 和 hexo deploy

```json
package.json
"dev":"hexo s",
"build":"hexo clean & hexo deploy"
```

部署命令

```bash
npm run build
```

Github action 自动部署到远程仓库

# Hexo添加评论

- Hypercomments评论

- Mastery
- 畅言

- 友言

- 来必力


1. 在[来必力](https://livere.com/)的官网上注册账号。
2. 在[此处](https://livere.com/insight/myCode)获取data-uid。
3. 打开NexT主题的配置文件`—config`中，搜索livere_uid，将livere_uid前面的#号去掉，将id填写到livere_uid：后面。ivere_uidivere_uid
4. [hexo博客优化之实现来必力评论功能 - 简书](https://www.jianshu.com/p/61abc6c43220)
5. [Hexo-NexT主题添加评论功能（来必力、Hypercomments、畅言、友言）_请别抢我的狗熊-CSDN博客_hexo安装来必力评论插件next主题](https://blog.csdn.net/qq_32454537/article/details/79482879)

[theme-next/theme-next-calendar: 一个简洁的hexo-next日历云插件](https://github.com/theme-next/theme-next-calendar)

# Hexo标题名带目录

- 给每篇文章添加YAML的Title标题声明

# 安装动态背景

Next主题默认提供了三种动态背景

- [Canvas-nest](https://link.zhihu.com/?target=https%3A//github.com/theme-next/theme-next-canvas-nest)
- [JavaScript 3D library](https://link.zhihu.com/?target=https%3A//github.com/theme-next/theme-next-three)
- [Canvas-ribbon](https://link.zhihu.com/?target=https%3A//github.com/theme-next/theme-next-canvas-ribbon)

### Canvas-nest

这是在网页背景显示的动态效果。

### 安装

切换到Next主题文件夹

```text
cd themes/next
```

安装模块

```text
git clone https://github.com/theme-next/theme-next-canvas-nest source/lib/canvas-nest
```

### 修改配置文件

打开Next主题路径下的配置文件`_config.yml`修改下列代码

```js
# Canvas-nest
# Dependencies: https://github.com/theme-next/theme-next-canvas-nest
canvas_nest:
  enable: true
  onmobile: true # 是否在手机上显示
  color: "255,51,51" # RGB颜色设置
  opacity: 0.5 # 线条透明度
  zIndex: -1 # 显示级别
  count: 160 # 线条的数量，越多越卡
```

如果想使用CDN加速的话需要设置

```js
vendors:
  ...
  canvas_nest: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1.0.0/canvas-nest.min.js
  canvas_nest_nomobile: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1.0
```

Hexo博客出现“Cannot GET/xxx”错误

```
npm i
npm install hexo-generator-index
```

hexo d命令报错：ERROR Deployer not found: git

```bash
npm install --save hexo-deployer-git
npm i

deploy
  type: git
  repository: git@github.com:YOUR_ID/YOUR_ID.github.io.git
  branch: master
```

[利用 Github Actions 自动部署 Hexo 博客 | Sanonz](https://sanonz.github.io/2020/deploy-a-hexo-blog-from-github-actions/)

##  持续集成 CI

将清除缓存 `hexo clean` ，生成静态文件 `hexo generate` 和部署到 GitHub Pages `hexo deploy` 这些步骤通过持续集成工具来帮助我们自动执行。

asdfasdfasfwerwerw

12312312123123

asdfasdf

asdfasdfasd1234234

2asdfasadfasd1342342

afdsfsd
