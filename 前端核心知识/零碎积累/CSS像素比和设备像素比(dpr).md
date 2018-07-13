## 1.CSS像素
CSS像素（CSS Pixels）：是Web编程的概念，指的是CSS样式代码中使用的逻辑像素

所以，1个CSS像素在不同设备上可能对应不同的物理像素数，这个比值是设备的属性（Device Pixel Ratio，设备像素比）

在CSS规范中，长度单位可以分为绝对单位和相对单位。px是一个相对单位，相对的是设备像素（Device Pixels）。比如iPhone5使用的是Retina视网膜屏幕，用2x2的Device Pixel代表1x1的CSS Pixel，所以设备像素数为640x1136px，而CSS逻辑像素数为320x568px

## 2.设备像素比
设备像素比缩写为DPR或者DPPX，如下：
>Device Pixel Ratio: Number of device pixels per CSS Pixel

>Dots Per Pixel: the amount of device pixels per CSS pixel

所以，设备像素比表示1个CSS像素（宽度）等于几个物理像素（宽度）：

DPR = 物理像素数 / 逻辑像素数
比如dpr=2时，1个CSS像素由4个物理像素点组成，见上面对CSS像素的解释

PS: DPR不是单位，而是一个属性名，比如在浏览器中通过window.devicePixelRatio获取屏幕的DPR

refer: [参考原文](http://www.ayqy.net/blog/%E5%AE%8C%E5%85%A8%E7%90%86%E8%A7%A3px-dpr-dpi-dip/)
