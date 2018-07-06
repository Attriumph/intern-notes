# React-router 4

## React-router和React-router-dom


### React-router
> React-router提供了一些router的核心api，包括Router, Route, Switch等，但是它没有提供dom操作进行跳转的api。

### React-router-dom
> React-router-dom提供了BrowserRouter, Route, Link等api,我们可以通过dom的事件控制路由。例如点击一个按钮进行跳转，大多数情况下我们是这种情况，所以在开发过程中，我们更多是使用React-router-dom。安装很简单npm i react-router-dom --save.

## React-router-dom的核心用法
HashRouter和BrowserRouter, 它们两个是路由的基本，就像盖房子必须有地基一样，我们需要将它们包裹在最外层，**只要选择其一就可以了**。现在讲它们的不同：

* HashRouter

      如果你使用过react-router2或3或者vue-router，你经常会发现一
      现象就是url中会有个#，例如localhost:3000/#，HashRouter就会
      出现这种情况，它是通过hash值来对路由进行控制。如果你使
      用HashRouter，你的路由就会默认有这个#。



* BrowserRouter

      很多情况下我们则不是这种情况，我们不需要这个#，因为它看起来很
      怪，这时我们就需要用到BrowserRouter。它的原理是使用HTML5 history API (pushState, replaceState, popState)来使你的内容随着url动态改变的.



##Route组件
Route是路由的一个原材料，它是控制路径对应显示的组件。我们经常用的是exact、path以及component属性。

* exact控制匹配到/路径时不会再继续向下匹配
* path标识路由的路径
* component表示路径对应显示的组件

后面我们将结合NavLink完成一个很基本的路由使用。同时我们可以设置例如/second/:id的方式来控制页面的显示，这需要配合Link或者NavLink配合使用，下面我们会提到

### Link和NavLink的选择
两者都是可以控制路由跳转的，不同点是NavLink的api更多，更加满足你的需求。

#### Link
主要api是to，to可以接受string或者一个object，来控制url。使用方法如下

### NavLink
它可以为当前选中的路由设置类名、样式以及回调函数等。

```javascript

ReactDOM.render{
  <BrowserRouter basename="/calendar">
    <div>
      <div>
        <ul>
          <li>
            <NavLink exact activeClassName="selected" to="/">home</NavLink>
          </li>
          <li>
            <NavLink activeClassName="selected" to="/second/1234">second</NavLink>
          </li>
        </ul>

      <Route exact path="/" component={ home }></Route>
      <Route exact path="/second/:id" component={ second }></Route>
    </div>    
}
```
exact用于严格匹配，匹配到/则不会继续向下匹配，to则是控制跳转的路径，activeClassName是选中状态的类名，我们可以为其添加样式。我们在/second后面添加1234来想路由中传递信息，这结合了上面Route中的/second/:id，结合使用了.


上面的1234内容显示需要用到match，我们马上就来讲一下。
### match
match是在使用router之后被放入props中的一个属性，在class创建的组件中我们需要通过this.props.match来获取match之中的信息。


### Switch
 常常会用来包裹Route，它里面不能放其他元素，用来只显示一个路由。

 refer: [原文更精彩](http://react-china.org/t/react-router4/15843)
