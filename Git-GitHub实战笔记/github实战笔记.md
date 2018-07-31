# GitHub 实战笔记

## 提交pr和issue注意点
1） 提的 pr 名字都统一叫：[NM]  主题XXX —— xxx nm 表示 no merge 的意思，名字统一这样关联 issue 的时候比较好看，知道这个 pr 做了什么，后面的
   xxx 表示当前修改的什么场景，小程序、app、pc 端、移动端等
    * NM: no merger
    * WIP: work in process
2） issue pr 写的内容一样的话，那开一个 issue 就没有意义了，要么都写在 issue 里，要么写在 pr 里，且写的内容最好简单明了。
   简单列表一下具体修改什么了，如果有没完成的就用 checkbox 来写，如果都已经完成了，直接 - markdown 来写就可以了
   记住一点就是，易读啊。写完之后 preview 的时候，能很直观的看到你修改的内容，再提 pr 或 issue

## 2.commit message书写规范

        格式： <type>(<scope>): <subject>
        // eg: feat(homepage): add new button, resolve #134
> 1.type 代表某次提交的类型，比如是修复一个 bug 还是增加一个新的 feature 。所有的 type 类型如下：

* feat: 新增 feature
* fix: 修复 bug
* docs: 仅仅修改了文档，比如 README, CHANGELOG, CONTRIBUTE 等等
* style: 仅仅修改了空格、格式缩进等等，不改变代码逻辑
* refactor: 代码重构，没有加新功能或者修复bug
* perf: 优化相关，比如提升性能、体验
* test: 测试用例，包括单元测试、集成测试等
* chore: 日常维护等杂项
* flow: 改变构建流程、或者增加依赖库、工具等
* revert: 回滚到上一个版本

> 2. scope 用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。也可以是影响了哪个模块。

> 3.subject 是 commit 目的的简短描述，不超过 50 个字符。如果需要的话，可以添加一个链接到 issue 地址或者其它文档，或者关闭某个 issue。结尾不加逗号。第一个字母不用大写。中英不限。动词可以不用过去式。


**参考：**[来自这里](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)
