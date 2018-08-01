# 自定义组件

## 为什么使用自定义组件
 * 不同的页面中重复使用；
 * 将复杂的页面拆分成多个低耦合的模块，有助于代码维护。

   ps：自定义组件在使用时与基础组件非常相似。

## 自定义组件的创建和使用
### 1.创建自定义组件
   一个自定义组件由 json wxml wxss js 4个文件组成。

   * 要编写一个自定义组件，首先需要在 json 文件中进行自定义组件声明（将 component 字段设为 true 可这一组文件设为自定义组件）：

          {
            "component": true
          }

   * 同时，还要在 wxml 文件中编写组件模版，在 wxss 文件中加入组件样式。

   代码示例：

      <!-- 自定义组件WXML结构 -->
      <view class="inner">
      {{innerText}}
      </view>

      // 自定义组件样式
      .inner {
        color: red;
        }

   **注意：在组件wxss中不应使用ID选择器、属性选择器和标签名选择器。（因为我们使用自定义组件本身就是为了重复使用代码）**

   * 在自定义组件的 js 文件中，需要使用 Component() 来注册组件，并提供组件的属性定义、内部数据和自定义方法。
   其中，组件的属性值和内部数据将被用于组件 wxml 的渲染，其中，属性值是可由组件外部传入的。

   代码示例：

    Component({
     properties: {
       // 这里定义了innerText属性，属性值可以在组件使用时指定
       innerText: {
         type: String,
         value: 'default value',
       }
     },
     data: {
       // 这里是一些组件内部数据
       someData: {}
     },
     methods: {
       // 这里是一个自定义方法
       customMethod: function(){}
     }
   })

### 2.使用自定义组件
   使用已注册的自定义组件前，首先要在**使用组件页面**的 json 文件中进行引用声明。此时需要提供每个自定义组件的标签名和对应的自定义组件文件路径：

    {
     "usingComponents": {
       //component-tag-name 是自己给组件起的名字
       "component-tag-name": "path/to/the/custom/component"
     }
    }
   这样，在页面的 wxml 中就可以像使用基础组件一样使用自定义组件。节点名即自定义组件的标签名，节点属性即传递给组件的属性值。

   代码示例：

    <view>
     <!-- 以下是对一个自定义组件的引用 -->
     <component-tag-name inner-text="Some text"></component-tag-name>
    </view>
   自定义组件的 wxml 节点结构在与数据结合之后，将被插入到引用位置内。

参考：https://developers.weixin.qq.com/miniprogram/dev/framework/custom-component/
