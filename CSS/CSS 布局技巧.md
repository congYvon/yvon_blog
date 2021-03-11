阿里妹导读：CSS是Web开发中不可或缺的一部分，随着Web技术的不断革新，CSS也变得更加强大。CSS的众多属性你知道了多少？具体开发中该使用什么属性才最适合恰当？如今的一些CSS属性可以让我们节约更多的时间。比如在Web布局中，现代CSS特性就可以更好的帮助我们快速实现如等高布局，水平垂直居中，经典的圣杯布局、宽高比例、页脚保持在底部等效果。淘系前端技术专家大漠将详细介绍一些不同的CSS属性来实现这些效果，希望对同学们有所帮助。
一  水平垂直居中
如何实现水平垂直居中可以说是CSS面试题中的经典面试题，在多年前这个面试题给很多同学都带来了困惑，但Flexbox布局模块和CSS Grid布局模块的到来，可以说实现水平垂直居中已是非常的容易。
Flexbox中实现水平垂直居中
在Flexbox布局模块中，不管是单行还是多行，要让它们在容器中水平垂直居中都是件易事，而且方法也有多种。最常见的是在Flex容器上设置对齐方式，在Flex项目上设置 margin:auto。
先来看在Flex容器上设置对齐方式。
Flex容器和Flex项目上设置对齐方式
你可能已经知道在Flex容器上设置 justify-content、align-items 的值为 center 时，可以让元素在Flex容器中达到水平垂直居中的效果。来看一个示例：
<!-- HTML -->
<div class="flex__container">    
    <div class="flex__item">
  </div>
</div>
/* CSS */
.flex__container {    
    display: flex;    
  justify-content: center;    
  align-items: center;
}
效果如下：
这种方式特别适应于让Icon图标在容器中水平垂直居中，不同的是在Icon图标容器上显示设置 display: inline-flex。比如下面这个示例：
<!-- HTML -->
<div class="flex__container">    
    <svg> </svg>
 </div>
/* CSS */
.flex__container {    
  display: inline-flex;    
  align-items: center;    
  justify-content: center;
}
效果如下：
在这种模式之下，如果要让多个元素实现水平垂直居中的效果，那还需要加上 flex-direction: column，比如：
<!-- HTML -->
<div class="flex__container">    
    <div class="avatar">:)</div>    
    <div class="media__heading"></div>    
    <div class="media__content"></div>    
    <div class="action"></div>
</div>
/* CSS */
.flex__container  {    
  display: flex;    
  flex-direction: column;    
  justify-content: center;    
  align-items: center;
}
效果如下：
在Flexbox布局中，还可以像下面这样让Flex项目在Flex容器中达到水平垂直居中的效果：
<!-- HTML -->
<div class="flex__container">    
    <div class="flex__item"></div>
</div>
/* CSS */
.flex__container {    
  display: flex; // 或inline-flex    
  justify-content: center;
}
.flex__item {    
  align-self: center;
}
效果如下：
如果在Flex容器中有多个Flex项目时，该方法同样有效：
.flex__container {    
  display: flex; // 或inline-flex    
  justify-content: center;
}
.flex__container > * {    
  align-self: center;
}
比如下面这个效果：
除此之外，还可以使用 place-content: center 让Flex项目实现水平垂直居中：
.flex__container {    
  display: flex;    
  place-content: center;
}
.flex__item {    
  align-self: center;
}
效果如下：
或者换：
.flex__container {   
  display: flex;    
  place-content: center;    
  place-items: center;
}
效果如下：
这两种方式同样适用于Flex容器中有多个Flex项目的情景：
.flex__container {    
  display: flex;    
  flex-direction: column;   
  place-content: center;
}
.flex__container > * {    
  align-self: center;
}
// 或
.flex__container {    
  display: flex;    
  flex-direction: column;    
  place-content: center;    
  place-items: center;
}
效果如下：
可能很多同学对于 place-content 和 place-items 会感到陌生。其实 place-content 是 align-content 和 justify-content 的简写属性；而 place-items 是 align-items 和 justify-items 的简写属性。即：
.flex__container {    
  place-content: center;    
  place-items: center;
}
等效于：
.flex__container {    
    align-content: center;    
  justify-content: center;
  align-items: center;    
  justify-items: center;
}
虽然扩展出来有四个属性，但最终等效于：
.flex__container {    
  display: flex;    
  align-items: center;    
  justify-content: center;
}
// 多行.flex__container {    
  display: flex;    
  flex-direction: column;    
  align-items: center;    
  justify-content: center;
}
在Flex项目上设置margin: auto
如果在Flex容器中只有一个Flex项目，还可以显式在Flex项目中显式设置 margin 的值为auto，这样也可以让Flex项目在Flex容器中水平垂直居中。例如：
.flex__container {    
    display: flex; 
  // 或 inline-flex
 }
