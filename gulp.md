### gulp简介

**gulp**：gulp是前端开发过程中对代码进行**构建的工具，**gulp是基于Nodejs的自动任务运行器， 她能**自动化**地完成 javascript/coffee/sass/less/html/image/css 等文件的的**测试**、**检查**、**合并**、**压缩**、**格式化**、**浏览器自动刷新**、**部署**文件生成，并监听文件在改动后重复指定的这些步骤。在实现上，她借鉴了Unix操作系统的**管道（pipe）**思想，前一级的输出，直接变成后一级的输入，使得在操作上非常简单。

gulp 和 grunt 非常类似，但相比于 grunt 的频繁 IO 操作，gulp 的流操作，能更快地更便捷地完成构建工作。

##### 使用步骤:

1.全局安装gulp

> npm install gulp -g

2.本地项目添加开发依赖

> npm install --save-dec gulp

3.

