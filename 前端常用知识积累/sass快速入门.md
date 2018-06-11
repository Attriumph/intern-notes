# Sass快速入门

SASS是一种CSS预处理器"（css preprocessor）。它是一种专门的编程语言，可以进行网页样式设计，可以将scss文件编译成正常的CSS文件。

## 1.安装
    * 需要安装Ruby
    * gem install sass
## 2.使用
    * 将scss转化为正常css代码
     sass test.scss test.css
     // 可以设置生产的style
     // nested, expanded,compact,compressed

     //通常使用
     sass --style compressed test.scss test.css
## 3.基本语法
   * 变量：以$开头，类似Jquery
     eg. $bule : #1875e7

     如果嵌套字符串中，需要将$blue放在#{}中
   * 允许使用算术表达式
   * 需要css嵌套（属性也可以嵌套）
   * 允许一个选择器继承另一个选择器
   * Mixin：可以重复使用的代码块，通过@include重用
   * 颜色函数
   * @import 插入外部文件
   * 支持if，while和for语句 开头用@
   * 允许自定义函数，同样用@

ref: [详细请参考](http://www.ruanyifeng.com/blog/2012/06/sass.html)
## 2.常用函数：
除了颜色函数，还有：
unit($number)：返回一个值的单位;
unitless($number)：判断一个值是否带有单位;
