## a 标签中使用JS代码

### 使用场景：
   可以替换使用button触发事件,只要给a设置为block，就可以设置css为button

### 当a标签调用JS中的代码时，有以下几个方法：


    <a href = "javascript:js_method()">文本</a>
>这是平台上常用的方法，但这种方法在传递this等参数时很容易出现问题，且javascript：协议作为a的href属性时不仅会导致不必要的触发window.onbeforeunload事件，在IE里面会使gif动画停止播放。W3C标准不推荐在href里面执行javascript语句。

    <a href = "javascript:void(0);" onclick ="js_method()">文本</a>
> 这个是很多网站最常用的方法，也是最周全的方法，onclick负责执行js函数，而void是一个操作符，void(0)返回undefined,地址不发生跳转，且这种方法不会像第一种方法一样直接将js方法暴露在浏览器的状态栏。

    <a href = "javascript:;" onclick = "js_merthod()">文本</a>
>这种方法跟第2种类似，区别只是执行了一条空的js代码。

    <a href ="#" onclick ="js_method()">
> 这种方法也是网上很常见的代码，#是标签内置的一个方法，代表top的作用。所以这种方法点击后网页后返回到页面的最顶端。

    <a href="#" onclick="js_method();return false;">
> 这种方法点击执行了js函数后return false，页面不发生跳转，执行后还是在页面的当前位置。
淘宝主页采用的是第2种方法，而Alibaba采用的是第1种方法，和我们的区别是每个href中的javascript方法都用try,catch包围。

综合上述，推荐使用：

    <a href ="javascript:void(0);" onclick ="js_method()">
    <a href = "javascript:;" onclick ="js_method()">
    <a href = "#" onclick ="js_method();return false">  

refer: [原文在这里~](https://blog.csdn.net/GIS__/article/details/7306220)
