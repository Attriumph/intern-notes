# Redux-saga框架
>redux-saga 是一个用于管理 Redux 应用异步操作的中间件（又称异步 action）。 redux-saga 通过创建 Sagas 将所有的异步操作逻辑收集在一个地方集中处理，可以用来代替 redux-thunk 中间件。

这意味着应用的逻辑会存在两个地方：
* Reducers 负责处理 action 的 state 更新

* Sagas 负责协调那些复杂或异步的操作
##saga中的sagas
Sagas 可以被看作是在后台运行的进程，Sagas 监听发起的action，然后决定基于这个 action来做什么：
* 是发起一个异步调用（比如一个 fetch 请求）
* 还是发起其他的action到Store
* 甚至是调用其他的 Sagas

##saga中的effects
在 redux-saga 的世界里，所有的任务都通用 yield Effects 来完成（Effect 可以看作是 redux-saga 的任务单元）。Effects 都是简单的 Javascript 对象，包含了要被 **Saga middleware 执行的信息**（打个比方，你可以看到 Redux action其实是一个个包含执行信息的对象）， redux-saga 为各项任务提供了各种Effect创建器，比如调用一个异步函数，发起一个action到Store，启动一个后台任务或者等待一个满足某些条件的未来的 action


参考：[原文更精彩](https://www.jianshu.com/p/7cac18e8d870)
