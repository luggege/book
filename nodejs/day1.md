# node基础及requirejs/seajs

> 浏览器解析js,目的是为了让计算机可以看懂js

### 引擎

#### 内核---&gt;js引擎

1. 转化 
   * js代码--&gt;机器码/字节码
2. 移植性

   * **node中的js是基于v8引擎的 \(好处: 不用考虑兼容性问题\)**

#### node是一门技术,用的语言就是JavaScript

### 通过nvm来切换node.js版本号

#### Node.js特点

* 轻量,高效

> Node.js最早是运行在linux系统下的

#### node 下的每一个js都是一个模块

### require加载模块机制

* 操作的时候其实是去硬盘中读取js文件,并把曝露的东西放到module对象中去,module这个对象是在内存中的\(缓存\).当第二次再重新执行这个js模块时就走缓存了,不会重新从上到下执行js

## JavaScript 模块化编程

### 网站越来越复杂，js代码、js文件也越来越多，会遇到什么问题？

1.命名冲突

2.文件依赖问题

### 什么是模块化

### 模块化开发演变

#### 全局函数

* 命名冲突
* 文件依赖的问题

#### 对象封装

* 用命名空间的方式进行封装
* 先约定命名的规范的形式
* 对象里面的属性和方法很容易被修改掉，很不安全

#### 划分私有空间

-通过匿名函数自执行的方法封装模块， -可以保护私有变量和方法

#### 模块的维护扩展

* 开闭原则，对修改关闭，对扩展开放。
* 增加了代码的健壮性和容错性

#### 模块的第三方依赖

* 模块职责唯一性
* 把依赖的模块，通过依赖注入的形式，在你的参数上进行体现。

#### 总结

* 最大的问题，规范的问题
* 如果在多人协作开发过程中，会有很大的问题
* 多人协作开发过程中：代码的风格一定要统一

### 模块化规范

> ES6之后有了类class的定义，根据服务器端模块化的思想，也就产生了前端的模块化思想：协同开发，复用别人的模块

#### 浏览器端模块化规范

* AMD
  * RequireJS
* CMD
  * SeaJS
* CommonJS
  * node.js

#### CMD与AMD的区别

* 二者都是异步加载模块
* 对依赖模块的执行时机不同：
* * AMD依赖前置，知道依赖的是谁，立即加载
  * CMD就近依赖，需要把模块变为字符串加载一遍才知道依赖了哪些模块

#### require和import的区别

* 二者都是异步加载
* require运行时调用，故可放在文件任意位置；import是编译时调用，故放在文件开头
* require\(\)拿到的等于是exports对象，需要`let { test } = require('./a.js');`的方式从exports中取出，**值的拷贝**
* ```js
  // module.js
  module.exports = {
      a: function() {
          console.log('exports from module');
      }
  }

  // sample.js
  var obj = require('./module.js');
  obj.a()  // exports from module
  ```
* import\(\)需要与export\(\)对应使用，**值的引用**
* ```js
  // import、export是ES6引入的新规范
  export default function() {}

  import test from './a.js'
  ```

### SeaJS

#### 基本使用

#### 定义模块 define

* 定义模块 define\(function\(\){}\)
* 函数体内的方法属性都属于这个方法，对外有封装性;解决了命名冲突问题，使js代码有了封装性
* 直接调用 jQuery 插件等非标准模块的方法 [http://my.oschina.net/briviowang/blog/208587](http://my.oschina.net/briviowang/blog/208587)

#### 启动模块 seajs.use

* 加载入口模块，我们把define定义的js就叫模块
* 这个用于在html代码里面的加载

  **加载模块 require**

  -加载文件依赖、模块依赖的，用于define函数体内

  **暴露接口 exports 和 module.exports**

* module.exports曝露出一个完整的对象，只能扔一次只能曝露出来一个

* exports是module.exports的别名，可以用来单个属性、方法、对象的曝露，用.的形式,exports能做的事情module.exports也可以做

* 使用场景用.属性的形式曝露属性和方法的时候，而且是多个的时候用exports

* module.exports直接等于的方式用，直接等于一个方法属性对象等等~~~

  **requirejs**

  与seajs的区别

  requirejs是优先加载的

  seajs是懒加载的，就是有拖延症，用的时候才加载

  [http://www.requirejs.cn/](http://www.requirejs.cn/)

#### `SeaJS` 的使用

* 定义模块 `define`作用域就在define的函数体里，三个参数require、exports、module
* 加载模块 `require`
  * 在一个模块系统中，`require` 加载过的模块会被缓存
  * 默认 `require` 是同步加载模块的
* 暴露接口 `exports` 和 `module.exports` exports是module.exports的别名，exports能做什么，module.exports就能做什么，module.exports是全局变量，exports是局部变量
* 启动模块系统 `seajs.use(callback)`
  * seajs.use 和 Document 的 ready 没有任何关系
  * 要想保证 文档结构加载完毕再执行你的 js 代码，一定要在 seajs.use 内部通过 window.onload 或者 $\(function\(\){}\)
* 分清楚前台模块化和node中的模块化的区别
* 掌握模块化的思想



