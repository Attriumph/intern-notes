## ES6 扩展运算符

### 扩展运算符作用
es6中引入扩展运算符（…），它用于把一个数组转化为用逗号分隔的参数序列，它常用在不定参数个数时的函数调用，数组合并等情形。因为typeScript是es6的超集，所以typeScript也支持扩展运算符。

## 例子解释
创建一个数组middle
创建第二个包含middle的数组
输出结果

      var middle = [3, 4];
      var arr = [1, 2, middle, 5, 6];
      console.log(arr);
      // [1, 2, [3, 4], 5, 6]
在上例中，没有使用扩展运算符。middle作为数组放入另一个数组中。

但是如果想让输出结果只有一个数组？

这时候就用到扩展运算符，看下面例子，除了使用扩展运算符其他都与上面例子相同。

    var middle = [3, 4];
    var arr = [1, 2, ...middle, 5, 6];
    console.log(arr);
    // [1, 2, 3, 4, 5, 6]

当创建数组arr和使用在middle数组上使用扩展运算符时，不是将middle数组直接插入到arr中，而是将middle数组扩展，然后将元素插入到arr中。

## 其他常用用途
###复制数组
slice()是JavaScript数组的方法，作用是复制数组。我们同样可以使用扩展运算符复制数组。

    var arr = ['a', 'b', 'c'];
    var arr2 = [...arr];
    console.log(arr2);
    // ['a', 'b', 'c']

arr数组中的元素扩展成为单独元素被分配到arr2中。现在可以随意改变arr2数组，且都不会对源数组arr产生影响。

这是因为，arr数组值被扩展后添加到arr2数组中，我们设置arr2等于arr的值，而不是其本身。我们可以关注没有扩展运算符时发生事情，就能理解了。


### 拼接数组
使用扩展运算符可以代替concat()来拼接数组。

    var arr = ['a', 'b', 'c'];
    var arr2 = ['d', 'e', 'f'];

    arr1 = arr.concat(arr2);
    console.log(arr);
    // ['a', 'b', 'c', 'd', 'e', 'f']

    使用扩展运算符

    var arr = ['a', 'b', 'c'];
    var arr2 = ['d', 'e', 'f'];
    arr = [...arr, ...arr2];
    console.log(arr);
    // ['a', 'b', 'c', 'd', 'e', 'f']

###Math
也可以使用math函数连同扩展运算符。如这个例子中，将使用Math.max()

Math.max()将返回一组数最大值。

    Math.max();
    // -Infinity
    Math.max(1, 2, 3);
    // 3
    Math.max(100, 3, 4);
    // 100

在没有扩展运算符，在数组上使用Math.max()最容易方法就是使用.apply()。

    var arr = [2, 4, 8, 6, 0];
    function max(arr) {
      return Math.max.apply(null, arr);
    }
    console.log(max(arr));
    // 8
现在看看使用扩展运算符做同样事情。只需要两行代码就可以做到同样效果。

    var arr = [2, 4, 8, 6, 0];
    var max = Math.max(...arr);
    console.log(max);
    // 8

###字符串转数组
  使用扩展运算符将字符串转换为数组。

    var str = "hello";
    var chars = [...str];
    console.log(chars);
    // ['h', 'e',' l',' l', 'o']

参考：[原文更精彩](https://juejin.im/post/592f63f0ac502e00686842c2)