.flex__item {    
    margin: auto;
}
效果如下：
整个过程，你可以通过下面这个示例来体验。尝试着选中不同方向的 margin 值：
Grid中实现水平垂直居中
CSS Grid布局可以说是现代Web布局中的银弹。它也是到目前为止布局系统中唯一一个二维布局系统。
在CSS Grid布局中，只需要仅仅的几行代码也可以快速的帮助我们实现水平垂直居中的效果。比如下面这个示例：
<!-- HTML -->
<div class="grid__container">    
    <div class="grid__item"></div>
</div>
/* CSS */
.grid {    
  display: grid; // 或 inline-grid    
  place-items: center
}
效果如下：
在CSS Grid布局模块中，只要显式设置了 display: grid（或 inline-grid）就会创建Grid容器和Grid项目，也会自动生成网格线，即行和列（默认为一行一列）。
在没有显式地在Grid容器上设置 grid-template-columns 和 grid-template-rows，浏览器会将Grid容器默认设置为Grid内容大小：
这种方法也适用于CSS Grid容器中有多个子元素（Grid项目），比如：
<!-- HTML -->
<div class="grid__container">    
    <div class="avatar">:)</div>    
    <div class="media__heading"></div>    
    <div class="media__content"></div>    
    <div class="action"></div>
</div>
这个时候你看到的效果如下:
而且 place-items 适用于每个单元格。这意味着它将居中单元格的内容。比如下面这个示例：
<!-- HTML -->
<div class="grid__container">    
    <div class="grid__item">        
    <h3>Special title treatment</h3>        
    <p>With supporting text below as a natural lead-in to additional content.</p>  
    <div class="action">Go somewhere</div>    
    </div>
</div>
/* CSS */
.grid__container {    
  display: grid;    
  place-items: center;    
  grid-template-columns: repeat(2, 1fr);    
  gap: 2vh;
}
.grid__item {    
  display: grid;    
  place-items: center;
}
效果如下：
二  等高布局
等高布局也是Web中非常常见的一种布局方式，而且实现等高布局的方案也有很多种。这里我们主要来看Flexbox布局模块和Grid布局模块给我们带来了什么样的变化。
在Flexbox和Grid布局模块中，让我们实现等高布局已经是非常的简单了，比如：
<!-- Flexbox -->
<flex__container>    
    <flex__item></flex__item>    
    <flex__item></flex__item>    
    <flex__item></flex__item>
</flex__container>
/* CSS */
.flex__container {    
  display: flex; // 或 inline-flex
}
简单地说，在容器上显式设置了 display 的值为 flex 或 inline-flex，该容器的所有子元素的高度都相等，因为容器的 align-items 的默认值为 stretch。
这个时候你看到的效果如下：
这种方式特别适用于卡片组件中：
在Grid布局模块中类似：
<!-- HTML -->
<grid__container>    
    <grid__item></grid__item>    
    <grid__item></grid__item>    
    <grid__item></grid__item>
</grid__container>
/* CSS */
.grid__container {    
  display: grid;    
  grid-template-columns: 20vw 1fr 20vw; /* 根据需求调整值*/
}
效果如下：
同样在一些卡片类布局中运用：
如果需求有所调整，比如在Flex项目 或 Grid项目的子元素高度和容器高度相同。
<!-- HTML -->
<flex__container>    
    <flex__item>        
        <content></content>    
    </flex__item>
