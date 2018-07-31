## Promise
Promise，简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果。

从语法上说，Promise 是一个对象，从它可以获取异步操作的消息。Promise 提供统一的 API，各种异步操作都可以用同样的方法进行处理。

ES6 规定，Promise对象是一个构造函数，用来生成Promise实例。

下面代码创造了一个Promise实例。

    const promise = new Promise(function(resolve, reject) {
      // ... some code

      if (/* 异步操作成功 /){
        resolve(value);
      } else {
        reject(error);
      }
    });

Promise构造函数接受一个函数作为参数，该函数的两个参数分别是resolve和reject。它们是两个函数，由 JavaScript 引擎提供，不用自己部署。

* resolve函数的作用：

  将Promise对象的状态从“未完成”变为“成功”（即从 pending 变为 resolved），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；
* reject函数的作用:

  将Promise对象的状态从“未完成”变为“失败”（即从 pending 变为 rejected），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。


Promise实例生成以后，可以用then方法分别指定resolved状态和rejected状态的回调函数。

    promise.then(function(value) {
      // success
      }, function(error) {
      // failure
      });

then方法可以接受两个回调函数作为参数。第一个回调函数是Promise对象的状态变为resolved时调用，第二个回调函数是Promise对象的状态变为rejected时调用。其中，第二个函数是可选的，不一定要提供。这两个函数都接受Promise对象传出的值作为参数。


>Promise 新建后就会立即执行。

    let promise = new Promise(function(resolve, reject) {
      console.log('Promise');
      resolve();
      });

      promise.then(function() {
        console.log('resolved.');
        });

      console.log('Hi!');

      // Promise
      // Hi!
      // resolved


下面是一个用Promise对象实现的 Ajax 操作的例子。

    const getJSON = function(url) {
      const promise = new Promise(function(resolve, reject){
        const handler = function() {
          if (this.readyState !== 4) {
            return;
          }
          if (this.status === 200) {
            resolve(this.response);
          } else {
            reject(new Error(this.statusText));
          }
        };

        const client = new XMLHttpRequest();
        client.open("GET", url);
        client.onreadystatechange = handler;
        client.responseType = "json";
        client.setRequestHeader("Accept", "application/json");
        client.send();
     });
    return promise;
  };

    getJSON("/posts.json").then(function(json) {
      console.log('Contents: ' + json);
      }, function(error) {
        console.error('出错了', error);
      });


上面代码中，getJSON是对 XMLHttpRequest 对象的封装，用于发出一个针对 JSON 数据的 HTTP 请求，并且返回一个Promise对象。需要注意的是，在getJSON内部，resolve函数和reject函数调用时，都带有参数。

参考：[阮一峰老师文章](http://es6.ruanyifeng.com/?search=%E8%A7%A3%E6%9E%84&x=0&y=0#docs/promise)
