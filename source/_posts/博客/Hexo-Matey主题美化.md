---
title: Hexo静态博客搭建
categories:
  - 博客
tags:
  - Matery
abbrlink: 49390
---

# Hexo-Matry主题美化

```markdown
{% meting "002j785c33YQHT" "tencent" "song" %}
```

> - [ ] [Hexo-Matery主题细致美化(上) | Marmalade's Blog](https://marmalade.vip/Materysettings1.html)
> - [ ] [Hexo-Matery主题细致美化(下) | Marmalade's Blog](https://marmalade.vip/Materysettings2.html)
> - [ ] [Github+Hexo+matery博客搭建【附源码】_果果小师弟_51CTO博客](https://blog.51cto.com/u_14114084/3666309)
> - [ ] [hexo-helper-live2d | Easy Hexo 👨‍💻](https://easyhexo.com/3-Plugins-use-and-config/3-3-hexo-helper-live2d/#%E6%9B%B4%E5%A4%9A%E6%A8%A1%E5%9E%8B)
> - [ ] [让你的 Hexo 博客支持远程编辑 | Easy Hexo 👨‍💻](https://easyhexo.com/4-High-order-hexo-gamer/4-1-remote-editing/#%E4%BC%98%E7%BC%BA%E7%82%B9)
> - [ ] [Hexo进阶：基于matery主题的网站配置教程 | 零下三度极寒](https://m3df.xyz/2020/06/13/e9fff968/)

## 安装主题

```bash
git clone https://github.com/blinkfox/hexo-theme-matery.git
```

```bash
theme: mastery
```

## 安装模块

```bash
npm install hexo-filter-github-emojis --save // emoji
npm i -S hexo-prism-plugin //代码光亮
npm install hexo-generator-search --save // 主题搜索 
npm i --save hexo-wordcount  // 字数统计
npm install hexo-generator-feed --save  // rss订阅
```

## 新建页面

```bash
// 批量操作
// /source/页面名/index.md
hexo new page "tags"
hexo new page "categories"
hexo new page "about"
hexo new page "contact"
hexo new page "friends"
```

### 标签页

```bash
hexo new page "tags"
// /source/tags/index.md
---
title: tags
date: 
type: "tags"
layout: "tags"
---
```

### 分类页

```bash
hexo new page "categories"
// /source/categories/index.md
---
title: categories
date: 
type: "categories"
layout: "categories"
---
```

### 关于页面

```bash
hexo new page "about"
// /source/about/index.md
---
title: about
date: 
type: "about"
layout: "about"
---
```

### 留言板

```bash
hexo new page "contact"
---
title: contact
date: 
type: "contact"
layout: "contact"
---
```

### 友情链接

```bash
hexo new page "friends"
---
title: friends
date: 2020-02-23 19:37:07
type: "friends"
layout: "friends"
---
```

```bash
/source/_data/friends.json

```

### 添加404页面

```
/source/404.md
---
title: 404
date: 2020-02-23 19:37:07
type: "404"
layout: "404"
description: "Oops～，我崩溃了！找不到你想要的页面了"
---
```

```bash
/layout/404.ejs
<style type="text/css">
    /* don't remove. */
    .about-cover {
        height: 90.2vh;
    }
</style>
<div class="bg-cover pd-header about-cover">
    <div class="container">
        <div class="row">
            <div class="col s10 offset-s1 m8 offset-m2 l8 offset-l2">
                <div class="brand">
                    <div class="title center-align"> 404 </div>
                    <div class="description center-align">
                        <%= page.description %>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
<script> // 每天切换 banner 图. Switch banner image every day. $('.bg-cover').css('background-image', 'url(/medias/banner/' + new Date().getDay() + '.jpg)'); </script>
```

### 添加自定义页面

```html
/source/aboutme/index.html 
About: url: / icon: fas fa-address-card children: - name: 关于我 url: /about icon: fas fa-user-circle - name: Another #这是新添加的，在原有配置基础上添加 url: /aboutme icon: fa fa-user-secret
```

```bash
# 其意思为在对文件进行渲染时跳过aboutme文件下的所有文件
skip_render: 
    - aboutme/** 
    - aaa/**
    - bbb/**
```

## 菜单导航

配置基本菜单导航的名称、路径 url 和图标 icon.

图标 icon 可以在 [Font Awesome](https://fontawesome.com/icons) 中查找

```
# main menu navigation url and icon # 配置菜单导航的名称、路径和图标icon. menu: Index: url: / icon: fas fa-home Tags: url: /tags icon: fas fa-tags Categories: url: /categories icon: fas fa-bookmark Archives: url: /archives icon: fas fa-archive About: url: /about icon: fas fa-user-circle Contact: url: /contact icon: fas fa-comments Friends: url: /friends icon: fas fa-address-book
```

二级菜单

```
menu: Index: url: / icon: fas fa-home Tags: url: /tags icon: fas fa-tags Categories: url: /categories icon: fas fa-bookmark Archives: url: /archives icon: fas fa-archive About: url: /about icon: fas fa-user-circle-o Friends: url: /friends icon: fas fa-address-book Medias: icon: fas fa-list children: - name: Musics url: /musics icon: fas fa-music - name: Movies url: /movies icon: fas fa-film - name: Books url: /books icon: fas fa-book - name: Galleries url: /galleries icon: fas fa-image
```

## 添加emoji表情

```bash
npm install hexo-filter-github-emojis --save
```

k Hexo 根目录下的 _config.yml 文件中，新增以下的配置项

```bash
githubEmojis:
  enable: true
  className: github-emoji
  inject: true
  styles:
  customEmojis:
```

在网站https://www.webfx.com/tools/emoji-cheat-sheet/可以搜索常用表情对应代码

在 [emoji-cheat-sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet/) 中找到你想要的表情，然后点击即可复制。使用方法和 [GitHub](https://github.com/) 一样，比如你想发一个笑脸 😄 直接输入笑脸对应的 emoji 编码 `:smile：` 就可以。

## 代码高亮

```bash
npm i -S hexo-prism-plugin

// 修改 Hexo 根目录下 _config.yml 文件中 highlight.enable 的值为 false，并新增 prism 插件相关的配置，主要配置如下：
highlight: 
#代码块的设置 enable: false 
#开启代码块高亮 line_number: true 
#如果未指定语言，则启用自动检测 auto_detect: false #显示行数 tab_replace: '' 
#用n个空格替换tabs；如果值为空，则不会替换tabs wrap: true hljs: false # 关闭原有的代码高亮，使用自己的 prism_plugin: mode: 'preprocess' # realtime/preprocess theme: 'tomorrow' line_number: false # default false custom_css:
```

## 主题的搜索功能

```
npm install hexo-generator-search --save
```

```yaml
search:
  path: search.xml
  field: post
```

## 文章字数统计插件

```
npm i --save hexo-wordcount

wordCount:
  enable: false # 将这个值设置为 true 即可.
  postWordCount: true
  min2read: true
  totalCount: true
```

## 添加RSS订阅支持

```
npm install hexo-generator-feed --save

feed: type: atom 
path: atom.xml 
limit: 20 
hub: 
content: content_limit: 140 
content_limit_delim: ' ' 
order_by: -date
```

## 修改页脚

```
 /layout/_partial/footer.ejs
```

## 修改社交链接

在主题的 config.yml 文件中，默认支持 QQ、GitHub 和邮箱等的配置，你可以在主题文件的 /layout/_partial/social-link.ejs 文件中，新增、修改你需要的社交链接地址，增加链接可参考如下

```
<% if (theme.socialLink.github) { %> <a href="<%= theme.socialLink.github %>" class="tooltipped" target="_blank" data-tooltip="访问我的GitHub" data-position="top" data-delay="50"> <i class="fab fa-github"></i> </a> <% } %>
```

## 修改打赏二维码图片

```
source/medias/reward
```

## 配置音乐播放器

 _config.yml 配置文件中激活 music 

```
music:
  enable: true
  showTitle: true
  title: 听听音乐
  fixed: false # 开启吸底模式
  autoplay: false # 是否自动播放
  theme: '#42b983'
  loop: 'all' # 音频循环播放, 可选值: 'all', 'one', 'none'
  order: 'list' # 音频循环顺序, 可选值: 'list', 'random'
  preload: 'auto' # 预加载，可选值: 'none', 'metadata', 'auto'
  volume: 0.7 # 默认音量，请注意播放器会记忆用户设置，用户手动设置音量后默认音量即失效
  listFolded: false # 列表默认折叠
  listMaxHeight: #列表最大高度
```

server 可选 netease（网易云音乐），tencent（QQ 音乐），kugou（酷狗音乐），xiami（虾米音乐），

baidu（百度音乐）。

type 可选 song（歌曲），playlist（歌单），album（专辑），search（搜索关键字），artist（歌手）

id 获取示例：浏览器打开网易云音乐，点击我喜欢的音乐歌单，地址栏有一串数字，playlist 的 id 即为这串数字。

## 全局音乐播放器



## 修改网站背景图

## 定制修改

#### 修改主题颜色

- 顶部导航栏颜色,底部状态栏颜色

在主题文件的 /source/css/matery.css 文件中修改

```css
// 搜索 .bg-color
/* 整体背景颜色，包括导航、移动端的导航、页尾、标签页等的背景颜色. */
.bg-color {
    background-image: linear-gradient(to right, #2558FF 0%, #0f9d58 100%);
}
/*如果想去掉banner图的颜色渐变效果，请将以下的css属性注释掉或者删除掉即可*/
@-webkit-keyframes rainbow {
   /* 动态切换背景颜色. */
}
@keyframes rainbow {
    /* 动态切换背景颜色. */
}
```

## 修改 banner 图和文章特色图

在 /source/medias/banner 文件夹中更换你喜欢的 banner 图片，主题代码中是每天动态切换一张，只需 7 张即可。如果你会 JavaScript 代码，可以修改成你自己喜欢切换逻辑，如：随机切换等，banner 切换的代码位置在 /layout/_partial/bg-cover-content.ejs 文件的 代码中：

```html
$('.bg-cover').css('background-image', 'url(/medias/banner/' + new Date().getDay() + '.jpg)');
```

在 /source/medias/featureimages 文件夹中默认有 24 张特色图片，你可以再增加或者减少，并需要在 _config.yml 做同步修改。

如果想改为每小时或者每分钟切换 banner 图的话，需要将 getDay() 改为 getHours() 或者 getMinutes() 即可。

## 添加评论模块配置

## 修改网站相关信息

```yaml
#这是根目录下的配置文件信息
# Site
title: xxxxx        #网站标题
subtitle: 世界很暗，但是你来了 #网站副标题
description: 本网站是个人兴趣爱好，总结分享经验，记录生活点滴的平台，希望在以后的学习旅途中，走出自己的风景。    #网站描述description 主要用于5E0，告诉搜索引擎一个关于您站点的简单描述
keywords: [HTML, CSS, JavaScript, JQuery, java, linux等]        #网站的关键词。使用半角逗号“，”分隔多个关键词
author: xxx            #您的名字
language: zh-CN            #网站使用的语言。建议修改为zh-CN
timezone:            #网站时区。Hexo默认使用您电脑的时区。


# 这是主题配置文件的相关信息
# 配置网站favicon和网站LOGO
# 此处我用的CDN，也可以使用本地文件
favicon: https://cdn.jsdelivr.net/gh/guixinchn/image/blog/favicon.png
logo: https://cdn.jsdelivr.net/gh/guixinchn/image/blog/logo.png


# 网站副标题，打字效果
# 如果有符号 ‘ ，请在 ’ 前面加上 \
subtitle:
  enable: true
  loop: true # 是否循环
  showCursor: true # 是否显示光标
  startDelay: 300 # 开始延迟
  typeSpeed: 100 # 打字速度
  backSpeed: 50 # 删除速度
  sub1: 如果放弃太早，你永远都不知道自己会错过什么。
  sub2: 没有伞的孩子必须努力奔跑！
  sub3: 花开不是为了花落，而是为了开的更加灿烂。
  sub4: 没有礁石，就没有美丽的浪花；没有挫折，就没有壮丽的人生。
```

注意：

网站打字效果副标题默认有两个，即 sub1 和 sub2，如果想写多个，则需要修改两处地方，首先修改配置文件，如上面所示，在 sub1 和 sub2 后面继续添加即可，然后在去主题目录下的 layout 文件夹下的_partial 文件夹，修改 bg-cover-content.ejs 文件，大约在 12 行左右，如下面所示：

```html
<div class="description center-align">
                <% if (theme.subtitle.enable) { %>
                <span id="subtitle"></span>
                <script src="https://cdn.jsdelivr.net/npm/typed.js@2.0.11"></script>
                <script>
                    var typed = new Typed("#subtitle", {
                        strings: ['<%= theme.subtitle.sub1 %>',
                                   '<%= theme.subtitle.sub2 %>',
                                  '<%= theme.subtitle.sub3 %>',
                                   '<%= theme.subtitle.sub4 %>'],
                        startDelay: <%= theme.subtitle.startDelay %>,
                        typeSpeed: <%= theme.subtitle.typeSpeed %>,
                        loop: <%= theme.subtitle.loop %>,
                        backSpeed: <%= theme.subtitle.backSpeed %>,
                        showCursor: <%= theme.subtitle.showCursor %>
                    });
                </script>
                <% } else { %>
                    <%= config.description %>
                <% } %>
            </div>
```

**社交链接的修改**

在主题的配置文件中修改

```yaml
# 首页 banner 中的第二行个人信息配置，留空即不启用
socialLink:
  qq: 1563972718
  weixin: https://gitee.com/marmalade0/images/blob/master/www.marmalade.vip/wechat.jpg
  github: #https://github.com/marmalade0
  email: 1563972718@qq.com
  facebook: # https://www.facebook.com/xxx
  twitter: # https://twitter.com/xxx
  weibo: # https://weibo.com/xxx
  zhihu: # https://www.zhihu.com/xxx
  csdn: https://blog.csdn.net/kuashijidexibao
  cnblogs: https://www.cnblogs.com/kuashijidexibao
  rss: true # true、false
```

期中的 weixin 我是用的图片链接，会跳转到一个新的标签页，之后还需要修改 ejs 文件，文件在主题目录下的 layout 文件夹下的_partial 文件夹，修改 social-link.ejs，添加相关的配置，比如：

```html
<% if (theme.socialLink.github) { %>
    <a href="<%= theme.socialLink.github %>" class="tooltipped" target="_blank" data-tooltip="访问我的GitHub" data-position="top" data-delay="50">
        <i class="fab fa-github"></i>
    </a>
<% } %>

<% if (theme.socialLink.email) { %>
    <a href="mailto:<%= theme.socialLink.email %>" class="tooltipped" target="_blank" data-tooltip="邮件联系我" data-position="top" data-delay="50">
        <i class="fas fa-envelope-open"></i>
    </a>
<% } %>

<% if (theme.socialLink.facebook) { %>
    <a href="<%= theme.socialLink.facebook %>" class="tooltipped" target="_blank" data-tooltip="关注我的Facebook: <%= theme.socialLink.facebook %>" data-position="top" data-delay="50">
        <i class="fab fa-facebook-f"></i>
    </a>
<% } %>

<% if (theme.socialLink.twitter) { %>
    <a href="<%= theme.socialLink.twitter %>" class="tooltipped" target="_blank" data-tooltip="关注我的Twitter: <%= theme.socialLink.twitter %>" data-position="top" data-delay="50">
        <i class="fab fa-twitter"></i>
    </a>
<% } %>

<% if (theme.socialLink.qq) { %>
    <a href="tencent://AddContact/?fromId=50&fromSubId=1&subcmd=all&uin=<%= theme.socialLink.qq %>" class="tooltipped" target="_blank" data-tooltip="QQ联系我: <%= theme.socialLink.qq %>" data-position="top" data-delay="50">
        <i class="fab fa-qq"></i>
    </a>
<% } %>

<% if (theme.socialLink.weibo) { %>
    <a href="<%= theme.socialLink.weibo %>" class="tooltipped" target="_blank" data-tooltip="关注我的微博: <%= theme.socialLink.weibo %>" data-position="top" data-delay="50">
        <i class="fab fa-weibo"></i>
    </a>
<% } %>

<% if (theme.socialLink.zhihu) { %>
    <a href="<%= theme.socialLink.zhihu %>" class="tooltipped" target="_blank" data-tooltip="关注我的知乎: <%= theme.socialLink.zhihu %>" data-position="top" data-delay="50">
        <i class="fab fa-zhihu1">知</i>
    </a>
<% } %>

<% if (theme.socialLink.rss) { %>
    <a href="<%- url_for('/atom.xml') %>" class="tooltipped" target="_blank" data-tooltip="RSS 订阅" data-position="top" data-delay="50">
        <i class="fas fa-rss"></i>
    </a>
<% } %>



<% if (theme.socialLink.jianshu) { %>
    <a href="<%= theme.socialLink.jianshu %>" class="tooltipped" target="_blank" data-tooltip="关注我的简书: <%= theme.socialLink.jianshu %>" data-position="top" data-delay="50">
        <i class="fab fa-jianshu">简</i>
    </a>
<% } %>

<% if (theme.socialLink.csdn) { %>
    <a href="<%= theme.socialLink.csdn %>" class="tooltipped" target="_blank" data-tooltip="关注我的CSDN: <%= theme.socialLink.csdn %>" data-position="top" data-delay="50">
        <i class="fab fa-csdn">C</i>
    </a>
<% } %>
<% if (theme.socialLink.juejin) { %>
    <a href="<%= theme.socialLink.juejin %>" class="tooltipped" target="_blank" data-tooltip="关注我的掘金: <%= theme.socialLink.juejin %>" data-position="top" data-delay="50">
        <i class="fab fa-juejin">掘</i>
    </a>
<% } %>

<% if (theme.socialLink.cnblogs) { %>
    <a href="<%= theme.socialLink.cnblogs %>" class="tooltipped" target="_blank" data-tooltip="关注我的博客园: <%= theme.socialLink.cnblogs %>" data-position="top" data-delay="50">
        <i class="fab fa-juejin">博</i>
    </a>
<% } %>
<% if (theme.socialLink.weixin) { %>
    <a href="<%= theme.socialLink.weixin %>" class="tooltipped" target="_blank" data-tooltip="微信联系我: <%= theme.socialLink.weixin %>" data-position="top" data-delay="50">
        <i class="fab fa-weixin"></i>
    </a>
<% } %>
```

## 其他DIY

实现方法，引入 js 文件，在主题文件下的 /source/js/ 下新建 FunnyTitle.js，增加以下代码：

```js
 var OriginTitle = document.title;
 var titleTime;
 document.addEventListener('visibilitychange', function () {
     if (document.hidden) {
         $('[rel="icon"]').attr('href', "https://cdn.jsdelivr.net/gh/guixinchn/image/blog/favicon.png");
         document.title = '我相信你还会回来的！';
         clearTimeout(titleTime);
     }
     else {
         $('[rel="icon"]').attr('href', "https://cdn.jsdelivr.net/gh/guixinchn/image/blog/favicon.png");
         document.title = '哈哈，我就知道！' + OriginTitle;
         titleTime = setTimeout(function () {
             document.title = OriginTitle;
         }, 2000);
     }
 });
```

然后在添加到 themes/matery/layout/layout.ejs 引入

## 个人简历

开 theme/matery/layout/about.ejs 文件，大约在 13 行。有一个 `` 标签，找出其对应结尾的标签，大约在 61 行左右，然后在新增如下代码：

```html
<div class="card">
     <div class="card-content">
         <div class="card-content article-card-content">
             <div class="title center-align" data-aos="zoom-in-up">
                 <i class="fa fa-address-book"></i>&nbsp;&nbsp;<%- __('个人简历') %>
              </div>
                 <div id="articleContent" data-aos="fade-up">
                     <%- page.content %>
                 </div>
           </div>
      </div>
</div>
```

### 修改网站背景图

主题配置文件

```yaml
background:
  enable: true
  url: "https://gitee.com/marmalade0/images/blob/master/www.marmalade.vip/24.jpg"
```

## 看板娘模块安装和使用

```bash
cnpm install --save hexo-helper-live2d

cnpm install {packagename}
# 例如cnpm install live2d-widget-model-haru
```

```bash
blog/_config.yml
live2d: enable: true scriptFrom: local pluginRootPath: live2dw/ pluginJsPath: lib/ pluginModelPath: assets/ tagMode: false debug: false model: use: live2d-widget-model-z16 display: position: right width: 200 height: 400 mobile: show: false

live2d:
  enable: true
  pluginModelPath: assets/
  model:
    use: live2d-widget-model-epsilon2_1 #模板目录，在node_modules里
  display:
    position: left
    #  1:2
    width: 300
    height: 600
  mobile:
    show: true #是否在手机进行显示
```



## 添加博客天气模块





## 添加樱花飘落动效



## 关闭首页颜色变换



## 给卡片区添加背景



## 添加加载动画



## 添加博客导航页

```bash
hexo new page navigate
---
title: 导航
date: 2020-05-09 11:19:14
type: "navigate"
layout: "navigate"
---
```



## 添加ICP/公安备案号

```css
hexo/themes/matery/layout/_partial路径下的footer.ejs
<img src="https://gitee.com/marmalade0/images/blob/master/www.marmalade.vip/beian.png"> <a href="http://www.beian.miit.gov.cn/" style="color:#f72b07" target="_blank">你自己的备案号，如鲁公网安备xxxxxx号</a>
```



## 自定义字体

全局字体自定义

```css
/source/font 
// 将你要用到的字体放入上述创建的文件夹内，字体名称最好为英文，如 /source/font/myFont.ttf
找到主题文件夹下的 my.css 文件，路径为 /themes/matery/source/css/my.css ，填入下面的代码：

@font-face{
    font-family: 'myFont';
    src: url('../font/myFont.ttf');
}

body{
    font-family: 'myFont';
}
```

局部字体自定义

```
/themes/matery/source/css/my.css

@font-face{
    font-family: 'myFont';
    src: url('../font/myFont.ttf');
}

.diyFont{
    font-family: 'myFont';
}
```

找到你要自定义的区域，如我要自定义博客主页的标题字体，那么就要找到相应的文件，也就是 `/themes/matery/layout/_partial/bg-cover-content.ejs` ，在相应的地方加入我刚刚自定义的 `diyFont` 类。如将下面的：

```
找到你要自定义的区域，如我要自定义博客主页的标题字体，那么就要找到相应的文件，也就是 /themes/matery/layout/_partial/bg-cover-content.ejs ，在相应的地方加入我刚刚自定义的 diyFont 类。如将下面的：
```

Hexo Matery代码块bug

```

```

Error: `prism_plugin` options should be added to _config.yml file

```
# 代码光亮
highlight:
  enable: false
  line_number: true
  auto_detect: false
  tab_replace: ""
  wrap: true
  hljs: false

prism_plugin:
  mode: 'preprocess'    # realtime/preprocess
  theme: 'tomorrow'
  line_number: false    # default false
  custom_css: 
```

Deprecated config detected: "use_date_for_updated" is deprecated, please use "updated_option" instead. See https://hexo.io/docs/configuration for more details.

[hexo-theme-matery主题优化 | 这么些年的技术总结](https://chen-shang.github.io/2019/08/15/ji-zhu-zong-jie/hexo/hexo-theme-matery-zhu-ti-you-hua/#toc-heading-8)

每日诗词

```

```

添加文章显示作者名字

```
---------------------- layout/_partial/post-detail.ejs -----------------------

<div class="info-break-policy">
    <% if (page.author && page.author.length > 0) { %>
        <i class="fa fa-pencil"></i> 作者: <%- page.author %>
     <% } else { %>
    <i class="fa fa-pencil"></i> 作者: <%- config.author %>
    <% } %>
</div>
```

markdown文件添加代码块语言

## 自适应屏幕的时候字体大小

```css
matery/source/css/matery.css

---------------------------- source/css/matery.css ----------------------------

/*全局基础样式*/
/*小屏幕下(手机类)的样式*/
@media only screen and (max-width: 601px) {
    .container {
        width: 95%;
    }
    header .brand-logo .logo-span {
        font-size: 1rem;
    }
    .bg-cover .title {
        font-size: 3rem;
        font-weight: 700;
        line-height: 1.85em;
        margin-bottom: 20px;
        position: relative;
    }
}

/*中等屏幕下(平板类)的样式*/
@media only screen and (min-width: 600px) and (max-width: 992px) {
    .container {
        width: 90%;
    }
    header .brand-logo .logo-span {
        font-size: 2rem;
    }
    .bg-cover .title {
        font-size: 4rem;
        font-weight: 700;
        line-height: 1.85em;
        margin-bottom: 20px;
        position: relative;
    }
}
/*大屏幕下(桌面类)的样式*/
@media only screen and (min-width: 993px) {
    .container {
        width: 85%;
        max-width: 1125px;
    }

    .post-container {
        width: 90%;
        margin: 0 auto;
        max-width: 1250px;
    }

    header .brand-logo .logo-span {
        font-size: 2rem;
    }

    .bg-cover .title {
        font-size: 4rem;
        font-weight: 700;
        line-height: 1.85em;
        margin-bottom: 20px;
        position: relative;
    }
}
```

为Hexo博客添加音乐播放器并保持跳转时不中断播放状态

```

```