</flex__container>
/* CSS */
.flex__container {    
  display: flex;
}
.content {    
  height: 100%
}
// 或
.grid__container {    
  display: grid;    
  grid-auto-flow: column;
}
.content {    
  height: 100%;
}
效果如下：
三  Sticky Footer
首先用下图来描述什么是Sticky Footer布局效果：
Sticky Footer实现方案和等高、垂直居中一样，同样有很多种方案可以实现。
比如像下面这样的结构：
<!-- HTML --><header></header><main></main><footer></footer>
先来看Flexbox布局模块中的实现方案：
body {    
  display: flex;    
  flex-direction: column;
}
footer {    
  margin-top: auto;
}
可以尝试着在 main 区域右下角向下拖动，改变主内容区域的高度，你会发现“当内容不足一屏时，<footer> 会在页面的最底部，当内容超出一屏时，<footer> 会自动往后延后”。
在Flexbox布局中，还可以在 <main> 区域上设置下面的样式，达到相等的效果：
body {    
  display: flex;    
  flex-direction: column;
}
main {    
  flex: 1 0 auto;
}
效果如下：
<main> 中的 flex: 1 0 auto 相当于是：
main {    
  flex-grow: 1; /*容器有剩余空间时，main区域会扩展*/    
  flex-shrink: 0; /*容器有不足空间时，main区域不会收缩*/    
  flex-basis: auto; /*main区域高度的基准值为main内容自动高度*/
}
如果你想省事的话，可以在 main 上显式设置 flex-grow:1，因为 flex-shrink 和 flex-basis 的默认值为 1 和 auto。
在CSS Grid布局中我们可以借助 1fr 让 <main> 区域根据Grid容器剩余空间来做计算。
.grid__container {    
  display: grid;    
  grid-template-rows: auto 1fr auto;
}
效果如下：
四  均分列
在Web布局中，很多时候会对列做均分布局，最为常见的就是在移动端的底部Bar，比如下图这样的一个效果：
在Flexbox和Grid还没出现之前，如果希望真正的做到均分效果，可以用 100%（或 100vw）除以具体的列数。比如：
<!-- HTML -->
<container>    
    <column></column>    
    <column></column>    
    <column></column>
</container>
/* CCSS */
.container {    
  inline-size: 50vw;    
  min-inline-size: 320px;    
  display: flex-row;
}
.column {    
  float: left;    
  width: calc(100% / 3);
}
效果如下：
通过浏览器调试器中可以发现，现个列的宽度都是相等的：
在Flexbox和Grid布局中，实现上面的效果会变得更容易地多。先来看Flexbox中的布局：
<!-- HTML -->
<flex__container>    
    <flex__item></flex__item>    
    <flex__item></flex__item>    
    <flex__item></flex__item>
</flex__container>
/* CSS */
.flex__container {    
  inline-size: 50vw;    
  display: flex;
}
.flex__item {    
  flex: 1;
}
效果如下：
在Flexbox布局模块中，当flex取的值是一个单值（无单位的数），比如示例中的 flex:1，它会当作显式的设置了 flex-grow: 1。浏览器计算出来的 flex：
接下来看Grid中如何实现上例的效果：
<!-- HTML -->
<grid__container>    
    <grid__item></grid__item>    
    <grid__item></grid__item>    
    <grid__item></grid__item>
</grid__container>
/* CSS */
.grid__container {    
  display: grid;    
  grid-template-columns: repeat(3, 1fr); /*这里的3表示具体的列数*/
}
最终的效果是相同的：
这样的布局方式也适用于其他的布局中。但不管是Flexbox还是Grid布局中，都存在一定的缺陷，当容器没有足够的空间容纳Flex项目（或Grid项目）时，Flex项目或Grid项目会溢出（或隐藏，如果Flex容器或Grid容器显式设置了 overflow:hidden）：
修复这种现象最简单的方式是在Flex容器或Grid容器显式设置一个 min-width（或 min-inline-size）：
.flex__container {    
  min-inline-size: 300px;
}
不过话又说回来，比如我们的Flex项目（或Grid项目）是一个卡片，每张卡片宽度是相等之外，更希望容器没有足够空间时，Flex项目（或Grid项目）会自动断行排列。
我们继续通过示例向大家展示。先来看Flexbox实现方案：
.flex__container {    
  display: flex;    
  flex-wrap: wrap;}
.flex__item {    
  flex: 0 1 calc((100vw - 18vh) / 4); /* calc(100vw -18vh) / 4 是flex-basis的基准值 */
}
你可以尝试着调整浏览器的视窗宽度，当浏览器的视窗越来越小时，Flex容器宽度也就会越来越小，当Flex容器小到没有足够的空间容纳四个Flex项目（就此例而言），那么Flex项目就会断行排列：
基于该例，如果把Flex项目的 flex 值改成：
.flex__item {    
    flex: 0 0 400px;
 }
