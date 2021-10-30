---

title: Vue学习
categories:
  - Vue
tags:
  - Vue
  - 前端
abbrlink: 1167
---

# Vue

相关文章

- [vue.js 1.x 文档](https://v1-cn.vuejs.org/)
- [vue.js 2.x 文档](https://cn.vuejs.org/)
- [String.prototype.padStart(maxLength, fillString)](http://www.css88.com/archives/7715)
- [js 里面的键盘事件对应的键码](http://www.cnblogs.com/wuhua1/p/6686237.html)
- [Vue.js 双向绑定的实现原理](http://www.cnblogs.com/kidney/p/6052935.html)
- [URL 中的 hash（井号）](http://www.cnblogs.com/joyho/articles/4430148.html)
- [pagekit/vue-resource](https://github.com/pagekit/vue-resource)
- [navicat 如何导入 sql 文件和导出 sql 文件](https://jingyan.baidu.com/article/a65957f4976aad24e67f9b9b.html)
- [贝塞尔在线生成器](http://cubic-bezier.com/#.4,-0.3,1,.33)

## VS 插件

### vscode-vue

Syntax Highlight for Vue.js

#### Code Snippets

| trigger      | snippet           |
| :----------- | :---------------- |
| `vud-cdn`    | `tag to cdnjs`    |
| `add`        | `vm.$add`         |
| `delete`     | `vm.$delete`      |
| `eval`       | `vm.$eval`        |
| `set`        | `vm.$set`         |
| `get`        | `vm.$get`         |
| `ipo`        | `vm.$interpolate` |
| `log`        | `vm.$log`         |
| `wat`        | `vm.$watch`       |
| `vue`        | `new Vue`         |
| `vue-config` | `Vue.config`      |
| `vue-dir`    | `Vue.directive`   |
| `vue-extend` | `Vue.extend`      |
| `vue-filter` | `Vue.filter`      |
| `v`          | `an empty object` |

### [Vetur](https://vuejs.github.io/vetur/)

1、vue文件没有css提示

```json
setting.json
"emmet.syntaxProfiles": {
  "vue-html": "html",
  "vue": "html"
},
 
"vetur.validation.template": false,
```

2、问题Vue文件出现  vscode红色波浪线问题 （严格模式下的格式警告），搜索Eslint 插件 取消 Eslint:Enable 的勾选，或者添加以下一行

```json
 "eslint.enable": false
```

[VSCode .vue 文件 html css 无智能提示 - 简书](https://www.jianshu.com/p/ad8e2698b221)

[vscode下的vue文件格式化 - 掘金](https://juejin.im/post/5bfcdee25188251d9e0c40f2)

## 基础

### 概念

#### 软件架构

MVVM 

```html
// MVVM中的View
<div id="app">
    <h1>Yout input is{{ message }}</h1>
    <input type="text" v-model="message">
</div>
<script>
    // MVVM VM调度者
    var vm = new Vue({
        el: '#app',
        data: { // 这里的data 就是MVVM中的，专门用来保存 每个页面的数据的
            message: ''
        }
    })
</script>
```

#### Node（后端）中的 M(数据库里面的数据)VC 与 前端中的 M(页面中的数据)VVM 之间的区别

- `MVC 是后端的分层开发概念`； Modle 数据保存 View Controller 业务逻辑
- `MVVM 是前端视图层的概念`，主要关注于 视图层分离，也就是说：MVVM 把前端的视图层，分为了 三部分 Model, View , VM ViewModel
- 为什么有了 MVC 还要有 MVVM

#### Vue.js 基本代码 和 MVVM 之间的对应关系

![01.MVC和MVVM的关系图解](https://i.loli.net/2020/05/07/zZb2BVYg8TeArLm.png)

#### Vue.js 是什么

- Vue 被定义成一个用来开发 Web 界面的前端库，是一个非常轻量级的工具。
- Vue.js 本身具有`响应式编程和组件化`的特点
- Vue.js 是目前最火的一个前端框架，React 是最流行的一个前端框架（React 除了开发网站，还可以开发手机 App， Vue 语法也是可以用于进行手机 App 开发的，需要借助于 Weex）
- Vue.js 是前端的**主流框架之一**，和 Angular.js、React.js 一起，并成为前端三大主流框架！
- Vue.js 是一套构建用户界面的框架，`Vue 的核心库只关注视图层`，它不仅易于上手，还便于与第三方库或既有项目整合。（Vue 有配套的第三方类库，可以整合起来做大型项目的开发）
- 前端的主要工作？主要负责 MVC 中的 V 这一层；主要工作就是和界面打交道，来制作前端页面效果；

* `一套用于构建用户界面的JavaScript渐进式框架` 什么是渐进式（由浅入深）简单到复杂

* Vue.js 被设计为可以`自底向上逐层应用`
* Vue 本身具有组件化和响应式编程（就是保持状态和视图一致、数据绑定）的特点

#### Vue 的优点

- 体积小，压缩后 33K

- 更高的运行效率 （高效） 20kb min+ gzip 运行大小 超快虚拟 DOM

  > 基于虚拟 DOM,一种可以预先通过 JavaScript 进行各种计算，把最终的 DOM 操作计算出来并优化的技术，由于这个 DOM 操作属于预处理操作，并没有真实的操作，所以叫做虚拟 DOM

- 双向数据绑定 保持状态与视图一致

- 生态丰富，学习成本低 大量的 UI 框架、常用组件

#### 为什么要学习流行框架

- 企业为了提高开发效率：在企业中，时间就是效率，效率就是金钱；

* 企业中，使用框架，能够提高开发的效率；

- 提高开发效率的发展历程：原生 JS -> Jquery 之类的类库 -> 前端模板引擎 -> Angular.js / Vue.js（``能够帮助我们减少不必要的 DOM 操作；提高渲染效率；双向数据绑定的概念【通过框架提供的指令，我们前端程序员只需要关心数据的业务逻辑，不再关心 DOM 是如何渲染的了】``）
- 在 Vue 中，一个核心的概念，就是让用户不再操作 DOM 元素，解放了用户的双手，让程序员可以更多的时间去关注业务逻辑；

#### 框架和库的区别

+ 框架：``是一套完整的解决方案``；对项目的侵入性较大，项目如果需要更换框架，则需要重新架构整个项目。
	+ 如node 中的 express；

+ `库（插件）：提供某一个小功能`，对项目的侵入性较小，如果某个库无法完成某些需求，可以很容易切换到其它库实现需求。 
- 从 Jquery 切换到 Zepto 
  - 从 EJS 切换到 art-template

### 安装

---

> 安装成功 页面控制台出现 vue 警告
>
> You are running Vue in development mode.
> Make sure to turn on production mode when deploying for production.
> See more tips at https://vuejs.org/guide/deployment.html

#### 1. CDN

```js
<!-- 开发环境版本，包含了有帮助的命令行警告 -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<!-- 生产环境版本，优化了尺寸和速度 -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

#### 2.官方 vue-cli 脚手架工具

```bash
命令行工具(CLI) 脚手架工具（安装vue-cli） 先安装node.js 使用npm命令 npm-v
查看npm版本 node-v 查看node版本 path 配置环境变量 
全局安装vue-cli 
npm install -g @vue/cli
# OR
yarn global add @vue/cli
本地安装vue-cli 
npm install @vue/cli
查看 vue-cli 的版本 
vue -V
创建项目
vue create my-project
cd my-project
npm install
npm run dev
注意：Vue.js 不支持 IE8 及其以下 IE 版本。
```

#### 3.webpack 安装vue-cli 脚手架工具

```bash
webpack安装vue 
全局安装 vue-cli
cnpm install -g @vue/cli
查看 vue-cli 的版本 
vue -V
@vue/cli 4.4.6
创建一个基于webpack 模板的新项目
vue init webpack my-project 
默认回车
安装依赖包 
cd my-project 
npm install
启动vue-cli
npm run dev 
```

安装报错

>  vue init webpack vue-webpack
>
>   Command vue init requires a global addon to be installed.
>   Please run yarn global add @vue/cli-init and try again.
>
>  @vue cli全局已安装@vue/cli-init后 仍提示无法初始化
>
> 解决方法
>
> 方法一
>
> yarn global add @vue/cli-init
>
> 方法二
>
> npm安装2.0兼容的cli-init
> npm install -g @vue/cli-init
>
> @vue/cli 与 cli-init 不兼容

#### `4.nrm`的安装使用

作用：提供了一些最常用的 NPM 包镜像地址，能够让我们快速的切换安装包时候的服务器地址；
什么是镜像：原来包刚一开始是只存在于国外的 NPM 服务器，但是由于网络原因，经常访问不到，这时候，我们可以在国内，创建一个和官网完全一样的 NPM 服务器，只不过，数据都是从人家那里拿过来的，除此之外，使用方式完全一样；

1. 运行`npm i nrm -g`全局安装`nrm`包；
2. 使用`nrm ls`查看当前所有可用的镜像源地址以及当前所使用的镜像源地址；
3. 使用`nrm use npm`或`nrm use taobao`切换不同的镜像源地址；

> node.js 常用的命令：node、npm、yarn、cnpm、nrm、nvm

### 目录分析

### @vue/cli安装目录分析

> node_modules 
>
> public   发布源代码
>
> src 开发目录
>
> -- assets
>
> -- components  组件
>
> -- App.vue  vue入口文件
>
> -- main.js	js入口文件
>
> package.json 项目配置文件。
>
> babel.config.js  babel配置文件。

### webpack安装@vue/cli目录分析

| 目录/文件    | 说明                                                         |
| :----------- | :----------------------------------------------------------- |
| build        | 项目构建(webpack)相关代码                                    |
| node_modules | npm 加载的项目依赖模块                                       |
| config       | 配置目录，包括端口号等。我们初学可以使用默认的。             |
| src          | 这里是我们要开发的目录，基本上要做的事情都在这个目录里。里面包含了几个目录及文件：assets: 放置一些图片，如logo等。components: 目录里面放了一个组件文件，可以不用。App.vue: 项目入口文件，我们也可以直接将组件写这里，而不使用 components 目录。main.js: 项目的核心文件。 |
| static       | 静态资源目录，如图片、字体等。                               |
| test         | 初始测试目录，可删除                                         |
| .xxxx文件    | 这些是一些配置文件，包括语法配置，git配置等。                |
| index.html   | 首页入口文件，你可以添加一些 meta 信息或统计代码啥的。       |
| package.json | 项目配置文件。                                               |
| README.md    | 项目的说明文档，markdown 格式                                |





## 基础特性

### 实例及选项

---

#### 模板渲染/模板

```html
<div id="app">
  <h1>Yout input is{{ message }}</h1>
</div>
<script>
  var vm = new Vue({
    el: "#app",
    data: {
      message: "Hello world"
    },
  });
</script>
```

重点

```html
vm.message == data.message
vm.message = 100
data.message = 200
vm.$data === data
vm.$el === el

<div id="app">
  <h1>Yout input is{{ message }}</h1>
</div>
<script>
  var data = {message: "Hello world"}
  var vm = new Vue({
    el: "#app",
    data: data
  });
</script>
```



#### 绑定用户数据/数据

```html
//Vue写法
<div id="app">
    <h1>Yout input is{{ message }}</h1>
    <input type="text" v-model="message">
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            message: ''
        }
    })
</script>
//js写法
<h1>Your input is <span id="append"><span></h1>
<input type="text">
<script>
    var inp = document.getElementsByTagName('input')[0];
    inp.oninput = function(){
        var appends = document.querySelector('#append');
        var val = inp.value;
        appends.innerHTML = val;
    }
    //改变时
    var inp = document.getElementsByTagName('input')[0];
    inp.onchange = function(){
        var appends = document.querySelector('#append');
        var val = inp.value;
        appends.innerHTML = val;
    }
</script>
```

#### 事件绑定/方法

```html
<button v-on:click="event.alert">按钮</button>
<script>
  new Vue({
    el: "#app",
    data: {
      a: 1,
    },
    methods: {
      alert: function () {
        console.log(this.a);
      },
    },
  });
</script>
```

#### 组件化，自定义 HTML 标签

```html
<div id="app">
  <message content="Hello World!!!"></message>
  <message content="Hello Name!!!"></message>
</div>
<script>
  var Message = Vue.extend({
    props: ["content"],
    template: "<h1>{{ content }}</h1>",
  });
  Vue.component("message", Message);
  var vm = new Vue({
    el: "#app",
  });
</script>

<div id="commponts-demo">
  <button-counter></button-counter>
  <button-counter></button-counter>
  <button-counter></button-counter>
</div>
<script>
  Vue.component("button-counter", {
    data: function () {
      return {
        count: 0,
      };
    },
    template:
      '<button v-on:click="count++">You clicked me {{ count }} times.</button>',
  });
  new Vue({
    el: "#commponts-demo",
  });
</script>
```

#### 插值

```html
<div id="app">
  <!-- 文本插值 -->
  <h1>{{ name }}</h1>
  <h1 v-once>{{ name }}</h1>
  <!-- 文本插值不可改变 -->

  <!-- HTML插值 -->
  <p v-bind:id="id">id="id"HTML属性</p>
  <p v-bind:id="'id-'+id">id="'id-'+id"HTML属性</p>
  <p :id="id">id="id"HTML属性</p>
  <p :id="'id-'+id">id="'id-'+id"HTML属性</p>
  <!-- 绑定表达式 -->
  <p>{{ index+100 }}</p>
  <p>{{ index+id }}</p>
  <p>{{ inde=200?'true':'false' }}</p>
</div>
<script>
  var vm = new Vue({
    el: "#app",
    data: {
      id: 1,
      index: 10,
      name: "heweiliang",
      avater: "http://www.baidu.com",
      count: [1, 2, 3, 4, 5],
      names: ["value1", "value2", "value3"],
      items: [
        { name: "value1.0", version: "1.0" },
        { name: "value2.0", version: "2.0" },
      ],
    },
  });
</script>
```

#### 方法

```html
<div id="app">
  <h1>
    {{a}} --- {{b}}
  </h1>
</div>
<script>
  var data = { a: 1, b: 100 };
  var vm = new Vue({
    el: "#app",
    data: data,
    methods:{ //这个methods属性中定义了当前vue实例所有可用的方法
        show:function(){
            alert('Hello')
        }
    } 
  });
  console.log(vm.a == data.a);
  // vm.$data.a = 'nihao';
  vm.b = "123456";
  data.b = "abcdf";
  vm.$watch("a", function (newVal, oldVal) {
    console.log(newVal + "---" + oldVal);
  });
  vm.a = "123456456";
</script>
```

#### 生命周期

什么是生命周期：从 Vue 实例创建、运行、到销毁期间，总是伴随着各种各样的事件，这些事件，统称为生命周期！

[生命周期钩子](https://cn.vuejs.org/v2/api/#选项-生命周期钩子)：就是生命周期事件的别名而已；

生命周期钩子 = 生命周期函数 = 生命周期事件

![lifecycle](https://i.loli.net/2020/05/09/x2omYMbzdQ83tKa.png)



![lifecycle](https://i.loli.net/2020/05/09/z6XpaGDCwvTlAUS.png)

主要的生命周期函数分类： `创建 =>运行==>销毁 `

- ==创建期间的生命周期函数==：

  - beforeCreate：实例刚在内存中被创建出来，此时，还没有初始化好 data 和 methods 属性（调用报错 ）`组件刚刚被创建`
  - created：实例已经在内存中创建 OK，此时 data 和 methods 已经创建 OK，此时还没有开始 编译模板
  - beforeMount：此时已经完成了模板的编译，但是还没有` `挂载到页面·中 `挂载之前`
  - mounted：此时，已经将编译好的模板，挂载到了页面指定的容器中显示 `挂载之后`

- ==运行期间的生命周期函数==：

* beforeUpdate：状态更新之前   执行此函数， 此时 data 中的状态值是最新的，但是界面上显示的 数据还是旧的，因为此时还没有开始重新渲染 DOM 节点
* updated：实例更新完毕之后调用此函数，此时 data 中的状态值 和 界面上显示的数据，都已经完成了更新，界面已经被重新渲染好了！

- ==销毁期间的生命周期函数==：

* beforeDestroy：实例销毁之前调用。在这一步，实例仍然完全可用。`组件销毁前调用`
* destroyed：Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。`组件销毁后调用`

create(创建) –>beforecompiled(编译前) -> compiled(编译) -> ready(准备) -> beforeDestory(销毁前) -> destory(销毁)

beforeCreate->created -> beforeMount -> mounted -> beforeUpdate -> updated

```html
<script>
  var vm = new Vue({
    el: "#app",
    init: function () {
      console.log("init");
    },
    created: function () {
      console.log("created");
    },
    beforeCompile: function () {
      console.log("beforeCreate");
    },
    compiled: function () {
      console.log("compiled");
    },
    attached: function () {
      console.log("attached");
    },
    beforeDestroy: function () {
      console.log("beforeDestory");
    },
    destroyed: function () {
      console.log("destoryed");
    },
    ready: function () {
      console.log("ready");
      this.$destroy();
    },
  });
  setTimeout(function () {
    vm.msg = "Hello nihao";
  }, 3000);
</script>
```

### 数据绑定

---

#### 数据绑定语法



#### 插值表达式



#### 计算属性和侦听器

 计算属性
​ 基础例子
​ 计算属性缓存 vs 方法
​ 计算属性 vs 侦听属性
​ 计算属性的 setter
​ 侦听器

#### 条件渲染

#####  v-if

 在 <template> 元素上使用 v-if 条件渲染分组

#####  v-else

#####  v-else-if

 用 key 管理可复用的元素

#####  v-show

 v-if vs v-show

v-if 的特点：每次都会重新删除或创建元素

v-show的特点 每次不会重新进行DOM的删除和创建操作，只是切换了元素的display : 

none 样式

```html
<input type="button" value="点击切换" @click="flag=!flag">
<input type="button" value="点击切换" @click="toggle">
<p v-if="flag">I used to find notes left in the collection basket, beautiful notes about my homilies</p>
<p v-show="flag">I used to find notes left in the collection basket, beautiful notes about my homilies</p>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            flag: true
        },
        methods: {
            toggle() {
                this.flag = !this.flag
            }
        }
    });
</script>
```

 v-if 与 v-for 一起使用

##### `v-if`和`v-show`

> 一般来说，v-if 有更高的切换消耗而
>
>  v-show 有更高的初始渲染消耗。因此，
>
> 如果需要频繁切换 v-show 较好，如果在运行时条件不大可能改变 v-if 较好。
>
> 如果元素可能永远也不会被显示出来被用户看到，则推荐使用 v-if

#### 列表

in  后面我们放过普通数组 对象数组 对象 数字

##### `v-for`和`key`属性

1. 迭代数组

```html
<ul>
  <li v-for="(item, i) in list">{{item}}+{{i}}</li>
    // i 是index 索引值
</ul>
```

2. 迭代对象中的属性

```html
<!-- 循环遍历对象身上的属性 -->
data:{
	useInfo:{
		id:1830315,
		name:'hwl',
		gender:'男'
	}
}
//val key index
<div v-for="(val, key, i) in userInfo">
	{{val}} --- {{key}} --- {{i}}
</div>

<div v-for="(val, key, i) in userInfo">
	{{val}} --- {{key}} --- {{i}}
</div>
```

3. 迭代数

```html
<p v-for="i in 10">这是第 {{i}} 个P标签</p>
```

4. 迭代对象数组

```html
data:{
	list:[
		{id:1,name:'zs1'},
		{id:2,name:'zs2'},
		{id:3,name:'zs3'},
		{id:4,name:'zs4'},
	]
}
<ul>
  <li v-for="(item, i) in list">索引：{{i}} --- 姓名：{{item.name}} --- 年龄：{{item.id}}</li>
    // i 是index 索引值
</ul>
```

> 2.2.0+ 的版本里，**当在组件中使用** v-for 时，key 现在是必须的。
>
> 在组件中，使用的时候

```html
<p v-for="item in list" :key="item.id"></p>
// key 绑定键
v-for 循环的时候 key 属性只能使用 number 获取string
key在使用的时候，必须使用 v-bind 属性绑定的形式，指定key的值
```



当 Vue.js 用 v-for 正在更新已渲染过的元素列表时，它默认用 “**就地复用**” 策略。如果数据项的顺序被改变，Vue 将**不是移动 DOM 元素来匹配数据项的顺序**， 而是**简单复用此处每个元素**，并且确保它在特定索引下显示已被渲染过的每个元素。

为了给 Vue 一个提示，**以便它能跟踪每个节点的身份，从而重用和重新排序现有元素**，你需要为每项提供一个唯一 key 属性。

用 v-for 把一个数组对应为一组元素
 在 v-for 里使用对象
 维护状态
 数组更新检测
 变异方法
 替换数组
 注意事项
 对象变更检测注意事项
 显示过滤/排序后的结果
 在 v-for 里使用值范围
 在`` <template> `上使用 v-for
 v-for 与 v-if 一同使用
 在组件上使用 v-for

#### 表单控件

#### Class 与 Style 绑定

##### 使用 class 样式

1. 数组  `[' ',' ']`

```html
<h1 :class="['red', 'thin']">这是一个邪恶的H1</h1>
```

2. 数组中使用三元表达式 `['red', 'thin', isactive?'active':'']`

```html
<h1 :class="['red', 'thin', isactive?'active':'']">这是一个邪恶的H1</h1>
data:{
	isactive: false;
}
```

3. 数组中嵌套对象

```html
<h1 :class="['red', 'thin', {'active': isactive}]">这是一个邪恶的H1</h1>
data:{
	isactive: false;
}
```

4. 直接使用对象

```html
在为class使用v-bind绑定对象的时候，对象的属性是类名，由于对象的属性可带引号，也可不带引号。
<h1 :class="{red:true, italic:true, active:true, thin:true}">这是一个邪恶的H1</h1>
```

##### 使用内联样式

1. 直接在元素上通过 `:style` 的形式，书写样式对象

    属性里面有 `-`需要单引号 包括

```html
<h1 :style="{color: 'red', 'font-size': '40px'}">这是一个善良的H1</h1>
```

2. 将样式对象，定义到 `data` 中，并直接引用到 `:style` 中

- 在 data 上定义样式：

```
data: {
        h1StyleObj: { color: 'red', 'font-size': '40px', 'font-weight': '200' }
}
```

- 在元素中，通过属性绑定的形式，将样式对象应用到元素中：

```
<h1 :style="h1StyleObj">这是一个善良的H1</h1>
```

3. 在 `:style` 中通过数组，引用多个 `data` 上的样式对象

- 在 data 上定义样式：

```
data: {
        h1StyleObj: { color: 'red', 'font-size': '40px', 'font-weight': '200' },
        h1StyleObj2: { fontStyle: 'italic' }
}
```

- 在元素中，通过属性绑定的形式，将样式对象应用到元素中：

```
<h1 :style="[h1StyleObj, h1StyleObj2]">这是一个善良的H1</h1>
```

绑定 HTML Class
​ 对象语法
​ 数组语法
​ 用在组件上
绑定内联样式
​ 对象语法
​ 数组语法
​ 自动添加前缀
​ 多重值

### 模板渲染

---

### 事件绑定与监听

---

## 指令

### 内置指令

#### v-cloak

Vue 之 - `基本的代码结构`和`插值表达式`、

使用 v-cloak能够解决 插值表达式闪烁的问题（网速慢，页面会出现插入表达式{{ }} 的问题;

```html
<style>
	[v-cloak]{
		display:none;
	}
</style>
<div id="app">
  <h1 v-cloak>Yout input is{{ message }}</h1>
</div>
<script>
  var vm = new Vue({
    el: "#app",
    data: {
      message: "Hello world",
    },
  });
</script>
```

#### `v-text`和`v-html`

默认 v-text 是没有闪烁问题，v-text会覆盖元素中原本的内容，但是 插值表达式 只会替换自已的这个占位符，不会把整个元素的内容清空 

```
<h1 v-cloak>Yout input is======== {{ message }} ------------</h1>
<p v-text="msg">======================</p>
<div v-html="msg2"> </div>
```

#### `v-bind`

1. 直接使用指令`v-bind`
2. 使用简化指令`:`
3. 在绑定的时候，拼接绑定内容：`:title="btnTitle + ', 这是追加的内容'"`
4. 是vue中，提供的用于绑定属性的指令
5. 可以写合法的JS表达式

#### `v-on的缩写`和`事件修饰符`

##### v-on的缩写 : @

事件修饰符：

- .stop 阻止冒泡 事件 默认从里到外 阻止外层事件 
- .prevent 阻止默认事件 a链接的跳转行为 
- .capture 添加事件侦听器时使用事件捕获模式 从外到里触发事件
- .self 只当事件在该元素本身（比如不是子元素）触发时触发回调z阻止了当前元素的冒泡事件

- .once 事件只触发一次

```
<input type="button" value="按钮" @click.事件修饰符="btnHandler">
```

.self只会阻止自已身上冒泡行为的触发，并不会真正阻止 冒泡的行为

##### `v-on 跑马灯效果`

```vue
<div id="app">
    <p>{{info}}</p>
    <input type="button" value="开启" @click="go">
    <input type="button" value="停止" v-on:click="stop">
</div>
<script>
var vm = new Vue({
    el: '#app', 
    data: {
        info: '猥琐发育，别浪~！', 
        intervalId:null
    }, methods: {
        go() { // 如果当前有定时器在运行，则直接return if
            if(this.intervalId != null) { return; } // 开始定时器 this.intervalId =
            setInterval(() => {
                  this.info = this.info.substring(1) + this.info.substring(0, 1);
            }, 500);
        }, 
        stop() { 
            clearInterval(this.intervalId); 
        	this.intervalId = null;
        }
    }
});
</script>
// 注意 在 vue实例中，如果想要获取data上的数据，或者 想要调用methods中的方法，必须通过this.数据属性名 或 this.方法名 来访问，这里的this，就表示 我们 new 出来的·VM实例对象
VM实例，会监听自已身上data中所有数据的改变，只要数据一发生改变，就会自动把最新的数据，从data上同步到页面中去;[只需要关心数据，不需要考虑如何重新渲染DOM页面]
```

#### `v-model`和`双向数据绑定`

v-bind 只能实现数据的单向绑定 ，从M到V 无法实现数据的双向绑定

使用  v-model 指令，可以实现 表单元素 和Model 中数据的双向数据绑定

v-model 只能运用在表单元素中

在vue中 ，使用事件绑定机制，为元素指定处理函数的时候，如果加了小括号，就可以给函数传参了

##### 简易计算器案例

```html
<div id="app">
    <input type="text" v-model="n1">
    <select v-model="opt">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
    </select>
    <input type="text" v-model="n2">
    <input type="button" value="=" @click="getResult">
    <input type="text" v-model="result">
</div>
<script>
    var vm = new Vue({
        el: '#app',
        data: {
            n1: 0,
            n2: 0,
            result: 0,
            opt: '0'
        },
        methods: {
            getResult() {	
                switch (this.opt) {
                    case '+':
                        this.result = parseInt(this.n1) + parseInt(this.n2);
                        break;
                    case '-':
                        this.result = parseInt(this.n1) - parseInt(this.n2);
                        break;
                    case '*':
                        this.result = parseInt(this.n1) * parseInt(this.n2);
                        break;
                    case '/':
                        this.result = parseInt(this.n1) / parseInt(this.n2);
                        break;
                }
                   // var codestr = 'parseInt(this.n1)' + this.opt+'parseInt(this.n2)'
                   //this.result = eval(codestr)
            }
        }
    });
</script>
```

### [自定义指令](https://cn.vuejs.org/v2/guide/custom-directive.html)

1. 自定义全局和局部的 自定义指令：

```
    // 自定义全局指令 v-focus，为绑定的元素自动获取焦点：

    Vue.directive('focus', {

      inserted: function (el) { // inserted 表示被绑定元素插入父节点时调用

        el.focus();

      }

    });



    // 自定义局部指令 v-color 和 v-font-weight，为绑定的元素设置指定的字体颜色 和 字体粗细：

      directives: {

        color: { // 为元素设置指定的字体颜色

          bind(el, binding) {

            el.style.color = binding.value;

          }

        },

        'font-weight': function (el, binding2) { // 自定义指令的简写形式，等同于定义了 bind 和 update 两个钩子函数

          el.style.fontWeight = binding2.value;

        }

      }

```

2. 自定义指令的使用方式：

```
<input type="text" v-model="searchName" v-focus v-color="'red'" v-font-weight="900">

```

## 过滤器 && 过渡

### 过滤器

概念：Vue.js 允许你自定义过滤器，**可被用作一些常见的文本格式化**。过滤器可以用在两个地方：**mustache 插值和 v-bind 表达式**。过滤器应该被添加在 JavaScript 表达式的尾部，由“管道”符指示；

### 私有过滤器

1. HTML 元素：

```
<td>{{item.ctime | dataFormat('yyyy-mm-dd')}}</td>

```

2. 私有 `filters` 定义方式：

```
filters: { // 私有局部过滤器，只能在 当前 VM 对象所控制的 View 区域进行使用

    dataFormat(input, pattern = "") { // 在参数列表中 通过 pattern="" 来指定形参默认值，防止报错

      var dt = new Date(input);

      // 获取年月日

      var y = dt.getFullYear();

      var m = (dt.getMonth() + 1).toString().padStart(2, '0');

      var d = dt.getDate().toString().padStart(2, '0');



      // 如果 传递进来的字符串类型，转为小写之后，等于 yyyy-mm-dd，那么就返回 年-月-日

      // 否则，就返回  年-月-日 时：分：秒

      if (pattern.toLowerCase() === 'yyyy-mm-dd') {

        return `${y}-${m}-${d}`;

      } else {

        // 获取时分秒

        var hh = dt.getHours().toString().padStart(2, '0');

        var mm = dt.getMinutes().toString().padStart(2, '0');

        var ss = dt.getSeconds().toString().padStart(2, '0');



        return `${y}-${m}-${d} ${hh}:${mm}:${ss}`;

      }

    }

  }

```

> 使用 ES6 中的字符串新方法 String.prototype.padStart(maxLength, fillString='') 或 String.prototype.padEnd(maxLength, fillString='')来填充字符串；

### 全局过滤器

```
// 定义一个全局过滤器

Vue.filter('dataFormat', function (input, pattern = '') {

  var dt = new Date(input);

  // 获取年月日

  var y = dt.getFullYear();

  var m = (dt.getMonth() + 1).toString().padStart(2, '0');

  var d = dt.getDate().toString().padStart(2, '0');



  // 如果 传递进来的字符串类型，转为小写之后，等于 yyyy-mm-dd，那么就返回 年-月-日

  // 否则，就返回  年-月-日 时：分：秒

  if (pattern.toLowerCase() === 'yyyy-mm-dd') {

    return `${y}-${m}-${d}`;

  } else {

    // 获取时分秒

    var hh = dt.getHours().toString().padStart(2, '0');

    var mm = dt.getMinutes().toString().padStart(2, '0');

    var ss = dt.getSeconds().toString().padStart(2, '0');



    return `${y}-${m}-${d} ${hh}:${mm}:${ss}`;

  }

});

```

> 注意：当有局部和全局两个名称相同的过滤器时候，会以就近原则进行调用，即：局部过滤器优先于全局过滤器被调用！

## [动画](https://cn.vuejs.org/v2/guide/transitions.html)

动画能够提高用户的体验，帮助用户更好的理解页面中的功能；

### 使用过渡类名实现动画

`.v-enter-active 和 .v-leave-active设置动画过渡的时间`

`.v-enter 和 .v-leave-active 设置动画进入和离开`

```html
<style>
/* 定义进入和离开时候的过渡状态 */
.v-enter-active,
.v-leave-active {
    transition: all 0.2s ease;
    position: absolute;
}

/* 定义进入过渡的开始状态 和 离开过渡的结束状态 */
.v-enter,
.v-leave-to {
    opacity: 0;
    transform: translateX(100px);
}
</style>

<div id="app">
    <input type="button" value="动起来" @click="myAnimate">
    <!-- 使用 transition 将需要过渡的元素包裹起来 -->
    <transition>
      <div v-show="isshow">动画哦</div>
    </transition>
</div>

<script>
// 创建 Vue 实例，得到 ViewModel
var vm = new Vue({
  el: '#app',
  data: {
    isshow: false
  },
  methods: {
    myAnimate() {
      this.isshow = !this.isshow;
    }
  }
});
</script>
```

### 自定义v-前缀

通过可以给`transtion标签添加name属性设置自定义v-前缀`

```html
<style>
/* 定义进入和离开时候的过渡状态 */
.fade-enter-active,
.fade-leave-active {
    transition: all 0.2s ease;
    position: absolute;
}

/* 定义进入过渡的开始状态 和 离开过渡的结束状态 */
.fade-enter,
.fade-leave-to {
    opacity: 0;
    transform: translateX(100px);
}
</style>

<div id="app">
    <input type="button" value="动起来" @click="myAnimate">
    <!-- 使用 transition 将需要过渡的元素包裹起来 -->
    <transition name="fade">
      <div v-show="isshow">动画哦</div>
    </transition>
</div>

<script>
// 创建 Vue 实例，得到 ViewModel
var vm = new Vue({
  el: '#app',
  data: {
    isshow: false
  },
  methods: {
    myAnimate() {
      this.isshow = !this.isshow;
    }
  }
});
</script>
```

### 钩子函数实现小球半场动画

```html
<style>
    .ball{
        width:20px;
        height:20px;
        border-radius:50%;
        background-color:red;
    }
</style>
<div id="app">
    <input type="button" value="按钮" @click="flag=!flag">
    <transition 
       @before-enter="beforeEnter" 
       @enter="enter"
       @after-enter="afterEnter"
               >
		<div class="ball" v-show="flag"></div>
     </transition>
</div>	

<script>
    var vm = new Vue({
        el: '#app',
        data: {
            flag: true
        },
        methods: {
            
    // 动画钩子函数的第一个参数el,表示 要执行动画的那个DOM元素，是个原生的JS DOM对象 是通过 document.getElementById('')方式获取到的原生的JS DOM对象       
         	beforeEnter(el){// 动画入场之前，此时动画尚未开始，可以在beforeEnter中，设置元素开始动画之前的起始样式
                el.style.transform="translate(0,0)";
            };
            enter(el,done){
 // 表示动画 开始之后的样式，这里，可以设置小球完成之后的，结束状态       	  		el.offsetWidth没有实际的作用，可以认为强制动画刷新el.offsetTop/Left/Right
        	    el.offsetWidth
        		el.style.transform="translate(150px,450px)"
       	        el.style.transition="all 1s ease"
        		//这里的done ,起始就是 afterEnter这个函数，也就是 done 是 afterEnter函数的引用
        		done()
    		},
            afterEnter(el){
                this.flag = !this.flag      
            }        
        }
    });
</script>
```

> 自定义指令 
>
> Vue.directive(‘focus’,function(el){
>
> })
>
> el是原生的DOM元素

### 小球动画每次重新开始的位置

```html

```



### 使用transition-group元素实例

```html
<style>
        * {
            margin: 0;
            padding: 0;
            list-style-type: none;
            text-decoration: none;
        }

        li {
            border: 1px solid black;
            padding: 10px;
        }
        
        li:hover{
            background-color: pink;
            transition: all 1s ease;
        }

        .v-enter,
        .v-leave-to {
            transform: translateY(150px);
            opacity: 0;
        }

        .v-enter-active,
        .v-leave-active {
            transition: all 1s ease;
        }
    </style>
    <div id="app">
        <label for="">
            id:
            <input type="text" name="" id="" v-model="id">
        </label>
        <label for="">
            name:
            <input type="text" name="" id="" v-model="name">
        </label>
        <input type="button" value="提交" @click="add">
        <ul>
          //在实现列表过渡的时候，如果需要过渡的元素，是通过 v-for 循环 渲染出来的，不能使用transition 包裹 ，需要使用transitionGroup
            //如果要为v-for 循环创建的元素设置动画，必须为每一个元素设置 key 属性
            <transition-group>
                <li v-for="item in list" :key="item.id">
                    id：{{item.id}} name:{{item.name}}
                </li>
            </transition-group>   
        </ul>
    </div>

    <script>
        var vm = new Vue({
            el: '#app',
            data: {
                list: [
                    { id: '1', name: 'hwl' },
                    { id: '2', name: 'hwq' },
                    { id: '3', name: 'hz' },
                    { id: '4', name: 'ljf' }
                ]
            },
            methods: {
                add() {
                    this.list.push({ id: this.id, name: this.name })
                    this.name = this.id = ''
                }
            }
        });
    </script>
```



### 实现transition-group元素实例

```html

```



### 实现列表删除和删除实例

```html
<style>
        * {
            margin: 0;
            padding: 0;
            list-style-type: none;
            text-decoration: none;
        }

        li {
            width: 100%;
            border: 1px solid black;
            padding: 10px;
        }
        
        li:hover{
            background-color: pink;
            transition: all 1s ease;
        }

        .v-enter,
        .v-leave-to {
            transform: translateY(150px);
            opacity: 0;
        }

        .v-enter-active,
        .v-leave-active {
            transition: all 1s ease;
        }
		// v-move和 .v-leaver-active配合使用，能够实现列表后续的元素，渐渐地飘上来的效果
        .v-move{
            transition: all 1s ease;
        }
        .v-leave-active {
            position: absolute;
        }
    </style>
    <div id="app">
        <label for="">
            id:
            <input type="text" name="" id="" v-model="id">
        </label>
        <label for="">
            name:
            <input type="text" name="" id="" v-model="name">
        </label>
        <input type="button" value="提交" @click="add">
        <ul>
            <transition-group>
                <li v-for="(item,index) in list" :key="item.id" @click="del(index)">
                    id：{{item.id}} name:{{item.name}}
                </li>
            </transition-group>   
        </ul>
    </div>

    <script>
        var vm = new Vue({
            el: '#app',
            data: {
                list: [
                    { id: '1', name: 'hwl' },
                    { id: '2', name: 'hwq' },
                    { id: '3', name: 'hz' },
                    { id: '4', name: 'ljf' }
                ]
            },
            methods: {
                add() {
                    this.list.push({ id: this.id, name: this.name })
                    this.name = this.id = ''
                },
                del(index){
                    this.list.splice(index,1)
                }
            }
        });
    </script>
```



### trasition-group 中appear

```html
// 给trasition-group 添加appear属性，实现页面展示出来时候，入场时候的效果  
同岗位transition-group元素，设置tag属性，指定transition-group渲染为指定的元素，如果不指定tag属性，默认，渲染为span 标签
//<ul>
<transition-group appear tag="ul">
                <li v-for="(item,index) in list" :key="item.id" @click="del(index)">
                    id：{{item.id}} name:{{item.name}}
                </li>
            </transition-group>  
//</ul>
```



### [使用第三方 CSS 动画库](https://cn.vuejs.org/v2/guide/transitions.html#自定义过渡类名)

1. 导入动画类库：

```html
<link rel="stylesheet" type="text/css" href="./lib/animate.css">
```

2. 定义 transition 及属性：

```html
<transition
	enter-active-class="fadeInRight"
    leave-active-class="fadeOutRight"
    :duration="{ enter: 500, leave: 800 }">
  	<div class="animated" v-show="isshow">动画哦</div>
</transition>
```

### 使用动画钩子函数

1. 定义 transition 组件以及三个钩子函数：

```html
<div id="app">
    <input type="button" value="切换动画" @click="isshow = !isshow">
    <transition
    @before-enter="beforeEnter"
    @enter="enter"
    @after-enter="afterEnter">
      <div v-if="isshow" class="show">OK</div>
    </transition>
  </div>
```

2. 定义三个 methods 钩子方法：

```html
methods: {
        beforeEnter(el) { // 动画进入之前的回调
          el.style.transform = 'translateX(500px)';
        },
        enter(el, done) { // 动画进入完成时候的回调
          el.offsetWidth;
          el.style.transform = 'translateX(0px)';
          done();
        },
        afterEnter(el) { // 动画进入完成之后的回调
          this.isshow = !this.isshow;
        }
}
```

3. 定义动画过渡时长和样式：

```
.show{
      transition: all 0.4s ease;
}
```

### [v-for 的列表过渡](https://cn.vuejs.org/v2/guide/transitions.html#列表的进入和离开过渡)

1. 定义过渡样式：

```
<style>
    .list-enter,
    .list-leave-to {
      opacity: 0;
      transform: translateY(10px);
    }

    .list-enter-active,
    .list-leave-active {
      transition: all 0.3s ease;
    }
</style>
```

2. 定义 DOM 结构，其中，需要使用 transition-group 组件把 v-for 循环的列表包裹起来：

```
  <div id="app">
    <input type="text" v-model="txt" @keyup.enter="add">

    <transition-group tag="ul" name="list">
      <li v-for="(item, i) in list" :key="i">{{item}}</li>
    </transition-group>
  </div>
```

3. 定义 VM 中的结构：

```
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        txt: '',
        list: [1, 2, 3, 4]
      },
      methods: {
        add() {
          this.list.push(this.txt);
          this.txt = '';
        }
      }
    });
```

### 列表的排序过渡

`<transition-group>` 组件还有一个特殊之处。不仅可以进入和离开动画，**还可以改变定位**。要使用这个新功能只需了解新增的 `v-move` 特性，**它会在元素的改变定位的过程中应用**。

- `v-move` 和 `v-leave-active` 结合使用，能够让列表的过渡更加平缓柔和：

```
.v-move{
  transition: all 0.8s ease;
}
.v-leave-active{
  position: absolute;
}
```









## 组件

### 组件的定义&&组件化和模块化的区别

什么是组件： 组件的出现，就是为了拆分 Vue 实例的代码量的，能够让我们以不同的组件，来划分不同的功能模块，将来我们需要什么样的功能，就可以去调用对应的组件即可；
组件化和模块化的不同：

- 模块化： 是从代码逻辑的角度进行划分的；方便代码分层开发，保证每个功能模块的职能单一；
- 组件化： 是从 UI 界面的角度进行划分的；前端的组件化，方便 UI 组件的重用；

###  组件的复用

####  概念

 组件是可复用的 Vue 实例对象
​ 每用一次组件，就会有一个它的新实例被创建。

```html
data// 必须是一个函数
data: function () {
    return {
     count: 0
    }
}
```

 一个组件的 data 选项必须是一个函数，因此每个实例可以维护一份被返回对象的独立的拷贝
​ 组件的组织
​ 概念
​ 一个应用会以一棵嵌套的组件树的形式来组织
​ 为了能在模板中使用，这些组件必须先注册以便 Vue 能够识别。这里有两种组件的注册类型：全局注册和局部注册。

```html
Vue.component('my-component-name', {
// ... options ...
})
```

### 全局组件定义的三种方式

1. 使用 Vue.extend 配合 Vue.component 方法：

```html
<login></login>
<lo-gin></lo-gin>
<script>
var logins = Vue.extend({
      template: '<h1>登录</h1>'
});
Vue.component('login', logins);
Vue.component('loGin', logins);
// 如果使用Vue.component 定义全局组件的时候，组件名称使用了驼峰命名,则在引用组件的时候，需要吧 大写的驼峰改为小写的字母，同时，两个单词之前，使用 - 链接;
</script>
```

2. 直接使用 Vue.component 方法：

```html
<script>
//Vue.component 第一个参数：组件的名称，将来在引入之间的时候，就是一个标签形式来引入它的
第二个参数：Vue.extend创建的组件，其中template 就是组件将来要展示的HTML内容
Vue.component('register', Vue.extend({
      template: '<h1>注册</h1>'
 }));
// 注意：不论是那种方式创建出来的组件，组件的template属性指向的模板内容，必须有且只能有唯一的一个根元素
Vue.component('register', {
	template: '<div><h1>注册</h1><span>spna</span></div>'
 });
</script>
```

3. 将模板字符串，定义到 script 标签中：

```html
// JS中
<script id="tmpl" type="x-template">
    <div><a href="#">登录</a> | <a href="#">注册</a></div>
</script>

<script>
    Vue.component('account', {
        template: '#tpl'
    });
</script>
```

4. 将模板字符串，定义到HTML中：

```html
<div id="app">
    <account></account>
</div>
// HTML中
<template id="tpl">
	<div>
        <h1>这是通过template元素,在定义</h1>
    	<h4>这是一个或</h4>
    </div>
</template>

<script>
    Vue.component('account', {
        template: '#tpl'
    });
</script>
```

> 注意： 组件中的 DOM 结构，有且只能有唯一的根元素（Root Element）来进行包裹！

### 使用components定义私有组

```html
<div id="app">
    <login></login> //不能再这里使用
</div>

<div id="app2">
    <login></login> // components 定义了私有组 
</div>

<template id="tpl2">
	<div>
        <h1>
            this is a h1
        </h1>
         <h1>
            this is a h1
        </h1>
    </div>
</template>

<script>
    var vm2 = new Vue({
    el: '#app2',
    data:{},
    methods:{},
    filters:{},
    directives:{},
    components:{
        login:{
            template:'#tpl2'
        }
    },
    beforeCreate(){},
    created(){},
    beforeMount(){},
    mounted(){},
    beforenUpdate(){},
    updated(){},
    beforeDestory(){},
    destoryed(){}
    })
</script>
```

### 组件计时器

```html
  <div id="commponts-demo">
        <button-counter></button-counter>
        <button-counter></button-counter>
        <button-counter></button-counter>
    </div>
    <div id="calc-demo">
        <btn></btn>
        <btn></btn>
        <btn></btn>
    </div>
    <template id="tpl">
        <div>
            <button @click="add">You clicked me {{ count2 }} times.</button>
            <h3>{{count2}}</h3>
        </div>
    </template>
    <script>
        Vue.component("button-counter", {
            data: function () {
                return {
                    count: 0,
                };
            },
            template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>',
        });
        Vue.component("btn", {
            template: '#tpl',
            data: function () {
                return {
                    count2: 0
                };
            },
            methods: {
                add() {
                    this.count2++
                }
            }
        })
        new Vue({
            el: "#commponts-demo",
        });
        new Vue({
            el: "#calc-demo",
        });
    </script>
```



### 组件中展示数据和响应事件

1. 在组件中，`data`需要被定义为一个方法，例如：

```html
//1.组件可以有自已的data数据
2.组件的data 和实例的data 有点不一样，实例中的data可以为一个对象，但是组件中的data必须是一个方法
3.组件中的data除了必须为一个方法之外，这个方法的内部，还必须返回一个对象才行;
4.组件中的data数据，使用方式，和实例中的data 使用方式完全一样

<script>
Vue.component('mycom',{
    template: '<h1>这是一个data</h1>',
    data:function(){
        return{
            msg: 'this a msg'
        }
    }
})    
    
Vue.component('account', {
      template: '#tmpl',
      data() {
        return {
          msg: '大家好！'
        }
      },
      methods:{
        login(){
          alert('点击了登录按钮');
        }
      }
});
</script>
```

2. 在子组件中，如果将模板字符串，定义到了 script 标签中，那么，要访问子组件身上的`data`属性中的值，需要使用`this`来访问；

### 【重点】为什么组件中的 data 属性必须定义为一个方法并返回一个对象

1. 通过计数器案例演示

```html
<div id="app">
    <btn></btn>
    <btn></btn>
    <btn></btn>
</div>
<template id="tpl">
    <div>
        <button @click="counter">点击{{count}}次数</button>
        <h2>{{count}}</h2>
    </div>
</template>
<script>
    Vue.component('btn', {
        template: '#tpl',
        data: function () {
            return { count: 0 }
        },
        methods: {
            counter() {
                this.count++;
            }
        }
    })

    var vm = new Vue({
        el: '#app',
        data: {

        },
        methods: {

        }
    });
</script>
```



### 使用`components`属性定义局部子组件

1. 组件实例定义方式：

```
<script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {},
      components: { // 定义子组件
        account: { // account 组件
          template: '<div><h1>这是Account组件{{name}}</h1><login></login></div>', // 在这里使用定义的子组件
          components: { // 定义子组件的子组件
            login: { // login 组件
              template: "<h3>这是登录组件</h3>"
            }
          }
        }
      }
    });
  </script>
```

2. 引用组件：

```
<div id="app">
    <account></account>
</div>
```

### 使用`flag`标识符结合`v-if`和`v-else`切换组件

1. 页面结构：

```
<div id="app">
    <input type="button" value="toggle" @click="flag=!flag">
    <my-com1 v-if="flag"></my-com1>
    <my-com2 v-else="flag"></my-com2>
  </div>
```

2. Vue 实例定义：

```
<script>
    Vue.component('myCom1', {
      template: '<h3>奔波霸</h3>'
    })

    Vue.component('myCom2', {
      template: '<h3>霸波奔</h3>'
    })

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        flag: true
      },
      methods: {}
    });
  </script>
  
   <div id="app">
        <a href="" @click.prevent="flag=true">登陆</a>
        <a href="" @click.prevent="flag=false">注册</a>
        <login v-if="flag"></login>
        <reg v-else="flag"></reg>
    </div>

    <script>
        Vue.component('login', {
            template: '<h1>登陆页面</h1>'
        })
        Vue.component('reg', {
            template: '<h1>注册页面</h1>'
        })
        var vm = new Vue({
            el: '#app',
            data: {
                flag:true
            },
            methods: {

            }
        });
    </script>
```

### 使用`:is`属性来切换不同的子组件,并添加切换动画

支持多个切换

1. 组件实例定义方式：

```
  // 登录组件
    const login = Vue.extend({
      template: `<div>
        <h3>登录组件</h3>
      </div>`
    });
    Vue.component('login', login);

    // 注册组件
    const register = Vue.extend({
      template: `<div>
        <h3>注册组件</h3>
      </div>`
    });
    Vue.component('register', register);

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: { comName: 'login' },
      methods: {}
    });
```

2. 使用`component`标签，来引用组件，并通过`:is`属性来指定要加载的组件：

```html
<div id="app">
    <a href="#" @click.prevent="comName='login'">登录</a>
    <a href="#" @click.prevent="comName='register'">注册</a>
    <hr>
    // 通过mode 属性，设置组件切换时候的模式
    <transition mode="out-in">
    // component是一个占位符，：is属性，可以用来指定要展示的组件的名称
      <component :is="comName"></component>
    </transition>
  </div>
```

3. 添加切换样式：

```css
<style>
.v-enter,
.v-leave-to {
    opacity: 0;
    transform: translateX(30px);
}

.v-enter-active,
.v-leave-active {
    position: absolute;
    transition: all 0.3s ease;
}
  
h3{
    margin: 0;
}
</style>
```

component 

```
var login = {
 	template:'<h1>hello</h1>'
}

var vm = new Vue({
	el:'#app',
	data:{},
	methods:{},
	components:{
		login// login:'login'
		// mylogin:'login '
	}
})
```



### 父组件向子组件传值

子组件中，默认无法访问到父组件中的data上的数据和methods 中的方法

1. 组件实例定义方式，注意：一定要使用`props`属性来定义父组件传递过来的数据

```
<script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        msg: '这是父组件中的消息'
      },
      components: {
        son: {
       	 // 子组件中的data数据，并不是通过父组件传递过来的，而是子组件自身私有的，比如：子组件通过AJax请求回来的数据，都可以放在data身上 data上的数据可读可写的
         data(){
       	  	return {
       	  	
       	  	}
       	  }
          template: '<h1>这是子组件 --- {{finfo}}</h1>',
        // props 中的数据都是只读的，无法重新赋值 
        props: ['finfo']，
        directives:{},
        filters:{},
        components:{},
      
        } 
      }
    });
  </script>
```

2. 使用`v-bind`或简化指令，将数据传递到子组件中：

```
<div id="app">
    <son :finfo="msg"></son>
  </div>
```

### 子组件向父组件传值

1. 原理：父组件将方法的引用，传递到子组件内部，子组件在内部调用父组件传递过来的方法，同时把要发送给父组件的数据，在调用方法的时候当作参数传递进去；
2. 父组件将方法的引用传递给子组件，其中，`getMsg`是父组件中`methods`中定义的方法名称，`func`是子组件调用传递过来方法时候的方法名称

```
<son @func="getMsg"></son>
```

3. 子组件内部通过`this.$emit('方法名', 要传递的数据)`方式，来调用父组件中的方法，同时把数据传递给父组件使用

```
<div id="app">
    <!-- 引用父组件 -->
    <son @func="getMsg"></son>

    <!-- 组件模板定义 -->
    <script type="x-template" id="son">
      <div>
        <input type="button" value="向父组件传值" @click="sendMsg" />
      </div>
    </script>
  </div>

  <script>
    // 子组件的定义方式
    Vue.component('son', {
      template: '#son', // 组件模板Id
      methods: {
        sendMsg() { // 按钮的点击事件
          this.$emit('func', 'OK'); // 调用父组件传递过来的方法，同时把数据传递出去
        }
      }
    });

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {
        getMsg(val){ // 子组件中，通过 this.$emit() 实际调用的方法，在此进行定义
          alert(val);
        }
      }
    });
  </script>
```

### 评论列表案例

目标：主要练习父子组件之间传值

### 使用 `this.$refs` 来获取元素和组件

```
  <div id="app">
    <div>
      <input type="button" value="获取元素内容" @click="getElement" />
      <!-- 使用 ref 获取元素 -->
      <h1 ref="myh1">这是一个大大的H1</h1>

      <hr>
      <!-- 使用 ref 获取子组件 -->
      <my-com ref="mycom"></my-com>
    </div>
  </div>

  <script>
    Vue.component('my-com', {
      template: '<h5>这是一个子组件</h5>',
      data() {
        return {
          name: '子组件'
        }
      }
    });

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {
        getElement() {
          // 通过 this.$refs 来获取元素
          console.log(this.$refs.myh1.innerText);
          // 通过 this.$refs 来获取组件
          console.log(this.$refs.mycom.name);
        }
      }
    });
  </script>
```

## 插件

### vue-router 

[Vue Router](https://router.vuejs.org/zh/)

#### 路由的概念

- 后端路由：对于普通的网站，所有的超链接都是 URL 地址，所有的 URL 地址都对应服务器上对应的资源；
- 前端路由：对于单页面应用程序来说，主要通过 URL 中的 hash(#号)来实现不同页面之间的切换，同时，hash 有一个特点：HTTP 请求中不会包含 hash 相关的内容；所以，单页面程序中的页面跳转主要用 hash 实现；（前端当前页面的跳转）
- 在单页面应用程序中，这种通过 hash 改变来切换页面的方式，称作前端路由（区别于后端路由）；

#### 安装

CDN

```html
<script src="https://cdn.bootcdn.net/ajax/libs/vue/2.6.11/vue.common.dev.js"></script>
<script src="https://cdn.bootcdn.net/ajax/libs/vue-router/3.1.3/vue-router.common.js"></script>
// vue-router 依赖于vue
```

NPM webpack构建vue项目

```bash
npm install vue-router

import Vue from 'vue'
import VueRouter from 'vue-router'

Vue.use(VueRouter)
```

#### 使用 vue-router

1. 导入 vue-router 组件类库：

```html
<!-- 1. 导入 vue-router 组件类库 -->
<script src="./lib/vue-router-2.7.0.js"></script>
```

2. 使用 router-link 组件来导航

```html
<a href="#/login">登陆</a>
<a href="#/register">注册</a>
替换上面的写法
<!-- 2. 使用 router-link 组件来导航 -->  
默认渲染一个a标签 ，自定义标签 使用tag 属性
<router-link to="/login" tag="span">登录</router-link>

<router-link to="/login">登录</router-link>
<router-link to="/register">注册</router-link>
```

3. 使用 router-view 组件来显示匹配到的组件

```html
<!-- 3. 使用 router-view 组件来显示匹配到的组件 -->
html中要放容器
这是vue-router提供的元素，专门用来当作占位符的，将来，路由规则，配到的组件，就会展示到这个router-view 中去
所以：我们可以把router-view 认为是一 个占位符
<router-view></router-view>
```

4. 创建使用`Vue.extend`创建组件

```js
// 4.1 使用 Vue.extend 来创建登录组件
// 组件的模板对象
var login = Vue.extend({
	template: '<h1>登录组件</h1>'
});
// 4.2 使用 Vue.extend 来创建注册组件
var register = Vue.extend({
	template: '<h1>注册组件</h1>'
});
```

5. 创建一个路由 router 实例，通过 routers 属性来定义路由匹配规则

```js
//创建一个路由对象，当导入vue-router 包之后，在 window全局对象中，就有了一个路由的构造函数，VueRouter
var router = new VueRouter({
    // route 这个配置对象 中的route 表示路由匹配规则 的意思
    //每个路由规则,都是一个对象,这个规则对象,身上,有两个必须的属性:
//属性1是path,表示监听哪个路由链接地址;
//属性2是component, 表示,如果路由是前面匹配到的path ,则展示component属性对应的那个组件   
// 注意：component 属性值，必须是一个 组件的模板对象，不能是 组件的引用名称   
    routes: [
        { path: '/', redirect:'/login' },
        // 默认根路径 的访问组件
        // 这里的redirect 和 Node 中的redirect 不一样
        { path: '/login', component: login },
        { path: '/register', component: register }
    ]
    //  component 不要忘记
});
```

6. 使用 router 属性来使用路由规则

```js
// 6. 创建 Vue 实例，得到 ViewModel
var vm = new Vue({

    el: '#app',
    router：router // 使用 router 属性来使用路由规则 

});
```

路由重定向的使用

```js
路由器重定向的使用
{ path: '/', redirect:'/login' }, 
routes: [
        { path: '/', redirect:'/login' },
        // 默认根路径 的访问组件
        // 这里的redirect 和 Node 中的redirect 不一样
        { path: '/login', component: login },
        { path: '/register', component: register }
]
```

设置路由高亮的两种方法

```css
// Vue默认的类名
.router-link-active{
	color:red;
    // 设置路由选中时的样式状态
}

var router = new VueRouter({
    routes: [
        { path: '/', redirect:'/login' },
        { path: '/login', component: login },
        { path: '/register', component: register }
    ]，
    linkActiveClass  :'myactive'
    //  component 不要忘记
});

.myactive{
	color:red;
    // 设置路由选中时的样式状态
}

```

为路由切换启动动画

```css
动画两组类
// mode 过渡的模式
<transition mode="out-in">
	<router-view></router-view>
</transition>

.v-enter,.v-leave-to{
	opacity:0;
    transform:translateX(140px);
}
.v-enter-active,.v-leave-active{
	transtion:all 0.5 ease;
}
```

使用jQuery方式传递参数 $route.query  ? query

```js
如果在路由中，使用查询字符串，给路由传递参数，则不需要修改
<router-link to="/logi？id=10">登录</router-link>
<router-link to="/register？id=10&name=zs">注册</router-link>
var login = {
	template :'<h1>login -- {{ this.$route.query.id }}  --- {{ $route.query.name }}</h1>'
	// 测试
	created(){
		console.log(this.$route.query)
	}
}

query: {id: "1830315", name: "hwl"}
```

使用params 方式传递路径  参数 

```js
<router-link to="/login/12/hwl">登录</router-link>
<router-link to="/register/id10/namezs">注册</router-link>
var login = {
	template :'<h1>login -- {{ this.$route.params.id }}  --- {{ $route.params.name }}</h1>'
	// 测试
	created(){
		console.log(this.$route.params)
	}
}

var router = new VueRouter({
    routes: [
        { path: '/', redirect:'/login' },
        { path: '/login/:id/:name', component: login },
        { path: '/register', component: register }
    ]，
    linkActiveClass:'myactive'
    //  component 不要忘记
});
```

1. 在规则中定义参数：

```js
{ path: '/register/:id', component: register }
```

2. 通过 `this.$route.params`来获取路由中的参数：

```js
var register = Vue.extend({
	template: '<h1>注册组件 --- {{this.$route.params.id}}</h1>'
});
```

params 方式传递路径 jQuery方式传递参数

```
<router-link to="login?id=1830315&name=hwl">login</router-link>
  { path: '/login', component: login },
  template: '<h1>login---{{ $route.query.name }} --- {{ $route.query.id }}</h1>',

 <router-link to="/login/12/i233d">login</router-link>
   { path: '/login/:id/:name', component: login }
 template: '<h1>login--- {{$route.params.name}} --- {{$route.params.id}} </h1>'
```

使用 `children` 属性实现路由嵌套

```html
<div id="app">
    <router-link to="/account">Account</router-link>
    <router-view></router-view>
</div>

<script>
    // 父路由中的组件
    const account = Vue.extend({
      template: `<div>
        这是account组件
        <router-link to="/account/login">login</router-link> |
        <router-link to="/account/register">register</router-link>
        <router-view></router-view>
      </div>`
    });

    // 子路由中的 login 组件
    const login = Vue.extend({
      template: '<div>登录组件</div>'
    });

    // 子路由中的 register 组件
    const register = Vue.extend({
      template: '<div>注册组件</div>'
    });

    // 路由实例
    var router = new VueRouter({
      routes: [
        { path: '/', redirect: '/account/login' }, // 使用 redirect 实现路由重定向
        {
          path: '/account',
          component: account,
            // 使用children 属性 实现子路由的path前面，不要带 / 否则 永远以根路径开始请求，这样不方便用户去理解URL地址
          children: [ // 通过 children 数组属性，来实现路由的嵌套
            { path: 'login', component: login }, // 注意，子路由的开头位置，不要加 / 路径符
            { path: 'register', component: register }
          ]
        }
      ]
    });

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {},
      components: {
        account
      },
      router: router
    });
 </script>


  <div id="app">
        <router-link to="/account">Account</router-link>
        <router-view></router-view>
    </div>
    <template id="tmpl">
        <div>
            <h1>这是Account组件</h1>
            <router-link to="/account/login">login</router-link>
            <router-link to="/account/register">register</router-link>
            <router-view></router-view>
        </div>
    </template>
    <script>
        var account = {
            template: '#tmpl'
        }

        var login = {
            template: '<h3>login</h3>'
        }

        var register = {
            template: '<h3>register</h3>'
        }

        var router = new VueRouter({
            routes: [
                {
                    path: '/account', component: account,
                    children: [
                        //使用children属性，实现子路由，同时，子路由的path前面，不要带/，否则永远以根路径开始请求，这样不方便我们用户去理解URL地址

                        { path: 'login', component: login },
                        { path: 'register', component: register }
                    ]
                }
            ]
        })

        var vm = new Vue({
            el: '#app',
            data: {

            },
            methods: {

            },
            router
        });
    </script>
```

命名视图实现经典布局 同一路由 多个组件

```js
<style>
    .header {
        border: 1px solid red;
    }

    .content{
        display: flex;
    }
    .sidebar {
        flex: 2;
        border: 1px solid green;
        height: 500px;
    }
    .mainbox{
        flex: 8;
        border: 1px solid blue;
        height: 500px;
    }
</style>
<div id="app">
    <router-view></router-view>
    <div class="content">
      <router-view name="a"></router-view>
      <router-view name="b"></router-view>
    </div>
  </div>
<script>
    var header = Vue.component('header', {
      template: '<div class="header">header</div>'
    });

    var sidebar = Vue.component('sidebar', {
      template: '<div class="sidebar">sidebar</div>'
    });

    var mainbox = Vue.component('mainbox', {
      template: '<div class="mainbox">mainbox</div>'
    });

    // 创建路由对象
    var router = new VueRouter({
      routes: [
        {
            //{ path: 'login', component: login }
            // componet -> components:{ 'default: 'header,} router-view 添加 name 属性值 
          path: '/', components: {
            default: header,
            a: sidebar,
            b: mainbox
          }
        }
      ]
    });

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {},
      router
    });
 </script>
```

父子组件传值

```
  <div id="app">
        <son v-bind:parmsg="msg" @func="getMessage"></son>
    </div>
    <template id="tpl">
        <div>
            <h1>this is a {{parmsg}}</h1>
            <input type="button" value="向父组件传递参数" @click="sendMessage">
        </div>
    </template>
    <script>
        var son = {
            template: '#tpl',
            data() {
                return {
                    sonmsg: '我是子组件的消息'
                }
            },
            methods: {
                sendMessage() {
                    this.$emit('func',this.sonmsg);
                }
            },
            props: ['parmsg']
        }
        var vm = new Vue({
            el: '#app',
            data: {
                msg: 'message',
                newmeg: ''
            },
            methods: {
                getMessage(data) {
                    this.newmeg = data
                    console.log(this.newmeg)
                }
            },
            components: {
                son
            }
        });
    </script>
```

父组件 -》子组件



父组件 《  -子组件



keyup

```html
<input type="text" name="" id="" v-model="firstname" @keyup="getFullName">+
        <input type="text" name="" id="" v-model="lastname" @keyup="getFullName">=
        <input type="text" name="" id="" v-model="fullname" @keyup="getFullName">
```





`watch`属性的使用

考虑一个问题：想要实现 `名` 和 `姓` 两个文本框的内容改变，则全名的文本框中的值也跟着改变；（用以前的知识如何实现？？？）

1. 监听`data`中属性的改变：

```
<div id="app">
    <input type="text" v-model="firstName"> +
    <input type="text" v-model="lastName"> =
    <span>{{fullName}}</span>
  </div>

  <script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        firstName: 'jack',
        lastName: 'chen',
        fullName: 'jack - chen'
      },
      methods: {},
//使用这个属性，可以监视data 中指定数据的变化，然后触发这个watch 中对应的function处理函数
      watch: {
        'firstName': function (newVal, oldVal) { // 第一个参数是新数据，第二个参数是旧数据
          this.fullName = newVal + ' - ' + this.lastName;
        },
        'lastName': function (newVal, oldVal) {
          this.fullName = this.firstName + ' - ' + newVal;
        }
      }
    });
  </script>
  
  v-model=""
  watch:{
  	'':function(newVal,oldVal){
  	
  	}
  }
  
```

2. 监听路由对象的改变：

```html
<div id="app">
    <router-link to="/login">登录</router-link>
    <router-link to="/register">注册</router-link>

    <router-view></router-view>
  </div>

  <script>
    var login = Vue.extend({
      template: '<h1>登录组件</h1>'
    });

    var register = Vue.extend({
      template: '<h1>注册组件</h1>'
    });

    var router = new VueRouter({
      routes: [
        { path: "/login", component: login },
        { path: "/register", component: register }
      ]
    });

    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {},
      methods: {},
      router: router,
      watch: {
        '$route': function (newVal, oldVal) {
          if (newVal.path === '/login') {
            console.log('这是登录组件');
          } else if (newVal.path === '/register') {
                        console.log('这是注册组件');
                    }
        }
          
         
      }
    });
  </script>



'$route.path': function (newVal, oldVal) {
          if (newVal === '/login') {
            console.log('这是登录组件');
          }
 else if (newVal === '/register') {
                        console.log('这是注册组件');
                    } 
        }
```

`computed`计算属性的使用

1. 默认只有`getter`的计算属性：

```html
<div id="app">
    <input type="text" v-model="firstName"> +
    <input type="text" v-model="lastName"> =
    <span>{{fullName}}</span>
  </div>

  <script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        firstName: 'jack',
        lastName: 'chen'
      },
      methods: {},
//在computed 中，可以定义-些属性这些属性，叫做[计算属性]，计算属性的，本质，就是一个方法，只不过，我们在使用这些计算属性的时候，是把它们的名称，直接当作属性来使用的；并不会把计算属性，当作方法去调用；       
      computed: { // 计算属性； 特点：当计算属性中所以来的任何一个 data 属性改变之后，都会重新触发 本计算属性 的重新计算，从而更新 fullName 的值

 //注意：计算属性，在引用的时候，一定不要加（）去调用，直接把它当作普通属性去使用就好了；
//注意：只要计算属性，这个function 内部，所用到的任何data 中的数据发送了变化，就会立即重新计算这个计算属性的值   
//注意3：计算属性的求值结果4会被缓存起来，方便下次直接使用：如果计算属性方法中，所以来的任何数据，都没有发生过变化，则，不会重新对计算属性求值；          
          
        fullName() {//'fullName':function()
          return this.firstName + ' - ' + this.lastName;
        }
      }
    });
  </script>
```

2. 定义有`getter`和`setter`的计算属性：

```html
<div id="app">
    <input type="text" v-model="firstName">
    <input type="text" v-model="lastName">
    <!-- 点击按钮重新为 计算属性 fullName 赋值 -->
    <input type="button" value="修改fullName" @click="changeName">

    <span>{{fullName}}</span>
  </div>

  <script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        firstName: 'jack',
        lastName: 'chen'
      },
      methods: {
        changeName() {
          this.fullName = 'TOM - chen2';
        }
      },
      computed: {
        fullName: {
          get: function () {
            return this.firstName + ' - ' + this.lastName;
          },
          set: function (newVal) {
            var parts = newVal.split(' - ');
            this.firstName = parts[0];
            this.lastName = parts[1];
          }
        }
      }
    });
  </script>
```

`watch`、`computed`和`methods`之间的对比

1. `computed`属性的结果会被缓存，除非依赖的响应式属性变化才会重新计算。主要当作属性来使用；
2. `methods`方法表示一个具体的操作，主要书写业务逻辑；
3. `watch`一个对象，键是需要观察的表达式，值是对应回调函数。主要用来监听某些特定数据的变化，从而进行某些具体的业务逻辑操作；可以看作是`computed`和`methods`的结合体；

4.

1)

在 vue 组件页面中，集成 vue-router 路由模块

[vue-router 官网](https://router.vuejs.org/)

1. 导入路由模块：

```js
import VueRouter from 'vue-router'
```

2. 安装路由模块：

```js
Vue.use(VueRouter);
```

3. 导入需要展示的组件:

```js
import login from './components/account/login.vue'
import register from './components/account/register.vue'
```

4. 创建路由对象:

```js
var router = new VueRouter({
  routes: [
    { path: '/', redirect: '/login' },
    { path: '/login', component: login },
    { path: '/register', component: register }
  ]
});
```

5. 将路由对象，挂载到 Vue 实例上:

```js
var vm = new Vue({
  el: '#app',
  // render: c => { return c(App) }
  render(c) {
    return c(App);
  },
  router // 将路由对象，挂载到 Vue 实例上
});
```

6. 改造 App.vue 组件，在 template 中，添加`router-link`和`router-view`：

```js
<router-link to="/login">登录</router-link>
<router-link to="/register">注册</router-link>
<router-view></router-view>
```

### vue-resource 

实现 get, post, jsonp 请求

The HTTP client for Vue.js

 https://github.com/pagekit/vue-resource

```html
yarn add vue-resource
npm install vue-resource
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
< script src="https://cdn.bootcdn.net/ajax/libs/vue-resource/1.5.1/vue-resource.js"></script>
```

除了 vue-resource 之外，还可以使用 `axios` 的``第三方包``实现实现数据的请求

1. 之前的学习中，如何发起数据请求？
2. 常见的数据请求类型？ get post jsonp
3. 测试的 URL 请求资源地址：

- get 请求地址： http://vue.studyit.io/api/getlunbo
- post 请求地址：http://vue.studyit.io/api/post
- jsonp 请求地址：http://vue.studyit.io/api/jsonp

```html
<div id="app">
    <input type="button" value="get请求" @click="getInfo">
    <input type="button" value="post请求" @click="postInfo">
    <input type="button" value="jsonp请求" @click="jsonpInfo">
</div>

<script>
    var vm = new Vue({
        el: '#app',
        data: {

        },
        methods: {
            getInfo() { // 发起get请求
                this.$http.get('http://vue.studyit.io/api/getlunbo').then(function (result) {
                    console.log(result)
                })
            },
            postInfo() { // 发起post请求 表单 application/x-www-form-urlencoded 手动发起的post请求，默认没有表单格式，所以，有的服务器处理不了
                // 通过post方法的第三个参数，{ emulateJSON: true } 设置提交的内容类型为普通表单数据格式
                this.$http.post('http://vue.studyit.io/api/post', {}, { emulateJSON: true }).then(result => {
                    console.log(result)
                })
            },
            jsonpInfo() { //发起jsonp请求
                this.$http.jsonp('http://vue.studyit.io/api/jsonp').then(result => {
                    console.log(result.body)
                })
            }
        }
    });
</script>
```



4. JSONP 的实现原理

- 由于浏览器的安全性限制，不允许 AJAX 访问 协议不同、域名不同、端口号不同的 数据接口，浏览器认为这种访问不安全；
- 可以通过动态创建 script 标签的形式，把 script 标签的 src 属性，指向数据接口的地址，因为 script 标签不存在跨域限制，这种数据获取方式，称作 JSONP（注意：根据 JSONP 的实现原理，知晓，JSONP 只支持 Get 请求）；
- 具体实现过程：

* 先在客户端定义一个回调方法，预定义对数据的操作；
* 再把这个回调方法的名称，通过 URL 传参的形式，提交到服务器的数据接口；
* 服务器数据接口组织好要发送给客户端的数据，再拿着客户端传递过来的回调方法名称，拼接出一个调用这个方法的字符串，发送给客户端去解析执行；
* 客户端拿到服务器返回的字符串之后，当作 Script 脚本去解析执行，这样就能够拿到 JSONP 的数据了；

- 带大家通过 Node.js ，来手动实现一个 JSONP 的请求例子；

```js
   const http = require('http');
   // 导入解析 URL 地址的核心模块
   const urlModule = require('url');

   const server = http.createServer();
   // 监听 服务器的 request 请求事件，处理每个请求
   server.on('request', (req, res) => {
     const url = req.url;

     // 解析客户端请求的URL地址
     var info = urlModule.parse(url, true);

     // 如果请求的 URL 地址是 /getjsonp ，则表示要获取JSONP类型的数据
     if (info.pathname === '/getjsonp') {
       // 获取客户端指定的回调函数的名称
       var cbName = info.query.callback;
       // 手动拼接要返回给客户端的数据对象
       var data = {
         name: 'zs',
         age: 22,
         gender: '男',
         hobby: ['吃饭', '睡觉', '运动']
       }
       // 拼接出一个方法的调用，在调用这个方法的时候，把要发送给客户端的数据，序列化为字符串，作为参数传递给这个调用的方法：
       var result = `${cbName}(${JSON.stringify(data)})`;
       // 将拼接好的方法的调用，返回给客户端去解析执行
       res.end(result);
     } else {
       res.end('404');
     }
   });

   server.listen(3000, () => {
     console.log('server running at http://127.0.0.1:3000');
   });
```

5. vue-resource 的配置步骤：

- 直接在页面中，通过`script`标签，引入 `vue-resource` 的脚本文件；
- 注意：引用的先后顺序是：先引用 `Vue` 的脚本文件，再引用 `vue-resource` 的脚本文件；

6. 发送 get 请求：

```js
getInfo() { // get 方式获取数据
  this.$http.get('http://127.0.0.1:8899/api/getlunbo').then(res => {
    console.log(res.body);
  })
}
```

7. 发送 post 请求：

```js
postInfo() {
  var url = 'http://127.0.0.1:8899/api/post';
  // post 方法接收三个参数：
  // 参数1： 要请求的URL地址
  // 参数2： 要发送的数据对象
  // 参数3： 指定post提交的编码类型为 application/x-www-form-urlencoded
  this.$http.post(url, { name: 'zs' }, { emulateJSON: true }).then(res => {
    console.log(res.body);
  });
}
```

8. 发送 JSONP 请求获取数据：

```js
jsonpInfo() { // JSONP形式从服务器获取数据
  var url = 'http://127.0.0.1:8899/api/jsonp';
  this.$http.jsonp(url).then(res => {
    console.log(res.body);
  });
}
```

#### 配置本地数据库和数据接口 API

1. 先解压安装 `PHPStudy`;
2. 解压安装 `Navicat` 这个数据库可视化工具，并激活；
3. 打开 `Navicat` 工具，新建空白数据库，名为 `dtcmsdb4`;
4. 双击新建的数据库，连接上这个空白数据库，在新建的数据库上`右键` -> `运行SQL文件`，选择并执行 `dtcmsdb4.sql` 这个数据库脚本文件；如果执行不报错，则数据库导入完成；
5. 进入文件夹 `vuecms3_nodejsapi` 内部，执行 `npm i` 安装所有的依赖项；
6. 先确保本机安装了 `nodemon`, 没有安装，则运行 `npm i nodemon -g` 进行全局安装，安装完毕后，进入到 `vuecms3_nodejsapi`目录 -> `src`目录 -> 双击运行 `start.bat`
7. 如果 API 启动失败，请检查 PHPStudy 是否正常开启，同时，检查 `app.js` 中第 `14行` 中数据库连接配置字符串是否正确；PHPStudy 中默认的 用户名是 root，默认的密码也是 root

### vue-devtools 

Vue 调试工具

### [vue-preview](https://github.com/LS1231/vue-preview)

一个 Vue 集成 PhotoSwipe 图片预览插件

![vuex概念图](https://i.loli.net/2020/05/07/7hMSeTGAWPqjbm2.png)

概念：
vuex 是 Vue 配套的 公共数据管理工具，它可以把一些共享的数据，保存到 vuex 中，方便 整个程序中的任何组件直接获取或修改我们的公共数据；

组件中的 css 作用域问题

抽离路由为单独的模块

## 状态管理 Vuex

### 概述

### 简单实例

### 严格模式

### 中间件

### 表单处理

### 目录结构









# Vue-cli

### 单文件组件

传统方式  ===> 单文件组件

1. 传统方式

```html
hello.html 
<div id="app">
	<h1>{{ message }}</h1>
</div>

<script>
    // 组件 全局组件
    Vue.component('Hello',{
        template: '<h1>this is a h1</h1>'
    })
    
    var vm = new Vue({
        el:'#app',
        data:{
            message: hello world
        }
    })
</script>
```

> 这种方式在很多中小规模的项目中运作的很好，在这些项目里 JavaScript 只被用来加强特定的视图。但当在更复杂的项目中，或者你的前端完全由 JavaScript 驱动的时候，下面这些缺点将变得非常明显：
>
> - **全局定义 (Global definitions)** 强制要求每个 component 中的命名不得重复
> - **字符串模板 (String templates)** 缺乏语法高亮，在 HTML 有多行的时候，需要用到丑陋的 `\`
> - **不支持 CSS (No CSS support)** 意味着当 HTML 和 JavaScript 组件化时，CSS 明显被遗漏
> - **没有构建步骤 (No build step)** 限制只能使用 HTML 和 ES5 JavaScript，而不能使用预处理器，如 Pug (formerly Jade) 和 Babel

2. 单文件组件就是一个vue文件代表一个组件，解决了传统方式的问题

> 文件扩展名为 `.vue` 的 **single-file components (单文件组件)** 为以上所有问题提供了解决方法，并且还可以使用 webpack 或 Browserify 等构建工具。

优点

- [完整语法高亮](https://github.com/vuejs/awesome-vue#source-code-editing)
- [CommonJS 模块](https://webpack.js.org/concepts/modules/#what-is-a-webpack-module)
- [组件作用域的 CSS](https://vue-loader.vuejs.org/zh-cn/features/scoped-css.html)

安装 vue-cli脚手架工具

```bash
npm install -g @vue/cli // 安装到全局下
npm install -s @vue/cli // 安装到本地项目下
```

安装webpack

```bash
npm install -g webpack
```

问题：vue-cli已经安装的版本过低 vue ui 没有效果

```bash
卸载旧版本
npm uninstall vue-cli -g 
yarn global remove vue-cli
```

报错

```bash
npm ERR! code EEXIST
npm ERR! path D:\SoftWare\NodeJs\nodejs\node_modules\@vue\cli\bin\vue.js
npm ERR! dest D:\SoftWare\NodeJs\nodejs\vue
npm ERR! EEXIST: file already exists, cmd shim 'D:\SoftWare\NodeJs\nodejs\node_modules\@vue\cli\bin\vue.js' -> 'D:\SoftWare\NodeJs\nodejs\vue'
npm ERR! File exists: D:\SoftWare\NodeJs\nodejs\vue
npm ERR! Remove the existing file and try again, or run npm
npm ERR! with --force to overwrite files recklessly.

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\Administrator\AppData\Roaming\npm-cache\_logs\2020-06-27T14_27_02_784Z-debug.log

=====
nodeJS 安装 要有两部分 命令行工具 和 安装目录
问题原因 nodeJS 目录中已经安装了vue的相关命令行工具，但是node_modules模块中没有@vue
解决方法：删除vue的命令行工具，然后重装 `npm install -g @vue/cli`
```

vue 图形化管理界面 创建新项目 `Create ` 

```bash
vue ui
```

vue命令行创建 vue-cli

```bash
vue官方 命令行创建工具
vue create myproject 
webpack 创建项目
vue init webpack myproject
```

目录介绍

```bash
node_modules
public 打包，部署到生产环境中的目录 
src  开发目录环境
-- components 组件目录
---- HelloWorld.vue 单文件组件
---- test.vue 单文件组件
-- App.vue 入口文件（组件的引入）
```

运行

```bash
npm run serve //命令是 npm run serve 不是 npm run server
```

```bash
npm ERR! missing script: server
npm ERR! 
npm ERR! Did you mean this?
npm ERR!     serve

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\Administrator\AppData\Roaming\npm-cache\_logs\2020-06-27T15_27_04_483Z-debug.log
====
命令是 npm run serve 不是 npm run server
```

新建 test.vue 文件

```vue
<template>
// 模板区域 视图区域	
	<h2 class="red">Hello {{ msg }}</h2>
</template>

<script>
// 脚本区域
//方法一
export default{
    name: 'World',
    props:{  // props 参数 和 data 参数
        msg:{
            type: String,  // 数据类型 String 是大写的
            default: "test msg"	 //默认
        }
    },
    methods:{
        
    },
    data:{
       return{
        	msg:'test msg'
    	} 
    },
}   

// 方法二
module.exports = {
    data:function(){
        return{
            greeting: 'Hello'
        }
    }
}
</script>

<style scoped>
	// 样式区域 scoped
    .red{color:red}
</style>
```

> 两种传递参数的方法：data 传递参数 和 props 传递参数

```
props:{
	msg:{
		type:string,
		default:"test msg"
	}
}

data:{
	return{
		msg: 'test msg'
	}
}
```

App.vue 入口文件引入 

三步 使用组件 + 导入 组件 + 组件注册

```bash
<template>
<div id="app">
	<hello></hello> // 3.使用组件
</div>
</template>

// 导入组件
<script>
	import hello from './componets/HelloWorld.vue'  // 1.导入组件
	export default {
      name: 'App',
      components: {
        HelloWorld,
        test // 2.组件注册
 	 }
}
</script>
```



第三种：不使用单文件组件，你仍然可以把 JavaScript、CSS 分离成独立的文件然后做到热重载和预编译。

```bash
<!-- my-component.vue -->
<template>
  <div>This will be pre-compiled</div>
</template>
<script src="./my-component.js"></script>
<style src="./my-component.css"></style>

```

#### webpack 部署vue时遇到的问题 e

```
You may use special comments to disable some warnings.
Use // eslint-disable-next-line to ignore the next line.
Use /* eslint-disable */ to ignore all warnings in a file.
```

Vue对语法的限制严格，所以第一次编译运行项目时一直失败

**解决办法：**

在build/webpack.base.conf.js文件中，注释或者删除掉：module->rules中有关eslint的规则

eslint是一个语法检查工具，但是限制很严格，在我的vue文件里面很多空格都会导致红线警告(可以屏蔽)，虽然可以屏蔽，但是在编译的时候老是会跳出来一堆警告出来，所以能完全关闭语法的限制是最好的了。

```
module: {
  rules: [
    //...(config.dev.useEslint ? [createLintingRule()] : []), // 注释或者删除
    {
      test: /\.vue$/,
      loader: 'vue-loader',
      options: vueLoaderConfig
    },
    ...
    }
  ]
}   
```



# Vuex







# Vue-router











# Vue-resource

Vue 2.0 后 作者停止更新，作者建议使用Axios替换 vue-resource

# Axios （ Vue .js AJAX）

注意使用场景

axios 依赖原生的 ES6 Promise 实现

Vue.js 2.0 版本推荐使用 axios 来完成 ajax 请求

Axios 是一个基于 Promise 的易用、简洁且高效的HTTP 库，可以用在浏览器和 Node.js。

[介绍 — Vue.js](https://cn.vuejs.org/v2/cookbook/index.html)

[Vue.js Ajax(axios) | 菜鸟教程](https://www.runoob.com/vue2/vuejs-ajax-axios.html)

[axios中文文档|axios中文网 | axios](http://www.axios-js.com/zh-cn/docs/index.html)

[axios/axios: Promise based HTTP client for the browser and node.js](https://github.com/axios/axios)

特点

- 从浏览器中创建XMLHttpRequests
- 从node.js 创建 http 请求
- 支持Promise API

> promise  依赖原生的 ES6 Promise 实现

安装

cdn

> axios 依赖于vue

```js
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
或
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script src="https://cdn.staticfile.org/axios/0.18.0/axios.min.js"></script>
```

npm 

```
npm install axios
```

yarn

```
yarn add axios
```

bower

```
bower install axios
```

HTTP 请求 GET 请求 和 POST 请求 实际上就是发送一个请求（数据）

是什么？ HTTP协议中的两种发送请求（request）的方法。request(请求) 和 response(响应)

> HTTP（超文本传输协议）是基于TCP/IP的关于数据如何在万维网通信的协议
>
> HTTPS (超文本加密传输协议) 
>
> TCP / UDP

| HTTP 请求 | 相同点  | 不同点 |
| --------- | ------- | ------ |
| POST请求  | TCP连接 |        |
| GET请求   | TCP连接 |        |

JSON 数据的格式(对象)

创建一个JSON 数据格式的文件

JavaScript Object Nation

```
https://heweiliang88.github.io/data.json
```

JSON 文件的构成

- 键值对
- 数组 （数组元素）可以是任何的数据类型
- 对象（键值对） 字符串类型要用双引号 
- 数组对象 // 对象数组
- 大括号



```
axios 组成部分
// 方法部分(请求方法的别名)
get()
post()
create()
...
.then()	 // 数据处理部分
.catch() // 错误处理部分
```



## Get 方法

Get 方法解析JSON 文件

```html
<div id="app">
	{{msg}}
</app>

<div id="app">
	<h1 v-for="msgs in msg">
    	{{msgs}}
    </h1> 
</app>

var vm = new Vue({
	el:'#app',
	data():{
		msg:null
	}
	mounted():{
		axios
			.get('https://heweiliang88.github.io/data.json')
			.then(response => (this.msg = response.data)) // response 读取 json 文件 response.data 读取json数据
			.catch(
				function(error){
					console.log(error);
				}
			)
	}
})
```

GET方法传递参数 URL （/user?ID=12345） 和  params :{ } 传递参数 (传递参数的两种方式)

```
// 直接在 URL 上添加参数 ID=12345
axios.get('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
 
// 也可以通过 params 设置参数：
axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```



## POST方法

```
new Vue({
	el:'#app',
	data(){
		return{
			info:null
		}
	},
	mounted(){
		axios
			.post('https://heweiliang88.github.io/data.json')
			.then(response => (this.info = response))
			.catch(
				function(error){
					console.log(error);
				}
			)
	}
})
```

```
axios.post('/user', {
    firstName: 'Fred',        // 参数 firstName
    lastName: 'Flintstone'    // 参数 lastName
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```



> GET  和 POST 的传递参数的方法
>
> GET  url 传递参数 和 params 传递参数
>
> POST 

```
axios.get('/user?firstname=he&&lastname=weiliang')

axios.get('/user',{
	params:{
        firstname:'he',
        lastname:'weiliang'
	}
})
axios.post('/user',{
	firstname:'he',
	lastname:'weiliang'
})
```



## axios API



| 方法                | 作用                  |
| ------------------- | --------------------- |
| axios(config)       | 发送POST请求          |
| axios(url[,config]) | 发送GET请求默认的方法 |

可以通过向 axios 传递 相关配置创建请求

```js
axios(config)
// 发送POST请求 axios({json}) 和上面的axios.get() / axios.post() 方法相同
axios({
	methods:'post',
	url:'/user/12345',
	data:{
		firstName:'HE'
        lastName:'WeiLiang'
	}
})
//  GET 请求远程图片
axios({
  method:'get',
  url:'http://bit.ly/2mTM3nY',
  responseType:'stream'
})
.then(function(response) {
  response.data.pipe(fs.createWriteStream('ada_lovelace.jpg'))
});
axios(url[, config])
// 发送 GET 请求（默认的方法）
axios('/user/12345');
```

>axios({methods、url、data})



## 请求方法的别名

> 请求方法提供了别名、可以直接使用别名来发起请求

```js
axios.request(config)
axios.get(url[, config])
axios.delete(url[, config])
axios.head(url[, config])
axios.post(url[, data[, config]])
axios.put(url[, data[, config]])
axios.patch(url[, data[, config]])

request、get、post、put、head、patch、delete
```



## 并发

同步和异步

处理并发请求的助手函数`all() 和 spread()`

```
axios.all(iterable); iterable 中的是一个数组
axios.spread(callback);
```

执行多个并发请求(就是同时执行多个请求) axios.all() 方法 

axios.all([函数1，函数2，函数3])

```
function getUseAccount(){
	return axios.get('/user/12345');
}
function getUserPrermissions(){
	return axios.get('/user/12345/permission');
}
axios.all() // 方法 
axios.all([getUseAccount(),getUserPermissions()])
	.then(axios.spread(function(acct.perms){
		// 两个请求现在都在执行完成
}));
```

## 创建实例

使用方法 axios.create([config])

```
axios.create([config])
const instance = axios.create({
	baseURL = '',
	timeout:1000,  // 超时时间
	headers: {'X-Custom-Header': 'foobar'} //头信息
}
```

## 实例方法

指定的配置将与实例的配置合并

```
axios#request(config)
axios#get(url[, config])
axios#delete(url[, config])
axios#head(url[, config])
axios#post(url[, data[, config]])
axios#put(url[, data[, config]])
axios#patch(url[, data[, config]])
```



## 请求配置

```js

```



## 响应结构(响应数据)

axios请求的响应包含以下信息（就是请求后返回的信息）

```json
{
	// data 由服务器提供的响应 数据
    data:{},
    
    // status HTTP 状态码
    status:200,
    
    //  statusTest 来自服务器响应的HTTP状态信息
    statusText:"OK",
    
    // headers 服务器响应的头信息
    headers:{}
    
    // config 是为请求提供的配置信息
    config:{}
    
}
```

```json
{ 
// data 由服务器提供的响应数据
"data": { "roles": { "name": "名字", "num": "数量", "companies": "公司种类" }, "name": "公司表", "num": 5, "companies": [ "腾讯", "Google", "github", "阿里巴巴", "百度" ], "effect": { "social": [ "腾讯", "Google", "github" ], "shopping": [ "阿里巴巴" ], "search": [ "Google", "百度" ] }, "sites": [ { "name": "Google", "info": [ "Android", "Google 搜索", "Google 翻译" ] }, { "name": "阿里巴巴", "info": [ "淘宝", "支付宝", "滴滴打车" ] }, { "name": "腾讯", "info": [ "王者荣耀", "微信", "QQ" ] }, { "name": "github", "info": [ "git" ] }, { "name": "百度", "info": [ "百度云", "百度搜索", "百度打车" ] } ] }, 
// 状态码
"status": 200,
//  statusTest 来自服务器响应的HTTP状态信息
"statusText": "", 
// headers 服务器响应的头信息
"headers": { "cache-control": "max-age=600", "content-length": "397", "content-type": "application/json; charset=utf-8", "expires": "Tue, 07 Jul 2020 01:38:21 GMT", "last-modified": "Mon, 06 Jul 2020 10:55:58 GMT" },
// config 是为请求提供的配置信息
"config": { "transformRequest": {}, "transformResponse": {}, "timeout": 0, "xsrfCookieName": "XSRF-TOKEN", "xsrfHeaderName": "X-XSRF-TOKEN", "maxContentLength": -1, "headers": { "Accept": "application/json, text/plain, */*" }, "method": "get", "url": "https://heweiliang88.github.io/data.json" }, "request": {} 

}
```

使用then 

```js
axios.get("/user/12345")
.then(function(response){
	console.log(response.data);
	console.log(response.status);
    console.log(response.statusText);
    console.log(response.headers);
    console.log(response.config);
});

then(response => (this.info = response))
```

使用catch

```
.catch(function(error){
	console.log(error);
})
```



## 配置默认值(default)

全局的 axios 默认值：

> 全局的axios(作用域作用在全局) 配置默认值，防止多次重复操作，减少代码的重复 URL headers.common/post

```js
axios.defaults.baseURL = 'https://api.example.com';  //默认URL
axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;  // headers
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded'; //post
```

自定义实例默认值

```js
// 创建实例设置默认配置的默认值
var instance = axios.create({
	baseURL:'https://api.example.com'
})

// 在实例已创建后修改默认值
instance.defaults.headers.common['Authorization'] = AUTH_TOKEN;
```



## 配置的优先级

> 配置会以一个优先顺序进行合并。这个顺序是：在 lib/defaults.js 找到的库的默认值，然后是实例的 defaults 属性，最后是请求的 config 参数。后者将优先于前者。
>
> lib/defaults.js库   => 实例的defaults  => config 参数  后者将优先于前者。
>
> 自定义创建实例默认值 > 实例的defaults > lib/defaults.js 库

```js
// 使用由库提供的配置的默认值来创建实例
// 此时超时配置的默认值是 `0`
var instance = axios.create();

// 覆写库的超时默认值
// 现在，在超时前，所有请求都会等待 2.5 秒
instance.defaults.timeout = 2500;

// 为已知需要花费很长时间的请求覆写超时设置 get 请求
instance.get('/longRequest', {
  timeout: 5000
});
```



## 拦截器

在请求或响应被then或catch 处理前拦截它们

> interceptors 拦截器  请求拦截器 和 响应拦截器
>
> interceptors.request.use()

```js
// 添加请求拦截器
axios.interceptors.request.use(
	function (config){
		return config;
	},function(error){
		return Promise.reject(error);
	}
});
// 添加响应拦截器
axios.interceptors.response.use(
	function (config){
		return config;
	},function(error){
		return Promise.reject(error);
	}
})
```

移除拦截器 `axios.interceptors.requeset.eject`

```js
var myInterceptor = axios.interceptors.request.use(function(){});
axios.interceptors.requeset.eject(myInterceptor);
// interceptors.use/eject 
```

可以为``自定义axios 实例``添加拦截器

```
var instance = axios.create();
instance.interceptors.request.use(function(){

})
```

> 自定义 axios 实例
>
> 创建axios 添加 拦截器
>
> 请求拦截器
>
> 直接使用拦截器

## 取消

使用 cancel token 取消请求

Axios 的 cancel token 





可以使用CancelToken.source 工厂方法创建 cancel token 

```js
var CancelToken = axios.CancelToken;
var source = CancelToken.source();
axios.get('/user.12345',{
	cacelToken:source.token
}).catch(function(thrown){
	if(axios.isCancel(thrown)){
		console.log('Requst canceled',thrown.message)
	}else{
	
	}
}})

source.cancel
```





## 错误处理

```js
axios.get('/user/123445')
.catch(function(error){
	if(error.response){
		console.log(error.response.data);
		console.log(error.response.status);
		console.log(error.response.headers);
	}else{
		console.log(’Error‘,error.message);
	}
	console.log(error.config);
});
```

`可以使用 validate Status 配置选项定义一个自定义 HTTP 状态码的错误范围。`

> validateStatus

```js
axios.get('/user/12345',funciton(){
	validateStatus:funciton(status){
		return status < 500  // 状态码在大于或等于500时才会 reject
	}
})
```



## querystring 模块（qs库）[Querry String]

node内置模块，该模块包含用以 URL 解析的实用函数。（对URL 处理的相关模块）

```
const querystring = require('querystring');
axios.post('http://heweiliang.com/',querrystring.stringify({foo:'bar'}));
```







# Vue 组件库

> 网络通信 （axios (实现ajax)）
>
> 页面跳转 （router）
>
> 状态管理 （vuex）
>
> UI 库 （Element-UI）
>
> iView

## UI 组件库

## ELement

[Element - 网站快速成型工具](https://element.eleme.cn/#/zh-CN)

Element，一套为开发者、设计师和产品经理准备的基于 `Vue 2.0 的桌面端组件库`

vue@cli3 以上版本  Element plugin for `@vue/cli` 3.0.

```
vue create my-app
cd my-app
// 安装
vue add element 
```

安装 

```bash
npm i element-ui -Snpm i element-ui -S
```

CDN

```js
<!-- 引入样式 -->
<link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
<!-- 引入组件库 -->
<!-- import Vue before Element -->
<script src="https://unpkg.com/vue/dist/vue.js"></script>
<!-- import JavaScript -->
<script src="https://unpkg.com/element-ui/lib/index.js"></script>
```

快速入门[使用方法]

安装[CDN,NPM] => 引入Element [完整引入，按需引入]  => 全局配置 => 开始使用

引入ELement  [导入（element-ui 和 css 文件） => Vue.use 使用]

修改 `main.js文件`完整引入

```vue
import Vue from 'vue';
// 导入
import ElementUI from 'element-ui';
// css
import 'element-ui/lib/theme-chalk/index.css';
import App from './App.vue';
// 使用 vue.use()
vue.use(ElementUI);

new Vue({
	el:'#app'
}}
```

按需引入[使用的是安装 babel-plugin-component 插件]

> babel Babel 是一个 JavaScript 编译器。可以将高等级的JavaScript 语法装换成转换为向后兼容的 JavaScript 语法，以便能够运行在当前和旧版本的浏览器或其他环境中。

```vue
import Vue from 'vue';
import {
  Pagination,
  Dialog,
  Autocomplete,
  Dropdown,
  DropdownMenu,
  DropdownItem,
  Menu,
  Submenu,
  MenuItem,
  MenuItemGroup,
  Input,
  InputNumber,
  Radio,
  RadioGroup,
  RadioButton,
  Checkbox,
  CheckboxButton,
  CheckboxGroup,
  Switch,
  Select,
  Option,
  OptionGroup,
  Button,
  ButtonGroup,
  Table,
  TableColumn,
  DatePicker,
  TimeSelect,
  TimePicker,
  Popover,
  Tooltip,
  Breadcrumb,
  BreadcrumbItem,
  Form,
  FormItem,
  Tabs,
  TabPane,
  Tag,
  Tree,
  Alert,
  Slider,
  Icon,
  Row,
  Col,
  Upload,
  Progress,
  Spinner,
  Badge,
  Card,
  Rate,
  Steps,
  Step,
  Carousel,
  CarouselItem,
  Collapse,
  CollapseItem,
  Cascader,
  ColorPicker,
  Transfer,
  Container,
  Header,
  Aside,
  Main,
  Footer,
  Timeline,
  TimelineItem,
  Link,
  Divider,
  Image,
  Calendar,
  Backtop,
  PageHeader,
  CascaderPanel,
  Loading,
  MessageBox,
  Message,
  Notification
} from 'element-ui';

Vue.use(Pagination);
Vue.use(Dialog);
Vue.use(Autocomplete);
Vue.use(Dropdown);
Vue.use(DropdownMenu);
Vue.use(DropdownItem);
Vue.use(Menu);
Vue.use(Submenu);
Vue.use(MenuItem);
Vue.use(MenuItemGroup);
Vue.use(Input);
Vue.use(InputNumber);
Vue.use(Radio);
Vue.use(RadioGroup);
Vue.use(RadioButton);
Vue.use(Checkbox);
Vue.use(CheckboxButton);
Vue.use(CheckboxGroup);
Vue.use(Switch);
Vue.use(Select);
Vue.use(Option);
Vue.use(OptionGroup);
Vue.use(Button);
Vue.use(ButtonGroup);
Vue.use(Table);
Vue.use(TableColumn);
Vue.use(DatePicker);
Vue.use(TimeSelect);
Vue.use(TimePicker);
Vue.use(Popover);
Vue.use(Tooltip);
Vue.use(Breadcrumb);
Vue.use(BreadcrumbItem);
Vue.use(Form);
Vue.use(FormItem);
Vue.use(Tabs);
Vue.use(TabPane);
Vue.use(Tag);
Vue.use(Tree);
Vue.use(Alert);
Vue.use(Slider);
Vue.use(Icon);
Vue.use(Row);
Vue.use(Col);
Vue.use(Upload);
Vue.use(Progress);
Vue.use(Spinner);
Vue.use(Badge);
Vue.use(Card);
Vue.use(Rate);
Vue.use(Steps);
Vue.use(Step);
Vue.use(Carousel);
Vue.use(CarouselItem);
Vue.use(Collapse);
Vue.use(CollapseItem);
Vue.use(Cascader);
Vue.use(ColorPicker);
Vue.use(Transfer);
Vue.use(Container);
Vue.use(Header);
Vue.use(Aside);
Vue.use(Main);
Vue.use(Footer);
Vue.use(Timeline);
Vue.use(TimelineItem);
Vue.use(Link);
Vue.use(Divider);
Vue.use(Image);
Vue.use(Calendar);
Vue.use(Backtop);
Vue.use(PageHeader);
Vue.use(CascaderPanel);

Vue.use(Loading.directive);

Vue.prototype.$loading = Loading.service;
Vue.prototype.$msgbox = MessageBox;
Vue.prototype.$alert = MessageBox.alert;
Vue.prototype.$confirm = MessageBox.confirm;
Vue.prototype.$prompt = MessageBox.prompt;
Vue.prototype.$notify = Notification;
Vue.prototype.$message = Message;
```

借助 [babel-plugin-component](https://github.com/QingWei-Li/babel-plugin-component)，我们可以只引入需要的组件，以达到减小项目体积的目的。

1. 安装

```bash
npm install babel-plugin-component -D// 开发目录
```

2.  修改`.babeirc || vue-cli 中的babel.config.js`

```
{
  "presets": [["es2015", { "modules": false }]],
  "plugins": [
    [
      "component",
      {
        "libraryName": "element-ui",
        "styleLibraryName": "theme-chalk"
      }
    ]
  ]
}

vue-cli
module.exports = {
	presets:[
		'@vue/cli-plugin-babel/preset',
		["es2015", { "modules": false }]
	],
	 "plugins": [
    [
      "component",
      {
        "libraryName": "element-ui",
        "styleLibraryName": "theme-chalk"
      }
    ]
  ]
}
```

2. 修改`main.js`文件–

```
import Vue from 'vue';
import { Button,Select } from 'element-ui';
import App from './App.vue';

Vue.componet(Button.name,Button);
Vue.componet(Select.name,Select);
/*
Vue.use(Button)
Vue.use(Select)
*/

new Vue({
	el:"#app",
	render: h -> h(App)
});
```

```
Module build failed: Error: Couldn't find preset "es2015" relative to directory 报错

npm install babel-preset-es2015
```

全局配置

在引入 Element 时，可以传入一个全局配置对象。该对象目前支持 `size` 与 `zIndex` 字段。`size` 用于改变组件的默认尺寸，`zIndex` 设置弹框的初始 z-index（默认值：2000）。按照引入 Element 的方式，具体操作如下：

完整引入 Element：

```vue
import Vue from 'vue';
import { Button } from 'element-ui';
Vue.use(Element,{ size:'small',zIndex:3000 });
```

按需引入 Element：

```vue
import Vue from 'vue';
import { Button } from 'element-ui';

Vue.prototype.$ELEMENT = { size: 'small', zIndex: 3000 };
Vue.use(Button);
```

组件分类

> Basic
>
> Form 表单
>
> Data
>
> Notice
>
> Navigation 导航
>
> Others

![Element](https://i.loli.net/2020/07/09/kot3ZuxGPFRBnvY.png)

组件快速使用



修改 三个文件

> 一、components 组件
>
> mylink.vue  子组件
>
> 新建组件 复制代码到组件中
>
> 
>
> 二、App.vue 入口组件 父组件 
>
> 三步
>
> 1. 导入新建的组件文件的位置
> 2. 创建组件components :{ } 全局组件
> 3. 使用标签（就是导入组件名）
>
> 注意： 导入的文件名
>
> ```
> import link from './components/link.vue';
> link导入的名字要和文件名相同
> ```
>
> 三、main.js  
>
> 导入 element-ui UI 库
>
> ```
> import ElementUI from 'element-ui'
> import 'element-ui/lib/theme-chalk/index.css'
> Vue,use(ElementUI)
> ```
>
> 分析：
>
> 
>
> mylink.vue 就是新建的一个子组件
>
> App.vue 是一个父组件
>
> main.js  是一个入口文件 负责导入所有的vue 文件



## iview



