# filter()函数

filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。
* filter() 不会改变原始数组

## 使用
array1.filter(callbackfn[, thisArg])

* array1：必需。一个数组对象。

* callbackfn 必需: 一个接受最多三个参数的函数。

    function callbackfn(value, index, array1)

* thisArg : 可选。可在 callbackfn 函数中为其引用 this 关键字的对象。
  如果省略 thisArg，则 undefined 将用作 this 值。

## 返回值
一个包含回调函数为其返回 true 的所有值的新数组。如果回调函数为 array1 的所有元素返回 false，则新数组的长度为 0。
