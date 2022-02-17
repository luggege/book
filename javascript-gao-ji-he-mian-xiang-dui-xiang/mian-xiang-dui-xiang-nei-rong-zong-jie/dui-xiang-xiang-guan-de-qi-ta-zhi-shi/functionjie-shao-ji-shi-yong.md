# Function介绍及使用

## 创建函数方式

1. 函数声明：`funtion fn() {}`
2. 函数表达式\(变量声明\)：`var fn = function() {}`
3. new Function：`var fn = new Function("console.log('1')")`

无参:创建的是空函数; 函数体: 创建的是无参的函数

多个参数: 前边的都是形参,最后一个是函数体

Function接收的所有参数都是字符串形式!!!

## 函数的构造函数Function

在 js 中 使用`Function`可以实例化函数对象。也就是说在 js 中函数与普通对象一样, 也是一个对象类型. 函数是 js 中的一等公民.

1. 函数是对象, 就可以使用对象的动态特性
2. 函数是对象, 就有构造函数创建函数
3. 函数是函数, 可以创建其他对象
4. 函数是唯一可以限定变量作用域的结构

要解决的问题

1. Function 如何使用
2. Function 与函数的关系
3. 函数的原型链结构

## Function 的使用

### 语法:

```js
//Function函数所有的参数全都是字符串
//Function函数的作用就是将所有的参数组合起来，变成一个函数
//1、如果只传一个参数，那么这个函数必然是函数体
//2、如果传多个参数，那么最后一个参数表示函数体，前面的参数代表将要创建的函数的参数
//3、如果不传参数，表示创建一个空函数
new Function(arg1, arg2, arg3, ..., argN, body);
```

### 创建一个打印一句话的函数

```js
//传统的方式
function foo(){
    console.log("你好");
}

//使用Function
var func = new Function("console.log('你好');");
```

这里两种方式创建出来的函数功能是一样的。

### 创建一个空函数

```js
//传统的方式
function foo(){}

//Function 
var func = new Function();
```

### 创建一个有参数的函数

```js
//传统的方式
function foo(num){
    console.log(num);
}
//Function
var func = new Function(){
    "num", "console.log(num);"
};
```

### 练习: 利用 Function 创建一个函数, 要求传入两个数字, 打印其和

```js
var func = new Function(
    'num1','num2','console.log( num1 + num2);'
);
```

### 练习: 利用 Function 创建一个函数, 要求允许函数调用时传入任意个数参数, 并且函数返回这些数字中最大的数字. 练习: 利用 Function 创建一个求三个数中最大数的函数.

```js
// 传统
function foo ( a, b, c ){
    var res = a > b ? a : b;
    res = res > c ? res : c;
    return res;
}

// Function
var func = new Function( 
    'a','b','c',
    'var res = a > b ? a : b;
    res = res > c ? res : c;
    return res;'
)
```



