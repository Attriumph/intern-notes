# pt，px，em和rem比较

## 1.pt与px
pt(point)是印刷行业常用的单位，等于1/72英寸，表示绝对长度。

px(pixel)指的是像素，是屏幕上显示数据的最基本的点，表示相对大小。
不同分辨率下相同数值的px元素显示会不一样，比如同样是14px大小的字，在1366*768显示屏下会显示的小，在1024*768尺寸的显示器下会相对大点。

px和pt转换规则很简单，默认的显示设置中把文字定义为96DPI（dpi-dots per inch），由72*px=pt*DPI（两边均为1英寸），可得pt=px*3/4。

## 2.em和rem
> em是相对长度单位，相对于当前对象内文本的字体尺寸，即em的计算是基于父级元素font-size的。比如：

    <body style="font-size:14px">
    <p style="font-size:2em">我这里的字体显示大小是28px(14px*2)</p>
    <div style="font-size:18px">
        <p style="font-size:2em">我这里显示字体大小是36px(18px*2),而不是上面计算的28px</p>
    </div>
</body>
效果如下:
<body style="font-size:14px">
    <p style="font-size:2em">我这里的字体显示大小是28px(14px*2)</p>
    <div style="font-size:18px">
        <p style="font-size:2em">我这里显示字体大小是36px(18px*2),而不是上面计算的28px</p>
    </div>
</body>

> rem是css3新增的一个相对单位，与em的区别在于，它是相对于html根元素的(在body标签里面设置字体大小不起作用)。还是上面那个例子，如果换做rem，结果如下：

    <body style="font-size:14px">
    <p style="font-size:2rem">我这里的字体显示大小是32px(16px*2),因为我是根据html根元素的font-size大小进行计算的</p>
    <div style="font-size:18px">
        <p style="font-size:2rem">我这里显示字体大小是32px(16px*2),因为我是根据html根元素的font-size大小进行计算的</p>
    </div>
 <body style="font-size:14px">
     <p style="font-size:2rem">我这里的字体显示大小是32px(16px*2),因为我是根据html根元素的font-size大小进行计算的</p>
     <div style="font-size:18px">
         <p style="font-size:2rem">我这里显示字体大小是32px(16px*2),因为我是根据html根元素的font-size大小进行计算的</p>
     </div>
 </body>
*补充默认font-size大小是16px(如果html中没有设置的话)。
