---
title:CSS + CSS3 
categories:
- 前端
tags:
- CSS
- 前端
---



《CSS权威指南 第三版》 和 《CSS权威指南 第四版》

> 480页  9h - 23h   ===> 14h  11h  1h  ==> 50张     

# [CSS权威指南 第四版](https://github.com/gdut-yy/CSS-The-Definitive-Guide-4th-zh/tree/master/docs)

HTML与CSS









字体：系统自带字体









## 值和单位

CSS 定义了三个全局关键字： inherit initial 和 unset 可以在任何属性上使用 

### inherit 继承父元素

> inherit  关键词使元素上该属性的值继承其父元素响应属性的值。换句话来说，在继承没有发生的情况下，它会强行进行属性继承。在很多情况下，你不需要特意指明继承，很多继承是自动进行的。但是，inherit关键词还是非常有用的。通过继承来做的话会使代码更加健壮

```html
继承父元素的样式
<div class="father">
	<p class="son"></p>
</div>

.father{
	border:1px solid red;
}

p{
	border:inherit;
}
```

### initial 恢复初始值(可以更改用户的CSS的默认值)  CSS 默认值

可以使用这个避免父元素的样式影响子元素

**initial** 关键词可以将属性的值恢复成初始值，某种程度上可以说它“重置”了该值。例如：fontweight属性的默认值为normal。因此，`font-weight: initial`这样声明跟`font-weight: normal`这样声明是一个效果。

> 如果所有的属性都有明确的初始值，你会觉得这个关键词的设计有点愚蠢，但事实并不是这样的。举个例子，字体颜色的初始值是由用户代理来决定的，而不是你设置的某种时髦字体。这意味着字体颜色的默认值是由浏览器的偏好设置决定的。虽然大部分用户的文本设置是黑色字体，也有一部分用户将字体设置成灰色甚至是亮红色。通过声明`color: initial;`,你可以告诉浏览器将元素内的字体颜色更改成用户设置的默认值。

### unset

**unset** 关键词是inherit和initial的通用替代。如果一个属性是继承的，unset的效果跟inherit关键词的效果相同，如果一个属性不是继承的，unset的效果则跟initial关键词的效果相同。

### all 特殊的属性 它只能接受全局关键字

**all** 关键词用于指代全部属性，除direction、unicode-bidi。因此，如果你在一个元素中这样声明`all: inherit`，意思是除了direction、unicode-bidi属性外，全部属性的值均继承自它们的父元素。如下：

```
section {color: white; background: black; font-weight: bold;}
#example {all: inherit;} // 强制从CSS中继承所有的属性 直接一步到位
<section>
<div id="example">This is a div.</div>
</section>
```

### 地址的两种表示方式

> /   ==  当前目录
>
> ./ == 下一级目录
>
> ../ ==  上一级目录

绝对路径  从盘符或者服务器的根目录开始

```html
url(protocol://server/pathname)
```

相对路径 从文件相对位置

> 在CSS中，``相对地址是相对于样式表自身的，而不是HTML文档``。例如，如果你的文档中引入了一个外部样式表，这个外部样式表中又以相对位置引入了另一个外部样式表，第二个样式表必须在第一个样式表的相对位置。即使以自身的目录找到要引入的目录位置

```html
url(pathname)
```

html 文件引入 css样式表

```html
<link rel="stylesheet" type:"text/css" href="http://heweilinag.github.io/he/wei/liang.css">
```

css 文件 引入 css样式表

```html
@import url("http://heweilinag.github.io/he/wei/liang.css")
```









image  

url



image-set

根据嵌入值中的一组条件选择一组图像。 例如，image-set（）可以指定将较大的图像用于桌面布局，而将较小的图像（像素大小和文件大小）用于移动设计。 它旨在至少近似于图片元素的srcset属性的行为。 截至2016年底，浏览器对图像集的支持仅限于Safari，Chrome和桌面Opera，并且无法与srcset的全部功能相提并论。

gradient 

单独或重复地引用线性或径向渐变图像。

url

一个外部资源的地址标识符；在这里，指的是图像的URL。



href





src



 Identifiers

