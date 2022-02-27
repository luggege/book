# let 和 const 命令

## let

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
// for循环中的经典使用
var a = []
// var定义的i全局有效
for(var i = 0; i < 10; i++){
    a[i] = function(){
        console.log(i)
    }
}
a[5]()    //10

// 循环生成10个子块级作用域，相互独立
for(let i = 0; i < 10; i++){
    a[i] = function(){
        console.log(i)
    }
}
a[7]()    // 7

// 或者使用闭包
var array  = []
for(var i = 0; i < 10; i++){
    (function(i){
        array[i] = function(){
            console.log(i)
        }
    })(i)
}
array[7]()  // 7

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
// 不报错
var x = x;
// （变量未声明就使用）Uncaught ReferenceError: x is not defined
let x = x;
```

* 不允许重复声明

```javascript
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
function foo(){
    let a = 10;
    let a = 20;
}

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

## const（指变量指向的内存地址的值不可修改，如果定义的是复合类型只是指针不可修改，不能保证对象的结构改变）

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



