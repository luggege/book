### let 和 const 命令

#### let

* 基本用法
* * let只在代码块中有效

```js
// let声明的变量只在代码块中有效
{
    let i = 1;
    var j = 2;
}
console.log(i)  // 报错
console.log(j)  // 2

for(let i = 0; i < 10; i++){}
i // i is not defined
for(var i = 0; i < 10; i++){}
i // 10
```

* * for循环中的经典使用

```js
var a = []
// var定义的i全局有效
for(var i = 0; i < 10; i++){
    a[i] = function(){
        console.log(i)
    }
}
a[5]()    //10
```

```js
// 循环生成10个子块级作用域，相互独立
for(let i = 0; i < 10; i++){
    a[i] = function(){
        console.log(i)
    }
}
a[7]()    // 7
```

```js
// 或者使用闭包
var array  = []
for(var i = 0; i < 10; i++){
    // 块级作用域的出现，取代了匿名立即执行函数
    (function(i){
        array[i] = function(){
            console.log(i)
        }
    })(i)
}
array[7]()  // 7
```

```js
// 父作用域与子作用域相互独立
// 父作用域
for(let i = 0; i < 3; i++){
    // 子作用域，相互独立
    let i = 'abc'
    console.log(i)   // abc（3次）
}
```

* 不允许变量提升

```js
console.log(bar)      // undefined
var bar = 2

console.log(bar)      // Uncaught ReferenceError: bar is not defined
let bar = 2
const bar = 111
```

* 暂时性死区（在代码块内，let声明变量之前，该变量不可用，不会受外部的影响）

```js
tmp = '222'
if(true){
    tmp = 'abc'
    console.log(tmp)     // Uncaught ReferenceError: Cannot access 'tmp' before initialization

    let tmp
    console.log(tmp)     // undefined

    tmp = 123
    console.log(tmp)     // 123
}
```

* * 因为暂时性死区的原因，typeof不是一个百分百安全的操作，因为申明之前不可用

  ```js
  typeof x                // 报错 Uncaught ReferenceError: a is not defined
  let x

  // 直接对未声明的变量使用typeof反而不会报错
  typeof a           // undefined
  ```

  ```js
  // 参数x等于参数y，此时y还没有声明，属于“死区“
  function bar(x = y, y = 2){
      return [x,y]
  }
  bar()     // VM1986:1 Uncaught ReferenceError: Cannot access 'y' before initialization              

  function bar(x = 2, y = x){
      return [x,y]
  }
  bar()   // [2, 2]
  ```

  ```js
  var x = x;  // 不报错
  // 变量未声明就使用
  let x = x;  // Uncaught ReferenceError: x is not defined
  ```
* 不允许重复声明

```js
// 不报错
function foo(){
    var a = 10;
    var a = 20;
}

// Uncaught SyntaxError: Identifier 'a' has already been declared
function foo(){
    var a = 10;
    let a = 20;
}
// Uncaught SyntaxError: Identifier 'a' has already been declared
function foo(){
    let a = 10;
    let a = 20;
}
// Uncaught SyntaxError: Identifier 'a' has already been declared
function foo () {
    let a = 10
    var a = 20
}
```

```js
// 因此函数内部不能重复声明
function fn(arg){
    let arg
}
fn()        // Uncaught SyntaxError: Identifier 'arg' has already been declared

function fn(arg){
    {
        let arg
    }
}
fn()        //不报错
```

##### 为什么使用let替代var

> 因为let有块级作用域的限制，var没有，容易造成变量污染

* 场景一：内层变量覆盖外层变量

```js
var tmp = new Date()
function f() {
    console.log(tmp)
    if (false) {
        var tmp = 'Hello world'   // var tmp 变量提升覆盖外层变量
    }
}
f()  // undefined
```

* 场景二：用来计数的循环变量泄漏为全局变量

```js
var s = 'hello'
for (var i = 0; i < s.length; i++) {
    console.log(s[i])
}
console.log(i)  // 5
```

##### let只能出现在当前作用域的顶层

```js
if (true) let x = 1   // Uncaught SyntaxError: Lexical declaration cannot appear in a single-statement context

// 严格模式下，函数只能申明在当前作用域的顶层
'use strict'
if (true) function f() {}    // Uncaught SyntaxError: In strict mode code, functions can only be declared at top level or inside a block.

'use strict'
if (true) {	function f() {} } // undefined
```

##### 顶层对象的属性

> 顶层对象：在浏览器指的是window，在Node指的是global。而window实体含义是浏览器的窗口对象，顶层对象也有一个实体含义，混为一谈不合适

* ES5中，顶层对象的属性和全局变量是一样的，这也是javascript语言设计最大的败笔之一
* ES6中，作出改变：var和function申明的全局变量，依旧是顶层对象的属性，let、const、class 申明的全局变量不属于顶层对象的属性，全局变量逐步与顶层对象的属性脱钩

```js
var a = 111
window.a  // 111

let b = 222
window.b. // undefined
```

##### globalThis 对象

> JavaScript 语言存在一个顶层对象，它提供全局环境（即全局作用域），所有代码都运行在这个环境，使用this 可以拿到这个顶层对象，但是不同环境的this 不同

* 全局环境中
* * this 返回顶层对象
  * Node.js中，this 是当前模块
  * ES6中，this 返回的是 undefined
* 函数里的this
* * 如果函数不是作为对象的方法运行，单纯作为函数运行，this 会指向顶层对象
  * 如果是严格模式下，this 返回 undefined

综上所述，很难找到一种方法，在所有情况下，都取到顶层对象，下面是两种可以勉强使用的方法

```js
(typeof window !== 'undefined'
 ? window
 : (typeof process === 'object' &&
 typeof require === 'function' &&
 typeof global === 'object')
 ? global
 : this);
```

```js
var getGlobal = function () {
 if (typeof self !== 'undefined') { return self; }
 if (typeof window !== 'undefined') { return window; }
 if (typeof global !== 'undefined') { return global; }
 throw new Error('unable to locate global object');
};
```

**ES2020中，globalThis可以在任何环境中拿到顶层对象，指向全局环境下的this**

#### const：指变量指向的内存地址的值不可修改，如果定义的是复合类型只是指针不可修改，不能保证对象的结构改变

* const声明常量，值不可修改

```js
const aaa = 111
aaa = 222
// Uncaught TypeError: Assignment to constant variable
```

* 声明时必须立即初始化，否则报错

```js
const bbb
bbb = 111
// Uncaught SyntaxError: Missing initializer in const declaration
```

* 和let一样，不可重复声明

```js
let bar = 100
const bar = 200
// VM1276:2 Uncaught SyntaxError: Identifier 'bar' has already been declared
```

* 和let一样，存在块级作用域，未声明前不可用

```js
if(true){
    const eee = 666
}
console.log(eee)
// Uncaught ReferenceError: eee is not defined

console.log(ddd)
const ddd = 100
// Uncaught ReferenceError: Cannot access 'ddd' before initialization
```



