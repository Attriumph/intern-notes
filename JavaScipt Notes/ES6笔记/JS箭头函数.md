## 箭头函数：
  ES6标准新增了一种新的函数，箭头函数类似于匿名函数，并且简化了函数定义。

  ### 箭头函数有两种格式：

     (参数1, 参数2, …, 参数N) => { 函数声明 }
     (参数1, 参数2, …, 参数N) => 表达式（单一）


    // 当只有一个参数时，圆括号是可选的：
    (单一参数) => {函数声明}
    单一参数 => {函数声明}

    // 没有参数的函数应该写成一对圆括号。
    () => {函数声明}


  ### this的不同
   箭头函数看上去是匿名函数的一种简写，但实际上，箭头函数和匿名函数有个明显的区别：箭头函数内部的this是词法作用域(静态作用域)，由上下文确定。