部分属性可以接收一个标识符值，它是用户自己定义的某种标识符。最常见的例子是生成列表计数器。它们在值语法中表示为`<identifer>`。 标识符本身就是单词，并且区分大小写；因此，就CSS而言，myID和MyID完全不同且彼此无关。如果某个属性同时接受标识符和一个或多个关键字，则作者应注意不要定义与有效关键字相同的标识符。









值 



像素单位

|      |      |
| ---- | ---- |
| %    |      |
| px   |      |
| rem  |      |
| em   |      |
|      |      |
|      |      |





颜色单位

|      |      |      |
| ---- | ---- | ---- |
| RGB  |      |      |
| HEX  |      |      |
|      |      |      |





## 布局

盒子

形态

padding



borders



outlines



margins







IE 盒子

```

```





w3C盒子

```

```







表格







浮动





定位





flex 布局



网格



CSS 常见问题

有时设置margin:0 auto;不起作用？

+maigin: 0 auto; 指元素的上下边距为0，左右边距根据于父元素（body）宽度自适应，即左右水平居中。如果该设置不起作用大致下面两种原因。

+（1）没有为p设置宽度，如果p么有宽度，就无法参考父元素的宽度来进行自身的auto。

+（2）p具有包裹性，即脱离标准流，就好比父对象所在的标准流比喻成地表，那包裹性元素就已经上天了。没有了可供参考的父元素宽度进行auto。

+块级元素中margin、border、padding以及content宽度之和构成父元素width。

使用auto属性后，父元素宽度发生变化，该元素的宽度也会随之变化。

下图中 auto 的值就是margin、border、padding以及content宽度之和



但是当该元素被设为浮动时，该元素的width就变成了内容的宽度了，由内容撑开，也就是所谓的有了包裹性。

overflow | position:absolute | float:left/right都可以产生包裹性，替换元素也同样具有包裹性。

*|position:relavtive|相对定位 占原来的位置，不能实现模式的转化，即不具有包裹性。









#### calc()是什么？

简单来说就是CSS3中新增的一个函数，calculate（计算）的缩写。用于动态计算宽/高，你可以使用calc()给元素的各个属性设置值【margin、border、padding、font-size】等，

#### calc()语法

calc的语法就是简单的四则运算，

1. 使用“+”、“-”、“*” 和 “/”四则运算；
2. 可以使用百分比、px、em、rem等单位；
3. 可以混合使用各种单位进行计算；
4. 表达式中有“+”和“-”时，其前后必须要有空格，如"width: calc(12%+5em)"这种没有空格的写法是错误的；
5. 表达式中有“*”和“/”时，其前后可以没有空格，但建议留有空格。

#### calc()的用途




min-width || max-width ()

min-witdth:500px ===> width:500px 以上

width:500px ===> 刚好500px

max-witdth:500px ===< width:0px ~ 500px 之间



max-width(不大于) — width —- min-width(不小于)  



CSS实现宽高等比例自适应矩形

```
        .son3 {
            width:100%;
            height: calc(100vw/2);
            background-color: greenyellow;
        }
        
           .son3 {
            width: calc(100vw -(2*10)px);
            /* width: 100vw; */
            /* padding: 0px 10px; */
            margin: 0px 100px;
            height: 100vh;
            background-color: teal;
        }
```



