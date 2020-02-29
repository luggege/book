# JavaScript预解析

JavaScript是解释型的语言，但是他并不是真的在运行的时候逐句的往下解析执行。

我们来看下面这个例子：

```javascript
fn();

function fn(){
     alert("Funciton has been called");
}
```

在上面这段代码中，函数func的调用是在其声明之前，如果说JavaScript代码真的是逐句的解析执行，那么在第一句调用的时候就会出错，然而事实并非如此，上面的代码可以正常执行，并且alert出来`Function has been called`。

**所以，可以得出结论，JavaScript并非仅在运行时简简单单的逐句解析执行！**

## JavaScript 预解析 <a id="javascript-&#x9884;&#x89E3;&#x6790;"></a>

JavaScript引擎在对JavaScript代码进行解释执行之前，会对JavaScript代码进行**预解析**，在预解析阶段，会将以关键字  **var** 和** function **开头的语句块提前进行处理。

_关键问题是怎么处理呢？_

当**变量**和**函数**的声明处在作用域比较靠后的位置的时候，变量和函数的声明会被提升到**作用域的开头**。

重新来看上面的那段代码

```javascript
fn();

function fn(){
     alert("Funciton has been called");
}
```

由于JavaScript的预解析机制，上面的代码就等效于：

```javascript
function fn(){
     alert("Funciton has been called");
}

fn();
```

看完函数声明的提升，再来看一个变量声明提升的例子：

```javascript
alert(a);

var a = 1;
```

由于JavaScript的预解析机制，上面这段代码，alert出来的值是**`undefined`**，如果没有预解析，代码应该会直接报错`a is not defined`，而不是输出值。

Wait a minute, 不是说要提前的吗？那不是应该alert出来1，为什么是`undefined`?

那么在这里有必要说一下`声明`、`定义`、`初始化`的区别。其实这几个概念是C系语言的人应该都比较了解的。

| 行为 | 说明 |
| :--- | :--- |
| 声明 | 告诉编译器/解析器有这个变量存在，这个行为是不分配内存空间的，在JavaScript中，声明一个变量的操作为：`var a;` |
| 定义 | 为变量分配内存空间，在C语言中，一般声明就包含了定义，比如：`int a;`但是在JavaScript中，`var a;`这种形式就只是声明了。 |
| 初始化 | 在定义变量之后，系统为变量分配的空间内存储的值是不确定的，所以需要对这个空间进行初始化，以确保程序的安全性和确定性 |
| 赋值 | 赋值就是变量在分配空间之后的某个时间里，对变量的值进行的刷新操作（修改存储空间内的数据\) |

所以我们说的提升，是**声明**的提升。

那么再回过头看，上面的代码就等效于：

```javascript
var a; 
//这里是声明

alert(a);
//变量声明之后并未有初始化和赋值操作，所以这里是 undefined

a = 1;
```

## 复杂点的情况分析 <a id="&#x590D;&#x6742;&#x70B9;&#x7684;&#x60C5;&#x51B5;&#x5206;&#x6790;"></a>

通过上一小节的内容，我们对变量、函数声明提升已经有了一个最基本的理解。那么接下来，我们就来分析一些略复杂的情况。

### 函数同名 <a id="&#x51FD;&#x6570;&#x540C;&#x540D;"></a>

观察下面这段代码:

```javascript
fn()

function fn(){
    console.log(1111)
}

fn()

function fn(){
    console.log(22222)
}
```

输出结果为：

```javascript
22222
22222
```

原因分析：由于预解析机制，`func1`的声明会被提升，提升之后的代码为：

```javascript
function fn(){
    console.log(1111)
}

function fn(){
    console.log(22222)
}

fn();
fn();
```

同名的函数（变量），**后面的会覆盖前面的**，所以两次输出结果都是`22222`。

### 变量和函数同名

```javascript
alert(foo);

function foo(){}

var foo = 2;
```

