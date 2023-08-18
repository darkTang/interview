CSS

布局

1、响应式布局
1）题目一：假设高度已知，请写出三栏布局，其中左栏、右栏宽度各为 300px，中间自适应
有五种常用解决方案，答出三个才算及格：
// 浮动布局
    <section class="layout float">
      <style media="screen">
        .layout.float .left {
          float: left;
          width: 300px;
          height: 110px;
          background: blue;
        }
        .layout.float .right {
          float: right;
          width: 300px;
          height: 100px;
          background: green;
        }
        .layout.float .center {
          height: 110px;
          background: red;
          overflow: hidden;
        }
      </style>
      <article class="left-center-right">
        <div class="left"></div>
        <div class="right"></div>
        <div class="center">
          <h1>这是浮动布局</h1>
          <p>这是三栏布局的中间元素</p>
          <p>浮动布局的中间元素要放在最后</p>
        </div>
      </article>
    </section>

//绝对布局
    <section class="layout absolute">
      <style media="screen">
        .layout.absolute .left-center-right>div {
          margin-top: 20px;
          position: absolute;
          height: 100px;
        }
        .layout.absolute .left {
          left: 0;
          width: 300px;
          background: blue;
        }
        .layout.absolute .center {
          left: 300px;
          right: 300px;
          background: red;
        }
        .layout.absolute .right {
          right: 0;
          width: 300px;
          background: green;
        }
      </style>
      <article class="left-center-right">
        <div class="left"></div>
        <div class="center">
          <h1>这是绝对布局</h1>
          <p>这是三栏布局的中间元素</p>
          <p>这是三栏布局的中间元素</p>
        </div>
        <div class="right"></div>
      </article>
    </section>

//弹性布局
    <section class="layout flex">
      <style media="screen">
        .layout.flex .left-center-right {
          display: flex;
          margin-top: 140px;
          height: 100px;
        }
        .layout.flex .left {
          width: 300px;
          background: blue;
        }
        .layout.flex .center {
          flex: 1;
          background: red;
        }
        .layout.flex .right {
          width: 300px;
          background: green;
        }
      </style>
      <article class="left-center-right">
        <div class="left"></div>
        <div class="center">
          <h1>这是弹性布局</h1>
          <p>这是三栏布局的中间元素</p>
          <p>这是三栏布局的中间元素</p>
        </div>
        <div class="right"></div>
      </article>
    </section>

//表格布局
    <section class="layout table">
      <style media="screen">
        .layout.table .left-center-right {
          margin-top: 20px;
          display: table;
          width: 100%;
          height: 100px;
        }
        .layout.table .left-center-right>div {
          display: table-cell;
        }
        .layout.table .left {
          width: 300px;
          background: blue;
        }
        .layout.table .center {
          background: red;
        }
        .layout.table .right {
          width: 300px;
          background: green;
        }
      </style>
      <article class="left-center-right">
        <div class="left"></div>
        <div class="center">
          <h1>这是表格布局</h1>
          <p>这是三栏布局的中间元素</p>
          <p>这是三栏布局的中间元素</p>
        </div>
        <div class="right"></div>
      </article>
    </section>

//网格布局
    <section class="layout grid">
      <style media="screen">
        .layout.grid .left-center-right {
          display: grid;
          width: 100%;
          margin-top: 20px;
          grid-template-rows: 100px;
          grid-template-columns: 300px auto 300px;
        }
        .layout.grid .left {
          background: blue;
        }
        .layout.grid .center {
          background: red;
        }
        .layout.grid .right {
          background: green;
        }
      </style>
      <article class="left-center-right">
        <div class="left"></div>
        <div class="center">
          <h1>这是网格布局</h1>
          <p>这是三栏布局的中间元素</p>
          <p>这是三栏布局的中间元素</p>
        </div>
        <div class="right"></div>
      </article>
    </section>
题目延伸一：这五种解决方案各有什么优缺点？

