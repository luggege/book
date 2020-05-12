# 原型链结构

凡是对象就有原型, 原型又是对象, 因此凡是给定义一个对象, 那么就可以找到他的原型, 原型还有原型. 那么如此下去, 就构成一个对象的序列. 称该结构为原型链.

使用构造函数创建出对象, 并且没有利用赋值的方式修改原型, 就说该对象保留默认的原型链.

默认原型链结构是什么样子呢?

```javascript
function Person() {}
var p = new Person();
// p 具有默认的原型链
```

默认的原型链结构就是:

当前对象 -&gt; 构造函数.prototype -&gt; Object.prototype -&gt; null

在实现继承的时候, 有时会利用替换原型链结构的方式实现原型继承, 那么原型链结构就会发生改变

```javascript
function ItcastCollection () {}
ItcastCollection.prototype = [];
var arr = new ItcastCollection();
// arr -> [] -> Array.prototype -> Object.prototype -> null
// var arr = new Array();
```

## 绘制原型链结构

**注意**：函数也有`__proto__`属性，暂时不考虑这个！

观察如下代码，绘制相应的原型链结构图:

```javascript
function Person() {};
var p = new Person();
```

### 对应的原型链结构图为：![](/assets/prototype_cycle)思考：

1. 绘制`{}`的原型链结构图

2. 绘制`[]`的原型链结构图

**注意**：

在 js 中, 所有的对象字面量在解析以后, 就是一个具体的对象了. 那么可以理解为 调用的 对应的构造方法.

* 例如在代码中写上`{}`, 就相当于`new Object()`

* 例如代码中有`[]`, 就相当于`new Array()`

* 例如代码中有`/./`, 就相当于`new RegExp( '.' )`

注意: 在底层理论执行的过程中, 是否有调用构造函数, 不一定. 和浏览器的版本有关.

### 思考：

绘制如下代码的原型链结构:

```javascript
var o = {
    appendTo: function( dom ) {}
};

function DivTag() {}

DivTag.prototype = o;

var div = new DivTag();
```





