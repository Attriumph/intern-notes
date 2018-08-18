# Flex 布局

### 用在何处？
 任何一个容器都可以指定为 Flex 布局

### Flex基本概念

1. 采用 Flex 布局的元素，称为 flex container），简称"容器"。它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"。


2. 容器默认存在两根轴：水平的主轴 **（main axis）** 和垂直的交叉轴 **（cross axis）**。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。

项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size

### flex container 的6大属性

* 1. flex-direction： 决定主轴的方向（即项目的排列方向）

        flex-direction: row | row-reverse | column | column-reverse;
* 2. flex-wrap： 定义如果一条轴线排不下，如何换行

        flex-wrap: nowrap | wrap | wrap-reverse;
* 3. flex-flow：是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap

         flex-flow: <flex-direction> || <flex-wrap>;
* 4. justify-content： 项目在主轴上的对齐方式。

        justify-content: flex-start | flex-end | center | space-between | space-around;
* 5. align-items：项目在交叉轴上如何对齐。

        align-items: flex-start | flex-end | center | baseline | stretch;
* 6. align-content：多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用

        align-content: flex-start | flex-end | center | space-between | space-around | stretch;
        // 备注
        flex-start：与交叉轴的起点对齐。
        flex-end：与交叉轴的终点对齐。
        center：与交叉轴的中点对齐。
        space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
        space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
        stretch（默认值）：轴线占满整个交叉轴。

### flex item 的6大属性
* 1.order：定义项目的排列顺序。数值越小，排列越靠前，默认为0。

        order: <integer>;
* 2.flex-grow：定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大

        flex-grow: <number>;
* 3.flex-shrink：定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小

        flex-shrink: <number>;
* 4.flex-basis：flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

        flex-basis: <length> | auto;
* 5.flex：flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

        flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
        //该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
* 6.align-self:允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

         align-self: auto | flex-start | flex-end | center | baseline | stretch;

参考原文：[一峰老师](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
