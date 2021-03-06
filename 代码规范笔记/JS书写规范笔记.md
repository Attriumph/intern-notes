# JavaScript 代码规范笔记和总结

> **refer：全文参考 《豆瓣市集前端开发代码规范》**

## 1.日常笔记之js代码规范：
  * 行尾不加分号
  * 字符串用双引号或者单引号 ，
   eg.

        let strA = `这是一个字符串`
        let strB = `组合：${strA}`
        let strC = '这是一个字符串'
   * {{变量}} 变量名两边保留空格：{{ 变量 }}
   * 尽量使用 let 或 const 代替 var
   * 缩进用两个空格或者一个TAB
   * 不要混用 tab 和 space；
   *  ===, !== 代替 == , != ；
   * 最外层统一使用单引号。
## 2.关于空格
  * for 循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格

        for (i = 0; i < 6; i++) {
          x++
        }

  * 下列关键字前：else, while, catch, finally
  * 下列关键字后：if, else, for, while, do, switch, case,  
      try, catch, finally, with, return, typeof
  * 单行注释 // 后（若单行注释和代码同行，则 //前也需要），多行多行
     注释* 后
  * 对象的属性值前

## 3.关于空行
  * 变量声明后（当变量声明在代码块的最后一行时，则无需空行）
  * 注释前（当注释在代码块的第一行时，则无需空行）
  * 代码块后（在函数调用、数组、对象中则无需空行）
  * 文件最后保留一个空行
## 4.注释
   ####   1) 多行注释
      /*
       * one space after '*'
       */
      var x = 1

>最少三行, '*'后跟一个空格；建议在以下情况下使用：

      1. 难于理解的代码段
      2. 可能存在错误的代码段
      3. 浏览器特殊的 HACK 代码
      4. 业务逻辑强相关的代码

   #### 2) 单行注释
   * 双斜线后，必须跟一个空格；
   * 缩进与下一行代码保持一致；
   * 可位于一个代码行的末尾，与代码间隔一个空格。
## 5.变量命名
   标准变量采用驼峰式命名；
   * 'ID' 在变量名中全大写；
   * 'URL' 在变量名中全大写；
   * 'Android' 在变量名中大写第一个字母；
   * 'iOS' 在变量名中只大写 OS；
   * 'iPhone' 在变量名中只大写 P；
   * 常量全大写，用下划线连接；
## 6.变量声明
   * 一个函数作用域中所有的变量声明尽量提到函数首部。
   * 每个变量单独声明。
   * es6 环境下，常量定义用 const，非全局变量用 let。
## 7.数组、对象
   * 对象属性名不需要加引号；
   * 对象以缩进的形式书写，不要写在一行；
## 8.null和undefined
   #### 1) undefined
> **永远不要直接使用 undefined 进行变量判断；使用typeof 和字符串  
  'undefined' 对变量进行判断。**   

      // not good
      if (person === undefined) {
        ...
      }

      // good
      if (typeof person === 'undefined') {
        ...
      }
  #### 2) null
  * 适用场景：
    * 初始化一个将来可能被赋值为对象的变量
    * 与已经初始化的变量做比较
    * 作为一个参数为对象的函数的调用传参
    * 作为一个返回对象的函数的返回值
* 不适用场景：
    * 不要用 null 来判断函数调用时有无传参
    * 不要与未初始化的变量做比较    