关于浮动问题，常见问题是清除浮动，浮动后是脱离文档流的，如果处理不好会带来很多问题，这是它本身的局限性
其优点是兼容性比较好，只要你能清除浮动，将浮动元素跟周边元素的关系处理好

绝对定位方案的好处是，快捷，也不容易出问题
缺点是，由于布局已经脱离文档流了，意味着下面所有的子元素也必须脱离文档流，那么这个导致了这个方案的使用性是比较差的

Flex 布局，其出现就是为了解决上述两个方式的不足，这是比较完美的解决方案，尤其是现在移动端基本上都是 Flex 布局

在历史上很多人摈弃说不要用 table 布局，比较麻烦，操作比较繁琐，对 SEO 也不够友好，其实这是对表格布局的一种误解，表格布局在很多场景中还是非常适用的，表格布局的兼容性很好，当用 Flex 布局解决不了的时候，尤其是要考虑兼容性问题时，比如 IE8 是不支持 Flex 的，那么就可以用表格布局来替代
表格布局的缺点除了历史的诟病以外，还有就是当其中一个单元格的高度变化时，另外两个单元格也会跟着变，有时候我们的场景是不需要同时增高的，那么什么时候用表格布局什么时候用 Flex 布局，根据不同的场景来选择

网格布局是新增的技术，比之前的模拟网格简化了代码量
题目延伸二：如果高度不已知，左右两边的高度跟着中间高度撑开，以上五种方案，哪种适用？

经过测试，如果高度不已知，只有弹性布局、表格布局和网格布局是适用的解决方案

2）题目二：上下高度固定，中间自适应

由于 div 可以自动水平撑开，而不能上下，所以适合的解决方案只有 flex、table 和 grid 布局。要注意 table-row 必须要有文本内容才会显示高度，否则不显示这个元素，且宽度会随着内容自动撑开。

3）题目三：CSS 实现宽度自适应 100%，宽高 16:9 的比例的矩形

    <style media="screen">
      .wrapper {
        overflow: hidden;
        width: 100%;
        height: 0;
        padding-bottom: 56.25%;
        background: red;
      }
    </style>
    <div class="wrapper"></div>
width 是根据父元素宽度撑开 100%，padding-top, padding-bottom, margin-top, margin-bottom 取值为百分比的时候，参照的也是父元素的宽度。

这个小小的知识点，其实有很大的用处，应用也很广泛，就是进行提前占位，避免资源加载时候的闪烁，还可以让高度自适应。

不能直接将 height 设置为 56.25%，因为会根据父元素的高度撑开这么多百分比。但可以这样设置：

{
  width: 100%;
  height: 56.25vw;
}
考虑到兼容性问题，应该还是使用第一种方式。


2、flex 布局
通过将 display 设置成 flex，可以将元素设置为一个弹性容器，其子元素就是弹性元素，永远沿着主轴排列，一个元素既可以是弹性容器也可以是弹性元素。
通过 flex-direction 来修改主轴方向；
通过 flex-wrap 来处理主轴的排列方式，当一行排列不下时；
通过 flex-shrink 来处理一行放不下时缩小比例，会将元素自身大小算进去；
通过 flex-grow 来处理可以放下时，剩下的宽度如何分配时的放大比例，按照值来进行分配；
上面两种方式是设定弹性尺寸，固定尺寸处理通过 width/height 之外，还可以通过 flex-basis 来设置，同时设置值时 flex-basis 优先级更高；flex-basis 设置的是元素在主轴上的初始尺寸，所谓的初始尺寸就是元素在flex-grow 和 flex-shrink 生效前的尺寸。
复合属性 flex = flex-grow + flex-shrink + flex-basis
通过 justify-content 设置主轴上的对齐方式，可能的值：flex-start flex-end center space-between space-around
通过 align-items 设置交叉轴上的单行对齐方式（只管一行），可能的值：stretch flex-start flex-end center baseline
通过 align-content 设置交叉轴上的多行对齐（管整体），可能的值：stretch flex-start flex-end center space-between space-around
通过 align-self 单独对某个元素设置交叉轴的对齐方式（管单个），值与 align-items 相同，可覆盖容器的 align-items，默认值为 auto，表示继承父元素的 align-items 属性
通过 order 设置元素之间的排列顺序，数值越小越靠前，默认为 0；值相同时，以 DOM 流为准。