这个时候，当Flex容器没有足够空间时，Flex项目会按 flex-basis: 400px 计算其宽度，Flex容器没有足够空间时，Flex就会断行：
反过来，如果Flex项目的值 flex 改成：
.flex__item {    
  flex: 1 0 400px;
}
当Flex容器没有足够空间排列Flex项目时，Flex项目会按 flex-basis: 400px 计算其宽度，Flex会断行，并且同一行出现剩余空间时，Flex项目会扩展，占满整个Flex容器：
在Grid中实现类似的效果要更复杂一点。可以使用 repeat() 函数，1fr 以及 auto-fit 等特性：
.grid__container {    
  display: grid;    
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));    
  gap: 2vh;
}
效果如下：
如果你对这方面知识感兴趣的话，还可以移步阅读《Container Query Solutions with CSS Grid and Flexbox》一文。
其实在Grid中与 auto-fit 对比的值还有一个叫 auto-fill。但两者的差异是非常地大，用下图来描述 auto-fit 和 auto-fill 的差异：
另外这种方式也是到目前为止一种不需要借助CSS媒体查询就可以实现响应式布局效果。
五  圣杯布局
圣杯布局（Holy Grail Layout）)是Web中典型的布局模式。看上去像下图这样：
对于圣杯布局而言，HTML结构是有一定的要求，那就是内容为先：
<!-- HTML -->
<header></header>
<main>    
  <article></article> 
  <!-- 主内容 -->    
  <nav></nav>    
  <aside></aside>
</main>
<footer></footer>
在这里主要还是和大家一起探讨，如何使用Flexbox和Grid布局模块来实现圣杯布局。先来看Flexbox实现方案：
body {    
  width: 100vw;    
  display: flex;    
  flex-direction: column;
}
main {    
  flex: 1;    
  min-height: 0;
  display: flex;    
  align-items: stretch;    
  width: 100%;
}
footer {    
  margin-top: auto;
}
nav {    
  width: 220px;    
  order: -1;
}
article {    
  flex: 1;
}
aside {   
  width: 220px;
}
效果如下：
通过在 nav、aside 和 article 上显式设置 order 的值，可以很好的控制这三个区域的布局顺序。比如说，希望 <aside> 在 <article> 之前排列，只需要在上面的示例基础上做一点点调整：
nav {    
  order: 0;
}
aside {    
  order: -1;
}
效果如下：
注意，order的默认值为0，值越大越排在后面！
在上例的基础上，借助CSS媒体对象的特性，可以很容易实现响应式的圣杯布局效果：
@media screen and (max-width: 800px) {    
  main {        
    flex-direction: column;    
  }
  nav, aside {        
     width: 100%;    
  }
}
效果如下：
尝试着拖动浏览器来改变视窗大小，你可以看到如下图的效果：
在Grid布局模块中，实现圣杯布局要比Flexbox布局模块中更容易，而且更灵活。在CSS Grid布局模块中，HTML结构可以更简洁：
<!-- HTML -->
<body>    
  <header></header>    
  <main></main>    
  <nav></nav>    
  <aside></aside>    
  <footer></footer>
