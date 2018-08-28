### gulp简介

**gulp**：gulp是前端开发过程中对代码进行**构建的工具，**gulp是基于Nodejs的自动任务运行器， 她能**自动化**地完成 javascript/coffee/sass/less/html/image/css 等文件的的**测试**、**检查**、**合并**、**压缩**、**格式化**、**浏览器自动刷新**、**部署**文件生成，并监听文件在改动后重复指定的这些步骤。在实现上，她借鉴了Unix操作系统的**管道（pipe）**思想，前一级的输出，直接变成后一级的输入，使得在操作上非常简单。

gulp 和 grunt 非常类似，但相比于 grunt 的频繁 IO 操作，gulp 的流操作，能更快地更便捷地完成构建工作。

##### 使用步骤:

1.全局安装gulp

> npm install gulp -g

2.本地项目添加开发依赖（本地安装gulp: 防止gulp版本控制问题，防止全局没装gulp，不能使用gulp的**api**：**.task\(\)/.src\(\)/.dest\(\)/.watch\(\)**）

> npm install --save-dev gulp

![](/assets/import.png)

3.项目根目录新建gulpfile.js文件（默认配置文件）

4.gulpfile.js文件中写需要处理的内容

* require引入需要的模块到gulp
* .task\(\)方法定义任务名称（终端执行gulp, 默认执行default任务）
* .src\(\)引入要处理的文件（返回的是node stream的一个实例，调用**node的api——pipe\(\)**方法返回的也是node stream的一个实例，从而实现管道传输串联的写法。）
* .dest\(\)方法将处理完的文件流重新写入新的位置，如果该目录不存在则会自动创建



