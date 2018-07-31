# JavaScirpt中if条件判断的几种情况

在JavaScript中，对于单独作为判断式里的一个表达式if(var)这样的条件判断时，会先把vat转换成布尔型true或false，再判断其真假。

具体的类型转换布尔型的规则是：

* 对于只定义未赋值的变量var ,其值为undefined，为false

* 字符串：空字符串""转换布尔型为false，其它为true

* 数字：数字0转换为布尔值为false，其它为true

* 对象：为null的对象转换为布尔型为false，其它为true；

* 对象属性值：未声明的属性值、属性值为0或空串""或false或null的，转换布尔值为false,其余为true；