</body>
在CSS方面有很多种方案可以实现圣杯布局效果。我们先来看第一种：
body {    
  display: grid;    
  grid-template: auto 1fr auto / 220px 1fr 220px;
}
header {    
  grid-column: 1 / 4;
}
main {    
  grid-column: 2 / 3;    
  grid-row: 2 / 3;
}
nav {    
  grid-column: 1 / 2;    
  grid-row: 2 / 3;
}
aside {    
  grid-column: 3 / 4;    
  grid-row: 2 / 3;
}
footer {    
  grid-column: 1 / 4;
}
效果如下：
上面示例采用的是网格线来给每个区域进行定位的：
和Flexbox布局类似，在媒体查询中可以改变每个网格区域的位置：
@media screen and (max-width: 800px) {    
  body {        
    grid-template-rows: auto;        
    grid-template-columns: auto;    
    }
  header,main,nav,aside,footer {        
    grid-column: 1 / 2;        
    min-height: auto;    
  }
  main {        
    grid-row: 3 / 4;        
    margin: 0;    
  }
  nav {        
    grid-row: 2 / 3;    
  }
  aside {        
    grid-row: 4 / 5;    
  }
  footer {        
    grid-row: 5 / 6;    
  }
}
除了 grid-template（即 grid-template-columns 和 grid-template-rows）之外，在Grid布局中还可以使用 grid-area 和 grid-template-areas 属性的结合，也能很方便的实现CSS圣杯布局。基于上面的示例上，只需要把你的CSS调整为：
body {    
  display: grid;    
  grid-template-areas: "header header header" "nav main aside""footer footer footer";
}
header {    
  grid-area: header;
}
main {    
  grid-area: main;
}
nav {    
  grid-area: nav;
}
aside {    
  grid-area: aside;
}
footer {    
  grid-area: footer;
}
@media screen and (max-width: 800px) {    
  body {        
    grid-template-areas:"header""nav""main""aside""footer";    
  }
}
效果如下：
你可能发现了它们之间的差异性：
后面这个示例中，<nav>、<main> 和 <aside> 区域宽度相等。这是因为我们示例中通过 grid-template-areas 来声明网格，在使用 grid-template-areas 创建网格时，其实也隐式的创建了网格线，只不过他和 grid-template 不同的是 grid-template 可以显式的指定网格轨道大小，而 grid-template-areas 在该示例中相当于网格轨道大小都是 1fr。
如果我们希望 <main> 的区域变得更大，那么可以在 grid-template-areas 上做个调整：
body {    
  display: grid;    
  grid-template-areas: "header header header header header""nav main main main aside""footer footer footer footer footer";
}
效果如下：
这个时候网格区域的划分像下图这样：
虽然在效果有所调整了，但还是均分状态。更好的解决方案是，将 grid-template-areas 和 grid-template 结合起来使用：
body {    
  display: grid;    
  grid-template-areas:"header header header""nav main aside""footer footer footer";    
  grid-template-columns: 220px 1fr 220px;    
  grid-template-rows: auto 1fr auto;
}
header {    
  grid-area: header;
}
main {    
  grid-area: main;
}
nav {    
  grid-area: nav;
}
aside {    
  grid-area: aside;
}
footer {    
  grid-area: footer;
}
@media screen and (max-width: 800px) {    
  body {        
    grid-template-areas:"header""nav""main""aside""footer";        
    grid-template-columns: 1fr;        
    grid-template-rows: auto auto 1fr auto auto;    
  }
  main {        
    margin-left: 0;        
    margin-right: 0;    
  }
}
效果如下：
你可以发现，这个时候，网格线的区域的命名像下图这样：
六  12列网格布局
12列网格布局最早是由960.gs提出的网格布局系统：
12列网格布局在设计系统和CSS Framework中经常使用，比如业内经典的Bootstrap就采用了12列网格布局系统：
在社区中也有很多在线工具，帮助我们快速构建12列网格系统，比如 Free CSS Grid Tools & Resources For Developers 一文中罗列的工具。
不过这里主要是想和大家一起看看在Flexbox和Grid布局模块中是如何实现12列的网格布局系统。
先来看Flexbox布局模块。12列网格布局的HTMl结构一般类似于下面这样：
<!-- HTML -->
<flex__grid>    
  <flex__row>        
    <flex__item col4></flex__item col4>        
    <flex__item col4></flex__item col4>        
    <flex__item col4></flex__item col4>    
  </flex__row>
