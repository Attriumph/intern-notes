
# npm install

使用 npm 安装 package 有两种方式：本地（当前项目路径）安装 或者 全局安装。

你选择哪种安装方式取决于你将如何使用这个包：

* 如果你只是想在当前项目里用 require() 加载使用，那你可以安装到本地
        npm install 默认就是安装到本地的
* 如果你想要在命令行里直接使用，比如 grunt CLI，就需要安装到全局了
        npm install -g <package-name>

npm install 默认会安装 package.json 中 dependencies 和 devDependencies 里的所有模块。

如果想只安装 dependencies 中的内容，可以使用 --production 字段：

        npm install --production

### 安装参数 --save 和 --save -dev
添加依赖时我们可以手动修改 package.json 文件，添加或者修改 dependencies devDependencies 中的内容即可。

另一种更酷的方式是用命令行，在使用 npm install 时增加 --save 或者 --save -dev 后缀：

        npm install <package_name> --save
        // 表示将这个包名及对应的版本添加到 package.json的 dependencies

        npm install <package_name> --save-dev
        // 表示将这个包名及对应的版本添加到 package.json的 devDependencies

参考文章：[精彩原文](https://blog.csdn.net/u011240877/article/details/76582670)
