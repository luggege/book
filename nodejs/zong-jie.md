# 总结

## node-lesson1

### 模块化开发复习

#### 什么是模块化

* 现实中的模块化
  * 生产效率高
  * 维护方便，成本低
* 程序中的模块化
  * 开发效率高 一次编写多次使用
  * 方便维护了（维护的成本更低）模块之间有高耦合低内聚的特点
* 为什么要在 程序 中使用 模块化的开发方式
  * 命名冲突
  * 文件依赖

#### `SeaJS` 的使用

* 定义模块 `define`作用域就在define的函数体里，三个参数require、exports、module
* 加载模块 `require`
  * 在一个模块系统中，`require` 加载过的模块会被缓存
  * 默认 `require` 是同步加载模块的
* 暴露接口 `exports` 和 `module.exports` exports是module.exports的别名，exports能做什么，module.exports就能做什么
* 启动模块系统 `seajs.use(callback)`
  * seajs.use 和 Document 的 ready 没有任何关系
  * 要想保证 文档结构加载完毕再执行你的 js 代码，一定要在 seajs.use 内部通过 window.onload 或者 $\(function\(\){}\)
* 分清楚前台模块化和node中的模块化的区别
* 掌握模块化的思想

### 什么是 Node?

* [https://nodejs.org/en/](zong-jie.md)
* node是js运行环境基于v8引擎

  特点用事件驱动、无阻塞的io模型

  优势轻量、高效

* node是门技术不是语言

  java java

  .net c\#

  node js

* Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.

  * JavaScript runtime JavaScript 运行时
  * Chrome's V8 JavaScript engine Chrome 浏览器 V8 引擎
  * Node.js 是一个 构建于 谷歌的 Chrome 浏览器的 V8 引擎之上的一个 `JavaScript运行时` 环境
  * Node.js可以解析和执行 JavaScript 代码

* Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient.
  * event-driven 事件驱动模型
  * non-blocking I/O model 非阻塞IO模型 IO（input/output）输入与输出
  * lightweight\[ˈlaɪtweɪt\] 轻量级
  * 在软件开发行业中，轻量级标识褒义词
  * 轻量级也就意味着 运行速度快
  * 轻量级也就意味着有更好的 跨平台 特性（平台的差异性，兼容性）
  * efficient\[ɪˈfɪʃnt\] 高效的
  * Node.js的 事件驱动和非阻塞IO模型使得Node.js本身非常的轻量和高效
* Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.
  * package ecosystem npm 包生态系统 npm
  * largest 最大的
  * open source libraries 开源库
  * 理论意义上 开源就表示有成熟的社区，开放源代码
  * Node.js 的npm包生态系统，是世界上 最大的 开源库 生态系统
  * 以前的 客户端中 JavaScript 库 散列在互联网的各个地方
  * npm 就是 把大家经常使用的一些开源库 给 组织到了一起

Node 是一个可以解析和执行 JavaScript 代码的 运行时环境

* Node.js 的作者
  * 瑞恩.达尔

#### Node 的实现结构

* V8 JavaScript 解析执行引擎 ECMAScript
* 中间层 （提供了文件操作、网络操作登陆接口）更加接近操作系统的接口供开发人员使用
* 硬件层

### 安装与配置

#### 3m安装法 nvm npm nrm

#### 安装包的方式安装

* 问题1：安装了node 没有卸载 2:32和64搞混了 3：；拼写错误，路径错误------&gt;老师眼力
* 下载地址：
* 一路下一步 next
* 如何确认是否安装成功：
  * `win + r` ，然后输入 `cmd` ，然后敲回车 就可以进入 cmd 控制台

#### nvm 安装和管理我们的 Node.js版本

```text
nvm的安装方式，node.js version manager 是一个node的版本管理工具

为了解决node版本切换问题

右键在此电脑上点击一下--》属性---》系统---》高级系统设置---》环境变量

控制面板---》系统---》高级系统设置---》环境变量

NVM_HOME---C:\dev\nvm

NVM_SYMLINK--C:\dev\nodejs

新建一个path %NVM_HOME%;%NVM_SYMLINK%
```

nvm 用法

查看版本号

nvm list

用哪个版本（已经下载过的版本）

nvm use 版本号

nvm use 版本号 32

下载相对应版本

nvm install 版本号

nvm install 版本号 32

nvm下载的是二进制版本

### 控制台基本使用

允许用户可以在终端命令台中与操作系统交互，其实就是输入与输出

#### 如何打开cmd

1. 通过 按 window 键，输入 `cmd` 打开cmd程序
2. 通过 `win+r` 输入 `cmd`，敲回车就可以进入

#### 基本命令

* `dir` directory 列出当前目录下所有的条目
  * 别名 `ls` 在 powershell 中可以使用
* `cd` change directory 切换目录

```text
切换到当前目录下的 Desktop 目录

当想切换到当前目录的时候，最好使用 cd ./ 相对路径的形式

C:\Users\iroc>cd Desktop

C:\Users\iroc\Desktop>

在Windows 上切换盘符：

`d:`

切换绝对路径之后再同一个盘符下才有效

切换到上一级目录

C:\Users\iroc\Desktop\code\seajs>cd ../

C:\Users\iroc\Desktop\code>

连续进入多级目录

C:\Users\iroc\Desktop\code>cd seajs/a

C:\Users\iroc\Desktop\code\seajs\a>
```

* `cls` clear screen 清屏

  * 别名 clear 在widnows中的 `powershell` 中可以使用

  windows下的寻址用\反斜杠

#### path 环境变量

目的是为了在控制台中的任何目录都可以快速打开或者使用该可执行文件

环境变量就是用来存储系统级别的变量

* 添加环境变量
  * 我的电脑 -&gt; 右键选择属性 -&gt; 高级系统设置 -&gt; 切换到`高级`面板 -&gt; 环境变量
  * 第一种方式：直接把可执行文件所属的目录 放到 PATH 环境变量中（如果没有PATH环境变量，自己新建）
  * 第二种方式：新建一个环境变量，变量名规范：逻辑名\_HOME 变量值：该可执行文件所属的目录
  * 注意：无论是直接添加的路径还是引用的变量名，一定要用 英文的分号 区分开
  * 引用变量名的时候，变量名两边都是 `%`

`> feiq`

当你在控制台中输入一个程序的名字的时候，cmd 默认把它当成一个可执行文件去执行了，

优先找当前目录下是否有没有一个叫做feiq.exe 的可执行文件，如果有，直接执行打开

如果没有，cmd会进入 path 环境变量中 一个目录一个目录的挨着查找里面是否有该可执行文件

### REPL\(Read-eval-print-loop\) 运行环境

用来测试一下代码的，repl和chrome的控制台很像

* 通过在控制台中输入 `node` 敲回车就可以计入 REPL 运行环境
* 通过在REPL运行环境中 连续按两次 `Ctrl+C` 就可以退出 REPL 运行环境

### 执行js文件

用node执行js文件，文件在当前目录下----&gt;node +文件名

如果不在当前目录下，node +文件路径的形式执行

相对路径

./当前路径

../上级目录

绝对路径执行js的方式

node c:\Users\cena\Desktop\code\01helloworld.js

### Global

global和window很像，都是全局对象

### CONSOLE

```text
断言 是用来测试用的

断言就是假定一个条件，如果条件成立则不输出任何内容，如果条件不成立则报错还要输出想要输出的内容。

console.assert(条件,条件不成立输出的内容);

var foo=3;

console.assert(foo==3,"失败");

time() timeEnd()成对出现，计算在两个方法中间的代码的运行时间，传入的参数要一致

console.time('test');

console.timeEnd('test1');
```

#### **dirname 和** filename

\_\_dirnamee 用来找到当前文件夹的路径

\_\_filename 用来去到当前文件的路径

不知道代码要才哪使用的时候，用于灵活的写代码取路径的时候。

它们属于模块作用域，可以直接使用

它们两个用来获取路径的，一般用于操作文件路径的时候，才会用到

### process

process 是一个全局可用对象，用来和我们现在启动中的node进行交互的

process.version取版本号

在控制台做标准输出

process.stdout.write\(`123123`\);

process.pid：当前进程的进程号。

process.version：Node的版本，比如v0.10.18。

process.platform：当前系统平台，比如Linux。

process.env：指向当前shell的环境变量，比如process.env.HOME。

process.stdout：指向标准输出。

process.stdin：指向标准输入。

process.stderr：指向标准错误。

### 模块系统

### node.js模块化

```text
一个js文件在node里面我们就理解为一个模块

require用来加载模块

module.exports用来曝露属性和方法的，因为模块有封装性，需要打破封装性曝露方法和属性来

exports是module.exports的别名，exports可以做的事情，module.exports都可以做，exports只能用.的形式曝露属性和方法
```