</flex__grid>
注意，12列网格中，一般同一行的列数值和刚好等于12。比如上面的HTML结构，行中有三列，每列的宽度刚好四个网格宽度加两个列间距。并且在计算的时候有一套成熟的计算公式：
而且还设计上也会有所差异，比如说距离容器两侧有没有间距等：
这些的差异对于计算公式和样式代码的设计都略有差异。我们用其中一个为例：
• 
你会看到的效果如下：
在该示例中采用了CSS自定义属性相关的特性，让整个计算变得更容易一些。
对于使用CSS Grid布局模块来实现12列网格布局，相对而言，不管是HTML结构还是CSS代码都会更简易一些。在使用CSS Grid布局模块实现12列网格布局，将会运用到 repeat()、minmax()、gap 和 fr 等特性。具体的来看一个示例吧。
<!-- HTML --><grid__container>    <grid__item></grid__item></grid__container>
我们来看CSS代码：
• 使用 fr 将网格均分为相等的值，即每列宽度都是 1 个 fr；配合 repeat() 函数，即 repeat(12, 1fr) 创建了12列网格。
• 使用 gap 可以用来控制网格之间的间距。
• 配合 minmax() 还可以设置网格最小值。
具体的代码如下：
• 
:root {    --columns: 12;    --gap: 10px;    --span: 1;}
.grid__container {    display: grid;    grid-template-columns: repeat(var(--columns), 1fr);    grid-template-rows: 1fr;    gap: var(--gap);    padding-left: calc(var(--gap) / 2);    padding-right: calc(var(--gap) / 2);}
.grid__item {    min-block-size: 10vh;    grid-column: span var(--span);}
.col1 {    --span: 1;}
.col2 {    --span: 2;}
.col3 {    --span: 3;}
.col4 {    --span: 4;}
.col5 {    --span: 5;}
.col6 {    --span: 6;}
.col7 {    --span: 7;}
.col8 {    --span: 8;}
.col9 {    --span: 9;}
.col10 {    --span: 10;}
.col11 {    --span: 11;}
.col12 {    --span: 12;}
你将看到的效果如下：
就该示例而言，grid-template-columns: repeat(12, 1fr) 创建网格如下图所示：
除了上述这种粗暴的方式，还可以更灵活一些，将 auto-fit、minmax() 以及 grid-auto-flow: dense 等来创建：
.grid__container {    
  padding: 1em;    
  display: grid;    
  grid-template-columns: repeat(auto-fit, minmax(60px, 1fr));    
  gap: 1em;    
  grid-auto-flow: dense;
}
对于 .grid__item 可以通过 grid-column、grid-row 来控制网格项目的位置：
加上 grid-auto-flow: dense 会根据Grid容器空间，Grid项目会自动流到合适的位置：
这种布局对于杂志类的布局非常的适用。有关于这方面更详细的介绍可以阅读@Keir Watson的《Responsive Grid Magazine Layout in Just 20 Lines of CSS》一文。
七  两端对齐
在Web布局中时常碰到两端对齐的需求。在Flexbox布局中，时常在Flex容器中显式设置 justify-content 的值：
.flex__container {   
  display: flex;    
  flex-wrap: wrap;    
  justify-content: space-between;
  width: 100%;
}
但在末尾行，如果和前面行的个数不相同（Flex项目）就会出现下图这样的效果：
像上图这样的效果，并不是我们所需要的，因为我们希望在最后一行的Flex项目不足够排列满一行时，希望Flex项目一个紧挨一个的排列：
在Flexbox要实现上图这样的效果，只需要在Flex容器中添加一个伪元素：
.flex__container::after {    
  content: "";    
  display: flex;    
  flex: 0 1 32vw;
}
注意，伪元素的 flex-basis 建议设置的和卡片的 flex-basis（或宽度）等同。这个时候你将看到像下面这样的示例：
不过这种方式也不是最佳的方式，当末尾行的个数不只少一个时，就会出现下图这样的效果：
面对这样的场景，我们需要给Flex容器添加额外的空标签元素：
占位符元素数量 = 每行最大的列数 - 2
但是 gap属性出现之后，要实现这样的效果就不难了：
body {    
  padding: 1vh;
}
.flex__container {    
  display: flex;    
  flex-wrap: wrap;    
  gap: 2vh;
  width: 100%;
}
.flex__item {    
  flex: 0 1 calc((100vw - 8vh) / 4);
}
效果如下：
注意，gap 运用在Flexbox中到目前为止，仅得到了Firefox浏览器的支持。上面的示例，使用Firefox浏览器，你看到的效果如下：
在CSS Grid布局中，就可以直接使用 gap：
body {    
  padding: 1vh;
}
.grid__container {    
  display: grid;    
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));    
  gap: 1vh;
}
效果如下：
八  选择最佳的值
很多时候，针对不同的场景，设计师会为我们提供不同的设计风格，比如元素大小：
随着 clam() 函数的到来，这一切都变得容易地多。
clam() 函数接受三个参数，即 clam(MIN, VAL, MAX)，其中 MIN 表示最小值，VAL 表示首选值，MAX 表示最大值。它们之间：
• 如果 VAL 在 MIN 和 MAX 之间，则使用 VAL 作为函数的返回值。
• 如果 VAL 大于 MAX，则使用 MAX 作为函数的返回值。
• 如果 VAL 小于 MIN，则使用 MIN 作为函数的返回值。
我们来看一个示例：
.element {    /**    * MIN = 100px    * VAL = 50vw ➜ 根据视窗的宽度计算    * MAX = 500px    **/
    width: clamp(100px, 50vw, 500px);}
