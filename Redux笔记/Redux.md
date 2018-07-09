# Redux笔记
## 1.Redux设计思想
Redux 的设计思想很简单，就两句话。

（1）Web 应用是一个状态机，视图与状态是一一对应的。

（2）所有的状态，保存在一个对象里面（store的快照state）。

## 2.重点概念理解

###2.1 Store
  **Store 保存数据的容器。**
  整个应用只能有一个 Store。Redux 提供createStore这个函数，用来生成 Store。


    import { createStore } from 'redux';
    const store = createStore(fn);

上面代码中，createStore函数接受另一个函数作为参数，返回新生成的 Store 对象。**一般传reducer函数，让reducer自动监听store变化**
###2.2  State
Store对象包含所有数据。如果想得到某个时点的数据，就要对 Store 生成快照。这种时间点的数据集合，就叫做 State。

当前时刻的 State，可以通过store.getState()拿到。


    import { createStore } from 'redux';
    const store = createStore(fn);

    const state = store.getState();
Redux 规定， 一个 State 对应一个 View。只要 State 相同，View 就相同。你知道 State，就知道 View 是什么样，反之亦然。

## 2.3 Action
State 的变化，会导致 View 的变化。但是，用户接触不到 State，只能接触到 View。所以，State 的变化必须是 View 导致的。**Action 就是 View 发出的通知，表示 State 应该要发生变化了。**

Action 是一个对象。其中的type属性是必须的，表示 Action 的名称。其他属性可以自由设置。

    const action = {
      type: 'ADD_TODO',
      text
    };

  但是，veiw通常要发很多action，所以我们用函数来生成aciton---Action Creator

    const ADD_TODO = '添加 TODO';

    function addTodo(text) {
        return {
          type: ADD_TODO,
          text
        }
      }

      const action = addTodo('Learn Redux');

###2.4 store.dispatch

**store.dispatch()是 View 发出 Action 的唯一方法。**


    import { createStore } from 'redux';
    const store = createStore(fn);

    store.dispatch({
      type: 'ADD_TODO',
      payload: 'Learn Redux'
      });
上面代码中，store.dispatch接受一个 Action 对象作为参数，将它发送出去。

###2.5 Reducer
**Store 收到 Action 以后**，必须给出一个新的 State，这样 View 才会发生变化。这种 State 的计算过程就叫做 Reducer。

Reducer 是一个函数，它接受 Action 和当前 State 作为参数，返回一个新的 State。

    const reducer = function (state, action) {
      // ...
      return new_state;
    };

  **store.dispatch方法会触发 Reducer 的自动执行。为此，Store 需要知道 Reducer 函数，做法就是在生成 Store 的时候，将 Reducer 传入createStore方法。**


    import { createStore } from 'redux';
    const store = createStore(reducer);

###2.6 store.subscribe()
Store 允许使用store.subscribe方法设置监听函数，一旦 State 发生变化，就自动执行这个函数。

    import { createStore } from 'redux';
    const store = createStore(reducer);

    store.subscribe(listener);
显然，只要把 View 的更新函数（对于 React 项目，就是组件的render方法或setState方法）放入listen，就会实现 View 的自动渲染。

## 3.Redux工作流程
* 首先，用户在view里发出 Action。

      store.dispatch(action);

* 然后，Store 自动调用 Reducer（因为dispatch会自动调用），并且传入两个参数：当前 State 和收到的 Action。 Reducer 会返回新的 State 。

      let nextState = todoApp(previousState, action);
* State 一旦有变化，Store 就会调用监听函数。

      // 设置监听函数
      store.subscribe(listener);

* listener可以通过store.getState()得到当前状态。如果使用的是 React，这时可以触发重新渲染 View。

      function listerner() {
        let newState = store.getState();
        component.setState(newState);   
      }

### 4. Provider组件
provider功能主要为以下两点：

* 在原应用组件上包裹一层，使原来整个应用成为Provider的子组件
* 接收Redux的store作为props