当出现变量声明和函数同名的时候，**只会对函数声明进行提升，变量会被忽略**。所以上面的代码的输出结果为

```javascript
function foo(){}
```

我们还是来吧预解析之后的代码展现出来:

```javascript
function foo(){};

alert(foo);

foo = 2;
```

再来看一种

```javascript
var num = 1;

function num () {
     alert( num );
}
num();
```

代码执行结果为：

```bash
Uncaught TypeError: num is not a function
```

直接上预解析后的代码：

```javascript
function num(){
     alert(num);
}

num = 1;
num();
```

## 预解析是分作用域的 <a id="&#x9884;&#x89E3;&#x6790;&#x662F;&#x5206;&#x4F5C;&#x7528;&#x57DF;&#x7684;"></a>

声明提升并不是将所有的声明都提升到window对象下面，提升原则是提升到变量运行的环境\(作用域\)中去。

```javascript
function showMsg(){
    var msg = 'This is message';
}
alert(msg); 
// msg is not defined
```

还是直接把预解析之后的代码写出来：

```javascript
function showMsg(){
    var msg;
    msg = 'This is message';
}
alert(msg); 
// msg is not defined
```

## 预解析是分段的

分段，其实就分script标签的

```javascript
<script>
    func(); 
    // 输出 AA2;
    function func(){
        console.log('AA1');
    }
    
    function func(){
        console.log('AA2');
    }
</script>

<script>
    function func(){
        console.log('AA3');
    }
</script>
```

在上面代码中，第一个script标签中的两个`func`进行了提升，第二个`func`覆盖了第一个`func`，但是第二个script标签中的`func`并没有覆盖上面的第二个`func`。所以说预解析是分段的。

tip：但是要注意，分段只是单纯的针对函数，变量并不会分段预解析。

## 函数表达式并不会被提升 <a id="&#x51FD;&#x6570;&#x8868;&#x8FBE;&#x5F0F;&#x5E76;&#x4E0D;&#x4F1A;&#x88AB;&#x63D0;&#x5347;"></a>

```javascript
func();

var func = function(){
    alert("我被提升了");
};
```

这里会直接报错，`func is not a function`，原因就是函数表达式，并不会被提升。只是简单地当做变量声明进行了处理，如下：

```javascript
var func;

func();

func = function(){
    alert("我被提升了");
}
```

一般开发中倾向于使用函数表达式的方式，因为js文件互相引入，可能存在函数名重复的情况，如果使用函数声明的方式后边的函数会覆盖前边函数。如果使用函数表达式就不会。

```javascript
//函数表达式
var fn = function(){
    console.log(111111);
}
fn()
var fn = function(){
    console.log(2222);
}
fn()
VM264:2 111111
VM264:6 2222


//函数声明
function fn(){
    console.log(111111);
}
fn()
function fn(){
    console.log(2222);
}
fn()
VM276:6 2222
VM276:6 2222
```

## 条件式函数声明 <a id="&#x6761;&#x4EF6;&#x5F0F;&#x51FD;&#x6570;&#x58F0;&#x660E;"></a>

```javascript
console.log(typeof func);

if(true){
    function(){
        return 1;
    }
}

console.log(typeof func);
```

上面这段代码，就是所谓的条件式函数声明，这段代码在Gecko引擎中打印`"undefined"`、`"function"`；而在其他浏览器中则打印`"function"`、`"function"`。

原因在于Gecko加入了ECMAScript以外的一个feature：条件式函数声明。

> Conditionally created functions Functions can be conditionally declared, that is, a function declaration can be nested within an if statement.
>
> Note: Although this kind of function looks like a function declaration, it is actually an expression \(or statement\), since it is nested within another statement. See differences between function declarations and function expressions.

Note中的文字说明，条件式函数声明的处理和函数表达式的处理方式一样，所以条件式函数声明没有声明提升的特性。