比如浏览器视窗现在所处的位置是1200px的宽度，那么 .element 渲染的结果如下：
这个时候 .element 元素的 width 是 500px。此时，clamp(100px, 50vw, 500px) 相当于 clamp(100px, 600px, 500px)，对应的 VAL 值是 600px，大于 MAX 值，那么这个时候 clamp()函数返回的值是 MAX，即 500px，这个时候 .element 的 width 值就是 500px（即 MAX 的值）。
如果我们把浏览器视窗缩小至 760px：
这个时候 .element 元素的 width 是 50vw。此时，clamp(100px, 50vw, 500px) 相当于clamp(100px, 380px, 500px)，对应的 VAL 值是 380px，该值大于 MIN 值（100px），小于 MAX 值（500px），那么这个时候 clamp() 函数返回的值是 VAL，即 50vw，这个时候 .element的 width 值就是 50vw（即 VAL 的值）。
如果继续将浏览器的视窗缩小至 170px：
这个时候 .element 元素的 width 是 100px。此时，clamp(100px, 50vw, 500px) 相当于 clamp(100px, 85px, 500px)，对应的 VAL 值是 85px，该值小于 MIN 值（100px），那么这个时候 clamp() 函数返回的值是 MIN，即 100px，这个时候 .element 的 width 值就是 100px（即 MIN 的值）。
就该示例而言，clamp(100px, 50vw, 500px) 还可以这样来理解：
• 元素 .element 的宽度不会小于 100px（有点类似于元素设置了 min-width: 100px）。
• 元素 .element 的宽度不会大于 500px（有点类似于元素设置了 max-width: 500px）。
• 首选值 VAL 为 50vw，只有当视窗的宽度大于 200px 且小于 1000px 时才会有效，即元素 .element 的宽度为 50vw（有点类似于元素设置了 width：50vw）。
九  Logo图标的对齐
我想你在Web开发中可能碰到过类似下图的这样的场景：
正像上图所示，Logo图像的有大有小（宽度和高度都不一样）。面对这样的业务场景，很多时候都希望设计师能提供相同尺寸的图像。但这样势必会影响Logo图像的外观。
前段时间看到@Ahmad Shadeed专门写了一篇博文《Aligning Logo Images in CSS》，就是介绍如何实现上图这样的布局效果。
其实实现这样的布局效果，主要运用到的就是CSS的 object-fit 属性，而这个属性早在多年前就得到了各大主流浏览器的支持。
这里我们用一个简单的示例，来看看具体实现过程。先来看HTML结构：
<!-- HTML --><ul class="brands">    <li class="brands__item">        <a href="#">            <img src="img/logo.png" alt="">        </a>    </li>    <li> <!-- ... --> </li></ul>
居中对齐前面已经介绍过了，这里主要是看图像大小方面的处理：
.brands {    display: grid;    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));    grid-gap: 1rem;}
.brands__item {    background: #eee;}
.brands__item a {    display: flex;    justify-content: center;    align-items: center;    height: 100%;}
.brands__item img {    width: 130px;    height: 75px;    object-fit: contain;}
这样就能实现上图的效果。你可能发现了，有些Logo图像带有背景颜色，如果让效果更好一些，可以把CSS混合模式相关的特性运用进来：
.brands__item img {    width: 130px;    height: 75px;    object-fit: contain;    mix-blend-mode: multiply;}
这个时候，你看到的效果如下：
object-fit 除了取值 contain 之外，还有其他几个值：
其实这个方案也适用于产品图片，人物头像等布局。
小结
文章中主要介绍了Web中一些布局的实现思路和具体方案。其实文章提到的效果，比如水平垂直居中、等高布局、平均分布列和Sticky Footer等，在CSS中一直有多种解决方案，只不过随着CSS Flexbox布局模块和CSS Grid布局模块的到来，实现这些效果变得更为灵活和简洁。
当然，文章中提到的只是一些最为常见的一些效果，其实在Web布局中，特别是Flexbox布局和Grid布局中还存在着很多有意思的东西，只不过因为篇幅的原因没有一一罗列。如果你感兴趣可以再挖掘一些出来，如果你在这方面有更好的经验或方案，欢迎在下面的评论中分享。最后希望这篇文章对你平时的工作有所帮助。
