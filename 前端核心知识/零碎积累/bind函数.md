## bind 函数

> 在 bind(arg1, arg2) 被调用时，会创建一个新函数，这个新函数的 this，都是 arg1，也就是第一个参数。

代码解释如下：

    this.x = 9;
      var module = {
      x: 81,
      getX: function() { return this.x; }
    };

    module.getX(); // 81

    var retrieveX = module.getX;
    retrieveX();  // 9

    var boundGetX = retrieveX.bind(module);
    boundGetX(); // 81
