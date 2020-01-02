# Function介绍及使用

## 函数的构造函数Function <a id="&#x51FD;&#x6570;&#x7684;&#x6784;&#x9020;&#x51FD;&#x6570;function"></a>

在 js 中 使用`Function`可以实例化函数对象。也就是说在 js 中函数与普通对象一样, 也是一个对象类型. 函数是 js 中的一等公民.

1. 函数是对象, 就可以使用对象的动态特性
2. 函数是对象, 就有构造函数创建函数
3. 函数是函数, 可以创建其他对象
4. 函数是唯一可以限定变量作用域的结构

要解决的问题

1. Function 如何使用
2. Function 与函数的关系
3. 函数的原型链结构

## Function 的使用 <a id="function-&#x7684;&#x4F7F;&#x7528;"></a>

### 语法: <a id="&#x8BED;&#x6CD5;"></a>

```text
//Function函数所有的参数全都是字符串
//Function函数的作用就是将所有的参数组合起来，变成一个函数
//1、如果只传一个参数，那么这个函数必然是函数体
//2、如果传多个参数，那么最后一个参数表示函数体，前面的参数代表将要创建的函数的参数
//3、如果不传参数，表示创建一个空函数
new
Function
(arg1, arg2, arg3, ..., argN, body);
```

### 创建一个打印一句话的函数 <a id="&#x521B;&#x5EFA;&#x4E00;&#x4E2A;&#x6253;&#x5370;&#x4E00;&#x53E5;&#x8BDD;&#x7684;&#x51FD;&#x6570;"></a>

```text
//传统的方式
function
foo
(
)
{

console
.log(
"你好"
);
}


//使用Function
var
 func = 
new
Function
(
"console.log('你好');"
);
```

这里两种方式创建出来的函数功能是一样的。

### 创建一个空函数 <a id="&#x521B;&#x5EFA;&#x4E00;&#x4E2A;&#x7A7A;&#x51FD;&#x6570;"></a>

```text
//传统的方式
function
foo
(
)
{}


//Function
var
 func = 
new
Function
();
```

### 创建一个有参数的函数 <a id="&#x521B;&#x5EFA;&#x4E00;&#x4E2A;&#x6709;&#x53C2;&#x6570;&#x7684;&#x51FD;&#x6570;"></a>

```text
//传统的方式
function
foo
(
num
)
{

console
.log(num);
}


//Function
var
 func = 
new
Function
(){
"num"
, 
"console.log(num);"
};
```

### 练习: 利用 Function 创建一个函数, 要求传入两个数字, 打印其和 <a id="&#x7EC3;&#x4E60;-&#x5229;&#x7528;-function-&#x521B;&#x5EFA;&#x4E00;&#x4E2A;&#x51FD;&#x6570;-&#x8981;&#x6C42;&#x4F20;&#x5165;&#x4E24;&#x4E2A;&#x6570;&#x5B57;-&#x6253;&#x5370;&#x5176;&#x548C;"></a>

```text
var
 func = 
new
Function
(

'num1'
,

'num2'
,

'console.log( num1 + num2 );'

);
```

### 练习: 利用 Function 创建一个函数, 要求允许函数调用时传入任意个数参数, 并且函数返回这些数字中最大的数字. 练习: 利用 Function 创建一个求三个数中最大数的函数. <a id="&#x7EC3;&#x4E60;-&#x5229;&#x7528;-function-&#x521B;&#x5EFA;&#x4E00;&#x4E2A;&#x51FD;&#x6570;-&#x8981;&#x6C42;&#x5141;&#x8BB8;&#x51FD;&#x6570;&#x8C03;&#x7528;&#x65F6;&#x4F20;&#x5165;&#x4EFB;&#x610F;&#x4E2A;&#x6570;&#x53C2;&#x6570;-&#x5E76;&#x4E14;&#x51FD;&#x6570;&#x8FD4;&#x56DE;&#x8FD9;&#x4E9B;&#x6570;&#x5B57;&#x4E2D;&#x6700;&#x5927;&#x7684;&#x6570;&#x5B57;-&#x7EC3;&#x4E60;-&#x5229;&#x7528;-function-&#x521B;&#x5EFA;&#x4E00;&#x4E2A;&#x6C42;&#x4E09;&#x4E2A;&#x6570;&#x4E2D;&#x6700;&#x5927;&#x6570;&#x7684;&#x51FD;&#x6570;"></a>

```text
// 传统
function
foo
 (
 a, b, c 
)
{

var
 res = a 
>
 b ? a : b;
    res = res 
>
 c ? res : c;

return
 res;
}


// Function
var
 func = 
new
Function
( 
'a'
,

'b'
,

'c'
,

'var res = a 
>
 b ? a : b;res = res 
>
 c ? res : c;return res;'
 )
```
