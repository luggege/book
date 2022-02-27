# 中间件

## node-project-lesson1

## 2.express

npm install express --save npm i -S express

npm install express --save-dev npm i -D express 脚手架工具的安装 npm install -g express-generator

### 2.1为什么使用框架？

app.use\(express.static\(path.join\(\_\_dirname, 'public'\)\)\);

* 原生Node开发，会发现很多问题。比如：
  * 呈递静态页面很不方便，需要处理每个HTTP请求
  * 路由处理不直观清晰,需要写很多字符串判断和正则表达式
  * 不能集中精力写业务，要考虑很多其它的东西
* Express框架致力于解决上述问题。
* 例如,jQuery,简化了dom操作，让我们的关注点从如何去操作dom转变成具体我们要操作dom去干什么。

  **2.2 express介绍**

* express 中文官网[http://www.expressjs.com.cn/](http://www.expressjs.com.cn/)

* Express是目前最流行的基于Node.js的Web开发框架，提供各种模块，可以快速地搭建一个具有完整功能的网站。

* Express有着惊艳的路由能力

  Express中静态资源服务，就是一句话的事儿

  Express与模板引擎配合，直观清晰。

  **2.3 路由**

  路由器，是告知请求者，所请求的ip在哪里，并且把信息发送过去。

  web框架的路由，是告知框架，所请求的http参数应该调用的模块、类、方法在哪里，把请求发送过去。

  ```javascript
  // GET method route
  app.get('/', function (req, res) {
  res.end('GET request to the homepage');
  });
  // POST method route
  app.post('/', function (req, res) {
  res.end('POST request to the homepage');
  });
  ```

  通过模糊匹配路由

  ```javascript
  // 匹配 acd 和 abcd
  app.get('/ab?cd', function(req, res) {
  res.send('ab?cd');
  });
  // 匹配 abcd、abbcd、abbbcd等 匹配n个加号前的字母
  app.get('/ab+cd', function(req, res) {
  res.send('ab+cd');
  });
  // 匹配 abcd、abxcd、abRABDOMcd、ab123cd等 *代表任意
  app.get('/ab*cd', function(req, res) {
  res.send('ab*cd');
  });
  // 匹配 /abe 和 /abcde
  app.get('/ab(cd)?e', function(req, res) {
  res.send('ab(cd)?e');
  });
  ```

  通过正则表达匹配路由

  ```javascript
  // 匹配任何路径中含有 a 的路径：
  app.get(/a/, function(req, res) {
  res.send('/a/');
  });
  // 匹配 butterfly、dragonfly，不匹配 butterflyman、dragonfly man等
  app.get(/.*fly$/, function(req, res) {
  res.send('/.*fly$/');
  });
  ```

  **2.4 中间件**

  **2.4.1 什么是中间件？**

* Express 是一个自身功能极简，完全是由路由和中间件构成一个的 web 开发框架：从本质上来说，一个 Express 应用就是在调用各种中间件。 中间件（Middleware）是一个函数，它可以访问请求对象（request object \(req\)）, 响应对象（response object \(res\)）, 和 web 应用中处于请求-响应循环流程中的中间件，一般被命名为 next 的变量。

* 往往一个http请求发送到服务器，都需要通过很多的判断和处理。 一个请求发送过来----&gt;用户是否已经登录----&gt;用户请求的是什么资源\(静态资源、动态页面、json数据\)----&gt;统计一下用户的请求---&gt;\(如果请求的内容不存在\)返回404

* 中间件的功能包括： 执行任何代码。 修改请求和响应对象。 终结请求-响应循环。 调用堆栈中的下一个中间件。 如果当前中间件没有终结请求-响应循环，则必须调用 next\(\) 方法将控制权交给下一个中间件，否则请求就会挂起。 通过 app.use\(中间件的代码\)使用中间件

  **2.4.2 中间件种类**

  Express 应用可使用如下几种中间件：

  * 内置中间件
  * 第三方中间件

* 错误处理中间件

* 应用级中间件

* 路由级中间件

### 2.4.3 内置中间件

* 介绍

  从 4.x 版本开始，express取消了大部分的内置中间件，除了 express.static, Express 以前内置的中间件现在已经全部单独作为模块安装使用了

* 为什么只留一个中间件

  让express只留一个框，轻量、灵活、便于修改。

### 2.4.4 使用中间件

* 挂载中间件

  app.use\(\[path\],function\)

* 回调函数中的参数

  req, res, next

  next是一个方法，被调用后，继续走下一个中间件。



