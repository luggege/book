# 词法作用域

**域**，表示的是一个范围，**作用域**，就是作用范围。

作用域说明的是一个变量可以在什么地方被使用，什么地方不能被使用。

## 块级作用域 <a id="&#x5757;&#x7EA7;&#x4F5C;&#x7528;&#x57DF;"></a>

JavaScript中没有块级作用域

```javascript
{
    var num = 123;
    {
        console.log( num );
    }
}

console.log( num );
```

上面这段代码在JavaScript中是不会报错的，但是在其他的编程语言中（C\#、C、JAVA）会报错。

这是因为，在JavaScript中没有块级作用域，使用`{}`标记出来的代码块中声明的变量`num`，是可以被`{}`外面访问到的。

但是在其他的编程语言中，有块级作用域，那么`{}`中声明的变量`num`，是不能在代码块外部访问的，所以报错。

## 词法作用域 <a id="&#x8BCD;&#x6CD5;&#x4F5C;&#x7528;&#x57DF;"></a>

**什么是词法作用域？**

词法\( 代码 \)作用域, 就是代码在编写过程中体现出来的作用范围. 代码一旦写好, 不用执行, 作用范围就已经确定好了. 这个就是所谓词法作用域.

**在 js 中词法作用域规则:**

* 函数允许访问函数外的数据.
* 整个代码结构中只有函数可以限定作用域.
* 作用域规则首先使用提升规则分析
* 如果当前作用规则中有名字了, 就不考虑外面的名字

### 例子1： <a id="&#x4F8B;&#x5B50;1&#xFF1A;"></a>

```javascript
var num = 123;


function foo() {
    console.log( num );
}

foo();
```

### 例子2： <a id="&#x4F8B;&#x5B50;2&#xFF1A;"></a>

```javascript
if ( false ) {
    var num = 123;
}

console.log( num ); 
// undefiend
```

### 例子3： <a id="&#x4F8B;&#x5B50;3&#xFF1A;"></a>

```javascript
var num = 123;

function foo() {
    
    var num = 456;
    
    function func() {
        console.log( num );
    }

    func();
}

foo();
```

### 练习： <a id="&#x7EC3;&#x4E60;&#xFF1A;"></a>

```javascript
var num1 = 123;

function foo1() {

var num1 = 456;

function foo2() {
        num1 = 789;

function foo3 () {

console.log( num1 );
        }
        foo3();
    }
    foo2();
}
foo1();

console.log( num1 );
```

### 面试题 <a id="&#x9762;&#x8BD5;&#x9898;"></a>

```text
var
 num = 
123
;

function
func1
(
)
{

console
.log(num);
}


function
func2
(
)
{

var
 num = 
456
;
    func1();
}
```

