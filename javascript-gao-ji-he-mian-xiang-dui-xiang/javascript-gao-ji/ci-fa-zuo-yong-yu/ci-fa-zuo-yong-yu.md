## 词法作用域

> **域**，表示的是一个范围。**作用域**，就是作用范围。
>
> 作用域说明的是一个变量可以在什么地方被使用，什么地方不能被使用。

### 块级作用域 

JavaScript中没有块级作用域

```javascript
{
    var num = 123;
    {
        console.log( num );  // 123
    }
} 

console.log( num );    // 123
```

上面这段代码在JavaScript中是不会报错的，但是在其他的编程语言中（C\#、C、JAVA）会报错。

这是因为，在JavaScript中没有块级作用域，使用`{}`标记出来的代码块中声明的变量`num`，是可以被`{}`外面访问到的。

但是在其他的编程语言中，有块级作用域，那么`{}`中声明的变量`num`，是不能在代码块外部访问的，所以报错。

### 词法作用域 

> 词法\( 代码 \)作用域, 就是代码在编写过程中体现出来的作用范围。代码一旦写好, 不用执行, 作用范围就已经确定好了. 这个就是所谓词法作用域.

### 在 js 中词法作用域规则:

* 函数**允许访问函数外的数据**
* 整个代码结构中**只有函数可以限定作用域**
* 作用域规则**首先使用提升规**则分析
* 如果**当前作用规则**中有名字了, 就**不考虑外面**的名字

**例子1：**

```javascript
var num = 123;
function foo() {
    console.log( num );
}
foo();  // 123
```

**例子2：**

```javascript
if ( false ) {
    var num = 123;
}
console.log( num );  // undefiend
```

**例子3：**

```javascript
var num = 123;
function foo() {
    var num = 456;
    function func() {
        console.log( num );
    }
    func();
}
foo();   // 456
```

### 练习：

```javascript
var num1 = 123;

function foo1() {
    var num1 = 456;

    function foo2() {
        num1 = 789;

        function foo3 () {
            console.log( 111, num1 );  // 789
        }
        foo3();
    }
    foo2();
}
foo1();

console.log( 222, num1 );  // 123
```

### 面试题

```javascript
var num = 123;

function func1(){
    console.log(111, num);   // 123
}

function func2(){
    var num = 456;
    func1();
    console.log(222, num);   // 456
}
func2()
```

