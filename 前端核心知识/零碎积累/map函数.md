## map函数
map() 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。

        // ES6
       let numbers = [1, 5, 10, 15];
       let doubles = numbers.map( x => x ** 2);

       // doubles is now [1, 25, 100, 225]
       // numbers is still [1, 5, 10, 15]