3、让文字在 div 中垂直居中的方式

1）使 height 和 line-height 相等

2）内边距上下相等

3）设定为 table-cell，配合 vertical-align: middle

4）使用 box 方法

5）使用 flex 布局

有说可以使用 transform 来实现，但实际上是让一个 div 在另一个 div 中居中，而不仅仅是让文字在 div 中居中。



4、display 哪些取值

none：隐藏对象
inline：指定对象为内联元素
inline-block：指定对象为内联块元素
block：指定对象为块级元素
list-item：指定对象为列表项目，即前面会显示黑点
table：指定对象为块元素级的表格。类同于 html 标签 <tabel>
inline-table：指定对象为内联元素级的表格。类同于 html 标签 <table>
table-caption：指定对象作为表格标题。类同于 html 标签 <caption>
table-row-group：指定对象作为表格行组。类同于 <tbody>
table-row：指定对象作为表格行。类同于 <tr>
table-cell：指定对象作为表格单元格。类同于 <td>
table-column-group：指定对象作为表格列组。类同于 <colgroup>
table-column：指定对象作为表格列。类同于 <col>
table-head-group：指定对象作为表格标题组。类同于 <thead>
table-footer-group：指定对象作为表格脚注组。类同于 <tfoot>
run-in：根据上下文决定对象是内联对象还是块级对象
box：将对象作为弹性弹性盒显示，弹性盒老版本
inline-box：将对象作为内联块级弹性弹性盒显示
flexbox：将对象作为弹性弹性盒显示，弹性盒过渡版本
flex：将对象作为弹性弹性盒显示，弹性盒新版本
inline-flex：将对象作为内联块级弹性弹性盒显示
grid：网格布局，flex 为一维布局，此为二维布局
inline-grid：作为行内元素

rem 布局原理

https://yanhaijing.com/css/2017/09/29/principle-of-rem-layout/，可以是追问 em

HTTP

网络模型

http缓存

跨域

fetch

http0.9->h2-h3

https

cdn加速原理

设计模式

单例、观察者(vue)、发布订阅(node event)、装饰器(es6中)、迭代器模式

JavaScript 基础

基础es6 很多语法this 指向原型链继承方式「new 的原理」js 内存babel 原理前端js 同步异步 promisejs 模块化(或 node)

微任务与宏任务

console.log("script start");

setTimeout(function () {
  console.log("timeout1");
}, 10);

new Promise((resolve) => {
  console.log("promise1");
  resolve();
  setTimeout(() => console.log("timeout2"), 10);
}).then(function () {
  console.log("then1");
});

console.log("script end");


Vue

vue 和 react 对比vuevue 组件 data为什么必须是函数new vue 之后的原理vue 中模版编译原理vue 响应式原理vue 如何实现数组的拦截组件间通讯的方式

react

react 中如何实现方式xss攻击的setState 同步还是异步react fiber 原理react 事件机制hook 和 函数组件的对比（包括生命周期对比）react diff 原理react redux 使用及原理

webpack

webpack 插件plugin和loader区别如何开发一个pluginwebpack 打包原理webpack 如何解决模块化

性能

性能关注哪些指标性能优化手段http 方向「请求数量、缓存、http2」包大小控制cdn 加速开启GPU渲染加速gzip 压缩

ts

好处基础类型联合类型interface 接口与 type 的区别declare 文件声明枚举泛型

前端安全

xss、csrf、域名劫持、sql注入

手写代码

debounce

throttle

实现发布-订阅模式

数组扁平化

函数柯里化 a(1)(2)(3) = 6

实现深拷贝

手写call, apply, bind

手动实现new

手写原生AJAX

写一个获取当前url查询字符串中的参数的方法

模拟 lodash 中的 _.get() 函数

