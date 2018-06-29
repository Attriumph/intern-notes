# React-redux库

## 组件分类
React-Redux 将所有组件分成两大类：UI 组件（presentational component）和容器组件（container component）。
**UI 组件负责 UI 的呈现，容器组件负责管理数据和逻辑。**
React-Redux 规定，所有的 UI 组件都由用户提供，容器组件则是由 React-Redux 自动生成。也就是说，用户负责视觉层，状态管理则是全部交给它。

## connect()
React-Redux 提供connect方法，用于从 UI 组件生成容器组件。connect的意思，就是将这两种组件连起来。

    import { connect } from 'react-redux'
    const VisibleTodoList = connect()(TodoList);

上面代码中，TodoList是 UI 组件，VisibleTodoList就是由 React-Redux 通过connect方法自动生成的容器组件。

但是，因为没有定义业务逻辑，上面这个容器组件毫无意义，只是 UI 组件的一个单纯的包装层。为了定义业务逻辑，需要给出下面两方面的信息。

（1）输入逻辑：外部的数据（即state对象）如何转换为 UI 组件的参数

（2）输出逻辑：用户发出的动作如何变为 Action 对象，从 UI 组件传出去。

因此，connect方法的完整 API 如下。


    import { connect } from 'react-redux'

    const VisibleTodoList = connect(
      mapStateToProps,
      mapDispatchToProps
      )(TodoList)
上面代码中，connect方法接受两个参数：mapStateToProps和mapDispatchToProps。它们定义了 UI 组件的业务逻辑。前者负责输入逻辑，即将state映射到 UI 组件的参数（props），后者负责输出逻辑，即将用户对 UI 组件的操作映射成 Action。
## provider组件
React-Redux 提供Provider组件，可以让容器组件拿到state。
