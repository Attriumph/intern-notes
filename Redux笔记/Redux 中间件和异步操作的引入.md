# Redux中间件和异步操作引入

## 1.中间件
中间件就是一个函数，对store.dispatch方法进行了改造，
在发出 Action 和执行 Reducer 这两步之间，添加了其他功能。


## 2.中间件的使用
别人已经写好，我们直接用就行
例子代码：

    import { applyMiddleware, createStore } from 'redux';
    import createLogger from 'redux-logger';
    const logger = createLogger();

    const store = createStore(
      reducer,
      applyMiddleware(logger)
     );
上面代码中，redux-logger提供一个生成器createLogger，可以生成日志中间件logger。然后，将它放在applyMiddleware方法之中，传入createStore方法，就完成了store.dispatch()的功能增强。

这里有两点需要注意：

（1）createStore方法可以接受整个应用的初始状态作为参数，那样的话，applyMiddleware就是第三个参数了。


    const store = createStore(
      reducer,
      initial_state,
      applyMiddleware(logger)
     );

（2）中间件的次序有讲究。


    const store = createStore(
      reducer,
      applyMiddleware(thunk, promise, logger)
    );

上面代码中，applyMiddleware方法的三个参数，就是三个中间件。有的中间件有次序要求，使用前要查一下文档。比如，logger就一定要放在最后，否则输出结果会不正确。

## 3.异步操作的基本思路
同步操作只要发出一种 Action 即可，异步操作的差别是它要发出三种 Action。

操作发起时的 Action
操作成功时的 Action
操作失败时的 Action
以向服务器取出数据为例，三种 Action 可以有两种不同的写法。
一般是fetch，success，fail三种action

    // 写法一：名称相同，参数不同
    { type: 'FETCH_POSTS' }
    { type: 'FETCH_POSTS', status: 'error', error: 'Oops' }
    { type: 'FETCH_POSTS', status: 'success', response: { ... } }

    // 写法二：名称不同
    { type: 'FETCH_POSTS_REQUEST' }
    { type: 'FETCH_POSTS_FAILURE', error: 'Oops' }
    { type: 'FETCH_POSTS_SUCCESS', response: { ... } }

除了 Action 种类不同，异步操作的 State 也要进行改造，反映不同的操作状态。下面是 State 的一个例子。
一般是pendding， success， fail

    let state = {
      // ... 
      isFetching: true,
      didInvalidate: true,
      lastUpdated: 'xxxxxxx'
    };
上面代码中，State 的属性isFetching表示是否在抓取数据。didInvalidate表示数据是否过时，lastUpdated表示上一次更新时间。

现在，整个异步操作的思路就很清楚了。

操作开始时，送出一个 Action，触发 State 更新为"正在操作"状态，View 重新渲染
操作结束后，再送出一个 Action，触发 State 更新为"操作结束"状态，View 再一次重新渲染
