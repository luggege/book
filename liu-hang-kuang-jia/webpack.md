### webpack

> 打包文件，只能解析js文件，所以需要借助各种loader打包
>
> webpack需要开发者找到入口，对于不同的资源使用不同的loader去处理

#### webpack的使用

> 1. 全局安装webpack\(npm install webpack -g\)
> 2. 搭建一个项目结构
> 3. 编写webpack的配置文件和src文件中的内容
> 4. 本地安装webpack \(npm install webpack -save-dev\)
> 5. 启动 \(webpack --config webpack.develop.config.js\)

#### loader 和 plugin的区别

* 二者都是webpack 功能的扩展。loader职责单一，一个loade就是一个NodeJs模块只是一种转换；
  plugin除了优化打包、压缩，还可以重新定义环境变量（define-plugin）
* loader运行在打包文件之前（预处理）；
  plugin运行在整个生命周期，监听webpack广播出的各种事件，然后在合适的时机通过webpack的API改变输出结果
* 写法
* * loader：是一个函数，入参是上一个loader返回的source，出参是经过处理的source，这也说明了loader是顺序执行的
  * plugin：new出来的，所以是一个类，每个阶段都有响应的钩子