[(29条消息)CSS中的块级元素、行内元素和行内块元素_swebin的专栏-CSDN博客_行内块元素](https://blog.csdn.net/swebin/article/details/90405950)

内联元素（行内元素）内联元素(inline element)

* a - 锚点
* abbr - 缩写
* acronym - 首字
* b - 粗体(不推荐)
* bdo - bidi override
* big - 大字体
* br - 换行
* cite - 引用
* code - 计算机代码(在引用源码的时候需要)
* dfn - 定义字段
* em - 强调
* font - 字体设定(不推荐)
* i - 斜体
* img - 图片
* input - 输入框
* kbd - 定义键盘文本
* label - 表格标签
* q - 短引用
* s - 中划线(不推荐)
* samp - 定义范例计算机代码
* select - 项目选择
* small - 小字体文本
* span - 常用内联容器，定义文本内区块
* strike - 中划线
* strong - 粗体强调
* sub - 下标
* sup - 上标
* textarea - 多行文本输入框
* tt - 电传文本
* u - 下划线
* var - 定义变量

块元素(block element)
* address - 地址
* blockquote - 块引用
* center - 举中对齐块
* dir - 目录列表
* div - 常用块级容易，也是css layout的主要标签
* dl - 定义列表
* fieldset - form控制组
* form - 交互表单
* h1 - 大标题
* h2 - 副标题
* h3 - 3级标题
* h4 - 4级标题
* h5 - 5级标题
* h6 - 6级标题
* hr - 水平分隔线
* isindex - input prompt
* menu - 菜单列表
* noframes - frames可选内容，（对于不支持frame的浏览器显示此区块内容
* noscript - ）可选脚本内容（对于不支持script的浏览器显示此内容）
* ol - 排序表单
* p - 段落
* pre - 格式化文本
* table - 表格
* ul - 非排序列表

可变元素
可变元素为根据上下文语境决定该元素为块元素或者内联元素。

* applet - java applet
* button - 按钮
* del - 删除文本
* iframe - inline frame
* ins - 插入的文本
* map - 图片区块(map)
* object - object对象
* script - 客户端脚本



区别主要是三个方面:一是排列方式，二是宽高边距设置，三是默认宽度。

块级元素会独占一行，而内联元素和内联块元素则会在一行内显示。
块级元素和内联块元素可以设置 width、height 属性，而内联元素设置无效。
块级元素的 width 默认为 100%，而内联元素则是根据其自身的内容或子元素来决定其宽度。
而行内块级元素又同时拥有块级元素和行内元素的特点。

# 《CSS揭秘》 

> 共235 页 5h 完成 1h === 50 页

## 第一章 引言

### 浏览器前缀

| 浏览器前缀 | 浏览器        |
| ---------- | ------------- |
| -moz-      | Firefox       |
| -ms-       | IE            |
| -o-        | Opera         |
| -webkit-   | Safari/Chrome |

```
-moz-border-radius:10px;
-ms-border-radius:10px;
-webkit-border-radius:10px;
-o-border-radius:10px;
border-radius:10px;
-ms-border-radius // -o-border-radius 没有在任何浏览器出现过  
```

<!-- more -->

### CSS编码技巧

#### 尽量减少代码重复

使用父级元素固定单位，修改父级元素的固定单位，子元素的单位相应的发生改变，不用修改子元素 

```
绝对单位 和 相对单位
1. 绝对单位 px
font-size: 20px;
line-height:30px;

2. 倍数
//行高是字号的1.5 倍。因此，把代码改成下面这样会更易维护：
font-size:20px;
line-height:1.5; // 使用倍数  20 * 1.5 = 30px

font-size:125%; /* 假设父级的字号是16px */
line-height 1.5;

3.相对单位 em
0.3em == .3em
```

#### 合理使用简写

```css
background: url(tr.png) top right,
url(br.png) bottom right,
url(bl.png) bottom left;
background-size: 2em 2em;
background-repeat: no-repeat;
```





## 第二章 背景与边框

RGBA/HSLA 颜色

### 半透明边框

---

半透明边框效果：盒子的边框可以透明看到 背景

```css
border:10px solid hsla(0,0%,100%,.5);
background:white;
background-clip:padding-box;
```

### 多重边框



### 灵活的背景定位



### 边框内圆角



### 条纹背景





### 复杂的背景图案



### 伪随机背景



### 连续的图像边框







## 第三章 形状

#### 自适应的椭圆

##### 圆

```
background: pink;
width: 200px;
height: 200px;
border-radius: 100px;  
// 如果指定任何大于100px 的半径，仍然可以得到一个圆形。
```

> 当任意两个相邻圆角的半径之和超过border box 的尺寸时，用户代理必须按比例减小各个边框半径所使用的值，直到它们不会相互重叠为止。

##### 椭圆 （ellipse）

单独指定水平和垂直半径，只要用一个斜杠（/）分隔这两个值即可。这个特性允许我们在拐角处创建椭圆圆角。

像素固定值（长度值）

```
border-radius: 100px/ 75px;
第一个值是水平半径
第二个值是垂直半径
```

百分比值

> 使用百分比值会得到 响应式的椭圆

```
border-radius:50%/50%;
前后的两个值现在是一致的（即使它们最终可能会被计算为不同的值）
border-radius: 50%;
```

##### 半椭圆

```
border-radius
-- border-top-left-radius
-- border-top-right-radius
-- border-bottom-left-radius
-- border-bottom-right-radius
从左上角开始以顺时针顺序应用到元素的各个拐角
```



#### 平行四边形

> skew 倾斜
>
> rotate 旋转

```
transform: skew(-45deg); //通过skew() 的变形属性来对这个矩形进行斜向拉伸
```

问题文字倾斜

解决方法

嵌套元素方案

```
<a href="#yolo" class="button">
<div>Click me</div>
</a>
.button { transform: skewX(-45deg); }
.button > div { transform: skewX(45deg); }
```

伪元素方案

```
.button {
position: relative;
/* 其他的文字颜色、内边距等样式…… */
}
.button::before {
content: ''; /* 用伪元素来生成一个矩形 */
position: absolute;
z-index:-1;
top: 0; right: 0; bottom: 0; left: 0;
background: blue;
transform:skew(45deg);
}
```



#### 菱形图片

#### 基于变形的方案 (缺点 ：不够健壮 不够简洁 只使用于处理一张正方形的图片，处理不了非正方形的图片)

```html
<div class="picture">
	<img src=".jpg" alt="..." />
</div>
.picture{
	width: 400px;
	transform:rotate(45deg);
	overflow:hidden;
}
.picture > img{
	max-width:100%;  //主要问题在于max-width: 100% 这条声明。100% 会被解析为容器（.picture）的边长。
	transform:rotate(-45deg) scale(1.42);
}

```



#### 裁切路径的方案 `clip-path`

裁切路径允许我们把元素裁剪为我们想要的任何形状。

```html
img {
    clip-path: polygon(50% 0, 100% 50%, 50% 100%, 0 50%);
	// polygon()（多边形）函数来指定一个菱形 n. 多边形；多角形物体
    transition: 1s clip-path;
}
    img:hover {
    clip-path: polygon(0 0, 100% 0,
    100% 100%, 0 100%);
}
```



#### 切角效果 





#### 梯形标签页 





#### 简单的饼图

transform 的解决方案





<section style="display:flex;justify-content: space-around;">
        <svg width="200px" height="200px" style="background:orange;border-radius:50%;transform:rotate(-90deg);">
            <circle r="100" cx="100" cy="100" fill="orange" stroke="pink" stroke-width="200" stroke-dasharray="130 600"></circle>
    </svg>
</section> 

```css
重点： 圆的虚线边框`stroke-width`必须是 圆半径 r 的两倍
svg 语法 与 CSS 语法不一样的
<svg width="100px" height="100px"> // 设置绘画容器的大小 建立直角坐标系   svg 设置容器的大小
	<circle r="30" cx="50" cy="50"> // r 半径 (cx,cy) 设置圆心的坐标位置 设置形状 circle 圆形 cx/cy 坐标点 r 半径
</svg>

svg{
	transform:rotate(-90deg); // 旋转到从正半轴开始
	border-radius:50%;  //设置一个新的圆形填充缺失的部分
	background-color:teal; // 设置与原本的圆 fill 颜色一致的颜色
}

circle {
    fill: teal;  // fill 颜色
    stroke: pink; // 边框颜色
    stroke-width: 30; // 边框宽度
    stroke-dasharray:130 189(超出整个扇形图的周长); // stroke-dasharray 虚线的线段长度  间隙长度;
    圆形的周长C = 2πr，因此在这里 C=2π × 30 ≈ 189。
    虚线的线段长度 是扇形图 占用的比例  把虚线间隙的长度设置为等于或大于整个圆周的长度时
	//虚线边框 还有很多不那么为人所知的属性可以微调描边的效果，其中之一就是stroke-dasharray，它是为虚线描边而准备
注意点: 绘画扇形图的步骤 是 画圆内 ==> 画圆外

```

添加动画效果

```css
circle {
    fill: orange;
    stroke: purple;
    stroke-width: 250;
    stroke-dasharray: 10 900;
    animation: fillup 35s linear infinite;
}

@keyframes fillup {
    to {
       
        
    }
}
```

自动适应容器的大小

```
<svg>

</svg>
```



## 第四章 视觉效果

> box-shadow: 2px 3px 4px rgba(0,0,0,.5);	// 水平距离  垂直距离  模糊半径  阴影颜色
>
> 水平 和 垂直 距离是移动距离 模糊半径是指定在原图形的模糊距离
>
> box-shadow 的本质就是一个新的盒子 从  原本的元素中分开出来
>
> 默认方向是：右下角 



### 单侧投影

---

#### 单侧投影

<div style="width:200px;height:200px;box-shadow:0px 10px 10px red;background:pink;margin:auto"></div>

问题 

```css
box-shadow: 0px -10px 4px red; 
// 这种效果没有办法做出单侧阴影的效果,它会使左右两侧产生阴影
```

解决方法

最终的解决方案来自box-shadow 鲜为人知的第四个长度参数。它排在
模糊半径参数之后，称作扩张半径。这个参数会根据你指定的值去扩大或
（当指定负值时）缩小投影的尺寸。举例来说，一个-5px 的扩张半径会把投
影的宽度和高度各减少10px（即每边各5px）。

```

```



#### 邻近投影





#### 双侧投影

把投影设置在元素的两条对边（比如左侧和右侧）时

```

```





### 不规则投影

---





### 染色效果

---



### 毛玻璃效果

---

> 半透明颜色最初的使用场景之一就是作为背景。将其叠放在照片类或其他花哨的背层1①之上，可以减少对比度，确保文本的可读性。这种效果确实很有视觉冲击力，但仍然可能导致文字很难阅读，特别是当不透明度较低或背层图案太过花哨时

解决的思路

使用伪类元素::before 再重新使用一次 背景图片 + `filter:blur(20px)`再使用z-index 把这一层图片层叠到背景透明色块的下一层 （毛玻璃效果背景图片一共使用了两次）

重点隐藏掉

```css
body {  // 背景图片层  剩余不模糊的部分
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    background: url("./壁纸.jpg") center center fixed;

}
main {  // 字体文字层  filter: blur(20px);用在这一层会模糊掉字体
    width: 70%;
    margin: 100px auto;
    padding: 30px;
    font-size: 20px;
    line-height: 1.5;
    color: white;
    background: hsla(0, 0%, 100%, 0.3); 重点 第一个 没有百分号 第二个有
    border-radius: 8px;
    position: relative;
    overflow: hidden; // 把filter:blur(20px) 中模糊出来的部分隐藏 保持 ::before 层没有其他部分
}
main::before // 设置了一个新的一层HTML 的内容 content 里面的是html 内容
main::before { // 模糊背景图片层 将这一层放在 字体文字层的下一层 达成folter:blur(20px)  模糊的区域
    content: '';
    position: absolute; // 将两层的位置置于层叠
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background: url("./壁纸.jpg") center center fixed;
    filter: blur(20px);
    z-index: -1;
    margin: -30px;
}
<main>
    <blockquote>
    " T I used to  me."
        <footer>
            <cite>
            "this is a blue"
            </cite>
        </footer>
    </blockquote>
</main>
//可以不用body中的清晰背景图片层 直接使用 毛玻璃效果（两层内容）
```

模糊效果在
中心区域看起来非常完美，但在接近边缘处会逐渐消退。这是因为模糊效果
会削减实色像素所能覆盖的范围，削减的幅度正是模糊半径的长度

为了补偿这种情况，我们需要让伪元素相对其宿主元素的尺寸再向
外扩大至少20px（即它的模糊半径）。可以通过-20px 的外边距来达到目
的，由于不同浏览器的模糊算法可能存在差异，用一个更大的绝对值（比
如-30px）会更保险一些。如图4-22 所示，这个方法可以修复边缘模糊消
伪元素模糊的方法基本上成功了，
但模糊效果在边缘处会逐渐消退，
削弱了毛玻璃的视觉效果
添加一个red 背景有助于解释
事情的真相
18　毛玻璃效果103
退的问题，但现在的情况是有一圈模糊效果超出了容器，这让它看起来不像
毛玻璃，而更像是玻璃脏了。

```
overflow: hidden;

::before
margin:-30px
```

### 折角效果

---





## 第五章 字体排印

### 连字符断行

---



### 插入换行

---





### 文本行的斑马条纹

---

### 调整tab 的宽度

---

### 连字 

---

### 华丽的& 符号 

---

### 自定义下划线 

---

### 现实中的文字效果 

---

### 环形文字

---



## 第六章 用户体验

### 选用合适的鼠标光标

---



### 扩大可点击区域

---



### 自定义复选框

---





### 通过阴影来弱化背景

---





### 通过模糊来弱化背景

---





### 滚动提示

---





### 交互式的图片对比控件

---





## 第七章 结构与布局

### 自适应内部元素

---





### 精确控制表格列宽

---





### 根据兄弟元素的数量来设置样式

---





### 满幅的背景，定宽的内容

---





### 垂直居中

---

水平居中

如果它是一个行内元素，就对它的父元素应用``text-align: center`；如果它是一个块级元素，就对它自身应用`margin: auto`。

#### 绝对定位

方法一：

局限性：它要求元素的宽高是固定的。在通常情况下，对那些需要居中的元素来说，其尺寸往往是由其内容来决定的。如果
能找到一个属性的百分比值以元素自身的宽高作为解析基准，那我们的难题就迎刃而解了！遗憾的是，对于绝大多数CSS 属性（包括margin）来说，百分比都是以其父元素的尺寸为基准进行解析的。

```css
section{
	 width: 100%;
     height: 500px;
     background-color: pink;
     position: relative;
}

.box{
	width: 18em;
    height: 14em;
    background-color: orange;
    position: absolute;
    top: 50%;
    left: 50%;
    margin-top: -7em; //	14em/2
    margin-left: -9em; //	18em/2
}
```

```css
.box{
	width:18em;
	height:6em;
	position:absolute;
	top:calc(50% - 3em);
	left:calc(50% - 9em);
}
```

方法二：

不用局限于宽度和高度

```css
.box{
	position:absolute;
	top:50%;
	left:50%;
	transform:translate(-50%,-50%);
}
```



#### 视口单位

> vw 是与视口宽度相关的。与常人的直觉不符的是，1vw 实际上表示
> 视口宽度的1%，而不是100%。
>  与 vw类似，1vh表示视口高度的 1%。
>
> 当视口宽度小于高度时，1vmin等于 1vw，否则等于 1vh。
> 当视口宽度大于高度时，1vmax等于 1vw，否则等于 1vh。

他是相对于视口（整个窗口） 居中的不是父元素居中的

```
main { // 设置父元素
    width: 18em;
    padding: 1em 1.5em;
    margin: 50vh auto 0; 
    transform: translateY(-50%);
}
```

#### FlexBox

```css
body{ //父元素
	display:flex;
	min-height:100vh;
	margin:0;
}

main{ // 子元素
	margin:auto;
}
```

```
body{ //父元素
	width:18em;
	height:10em;
	display:flex;
	align-item:center;
	justify-content:center;
}
```



### 紧贴底部的页脚

---

```html
<header>
<h1>Site name</h1>
</header>
<main>
<p>Bacon Ipsum dolor sit amet...
<!-- 从baconipsum.com那里复制一些示意文字过来 --></p>
</main>
<footer>
<p>© 2015 No rights reserved.</p>
<p>Made with ♥ by an anonymous pastafarian.</p>
</footer>
```

固定高度





FlexBox的解决方法



```css
body{
	display: flex;
	flex-flow:column;
	min-height:100vh;
}
main{
	flex:1;  //flex: flex-grow flex-shrink flex-basis;
}
```



## 第八章过渡和动画

### 缓动效果

---



### 逐帧动画

---



### 闪烁效果

---





### 打字动画

---





### 状态平滑的动画

---





### 沿环形路径平移的动画







