## 函数的四种调用模式

### 函数模式

**特征：**就是一个简单的函数调用，函数名前面没有任何的引导内容。

```javascript
function foo(){}
var func = function(){}
foo(); 
func();
(function(){})();
```

`this`在函数模式中的含义：`this`_**在函数中表示全局对象，在浏览器中是window对象**_

### 方法模式

**特征：**方法一定是依附于一个对象, 将函数赋值给对象的一个属性, 那么就成为了方法.

```javascript
function f() {
    this.method = function () {};
}

var o = {
    method: function () {}
}
```

`this`在方法模式调用中的含义:_**表示函数所依附的这个对象**_

### 构造器调用模式

由于构造函数只是给 this 添加成员. 没有做其他事情. 而方法也可以完成这个操作, 就 this 而言, 构造函数与方法没有本质区别.

**特征：**使用 new 关键字, 来引导构造函数.

```javascript
function Person(){
    this.name = "zhangsan";
    this.age =  19;
    this.sayHello = function(){};
}
var p = new Person();
```

构造函数中的`this`与方法中一样, 表示对象, 但是构造函数中的对象是刚刚创建出来的对象

**关于构造函数中**`return`**关键字的补充说明**

* 构造函数中不需要`return`, 就会默认的`return this`
* 如果手动的添加`return`, 就相当于 return this
* 如果手动的添加`return`基本类型; 无效, 还是保留原来 返回`this`
* 如果手动添加`return null`; 或`return undefiend`, 无效
* 如果手动添加`return 对象类型`; 那么原来创建的`this`就会被丢掉, 返回的是`return`后面的对象

### 创建对象的模式

#### 工厂方法

```javascript
// 工厂就是用来生产的, 因此如果函数创建对象并返回, 就称该函数为工厂函数
function createPerson(name, age, gender) {
    var o = {};
    o.name = name;
    o.age = age;
    o.gender = gender;
    return o;
}
// document.createElement()
```

#### 构造方法

```javascript
function Person(name, age, gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
}
var p = new Person("zhangsan", 19, "男");
```

#### 寄生式创建对象

```javascript
function Person(name, age, gender){
    var o = {};
        o.name = name;
        o.age = age;
        o.gender = gender;

    return o;
}

var p = new Person("Jack", 18, "male");
```

#### 混合式创建

混合式继承就是将所有的属性放在构造方法里面，然后将所有的方法放在原型里面，使用构造方法和原型配合起来创建对象。

### 上下文调用模式

> 上下文\(Context\)，就是**函数调用所处的环境**。
>
> 上下文调用，也就是自定义设置`this`的含义。在其他三种调用模式中，函数/方法在调用的时候，this的值都是指定好了的，我们没办法自己进行设置，如果尝试去给`this`赋值，会报错。

**上下文调用的语法**

```javascript
//第一种， apply
函数名.apply(对象, [参数]);

//第二种， call
函数名.call(对象, 参数);

//上面两种方式的功能一模一样，只是在传递参数的时候有差异。
```

_**功能描述：**_

1. 语法中的函数名表示的就是函数本身，使用函数调用模式的时候，`this`默认是全局对象
2. 语法中的函数名也可以是方法\(如:`obj.method`\)，在使用方法模式调用的时候，`this`默认是指当前对象
3. 在使用`apply`和`call`的时候，默认的`this`都会失效，`this`的值由`apply`和`call`的第一个参数决定

_**补充说明**_

1. 如果函数或方法中没有`this`的操作, 那么无论什么调用其实都一样.
2. 如果是函数调用`foo()`, 那么有点像`foo.apply( window )`.
3. 如果是方法调用`o.method()`, 那么有点像`o.method.apply( o )`.

**参数问题**

`call`和`apply`在没有后面的参数的情况下\(函数无参数, 方法无参数\) 是完全一样的.

如下：

```javascript
function foo() {
    console.log( this );
}
foo.apply( obj );
foo.call( obj );
```

_**第一个参数的使用规则:**_

1. 如果传入的是一个**对象，**那么就相当于**设置该函数中的 this 为参数**
2. 如果**不传**入参数，或传入 null. undefiend 等，那么相当于** this 默认为 window**

```javascript
foo();
foo.apply();
foo.apply( null );
foo.call( undefined );
```

如果传入的是基本类型, 那么 this 就是基本类型对应的包装类型的引用

* number -&gt; Number
* boolean -&gt; Boolean
* string -&gt; String

_**第二个参数的使用规则**_

在使用上下文调用的时候, 原函数\(方法\)可能会带有参数, 那么这个参数在上下文调用中使用第二个\( 第 n 个 \)参数来表示

```javascript
function foo( num ) {
    console.log( num );
}
foo.apply( null, [ 123 ] );
// 等价于
foo( 123 );
```

### 上下文调用模式的应用

上下文调用只是能修改`this`, 但是使用上最多的地方是函数借用.

#### 1. 将伪数组转换为数组

传统的做法：

```javascript
var a = {};
a[ 0 ] = 'a';
a[ 1 ] = 'b';
a.length = 2;

// 使用数组自带的方法 concat
// 如果参数中有数组会把参数数组展开
// 语法: arr.concat( 1, 2, 3, [ 4, [ 5 ] ] );
// 特点：不修改原数组
var arr = [];
var newArr = arr.concat( a );
```

由于`a`是伪数组, 只是长得像数组. 所以上面的代码不能成功，不能使用concat方法。

但是`apply`方法有一个特性, 可以将数组或伪数组作为参数。（IE8不支持伪数组操作）

```javascript
foo.apply( obj, 伪数组 ); 
// IE8 不支持
```

利用`apply`方法，可以写出以下

```javascript
//将伪数组 a 作为 apply 的第二个参数
var newArr = Array.prototype.concat.apply( [], a )
```

处理数组转换, 实际上就是将元素一个一个的取出来构成一个新数组, 凡是涉及到该操作的方法理论上都可以。

**push方法**

```javascript
//将这三个元素依次加到数组中, 返回arr的个数
arr.push( 1, 2, 3 ); 

// 伪数组
var a = { length: 0 }; 

a[ a.length++ ] = 'abc'; 
// a[ 0 ] = 'abc'; a.length++;
a[ a.length++ ] = 'def';

// 使用一个空数组, 将元素一个个放到数组中即可
var arr = [];

// 此时不会将元素展开, 而是将这个伪数组作为一个元素加到数组中
arr.push( a );

// 再次利用 apply 可以展开伪数组的特征
// 利用 apply 可以展开伪数组的特性, 这里就相当于 arr.push( a[0], a[1] )
arr.push.apply( arr, a );
```

#### 2. 求数组中的最大值

传统的做法

```javascript
var max = arr[ 0 ];
for ( var i = 1; i < arr.length; i++ ) {
    if ( arr[ i ] > max ) {
        ...
    }
}
```

在 js 中的`Math`对象中提供了很多数学函数`Math.max( 1,2,3 )`

还是利用 apply 可以展开数组的特性

```javascript
var arr = [ 123456,12345,1234,345345,234,5 ];
Math.max.apply( null, arr );
```

#### 3. 借用构造函数继承

```javascript
function Person ( name, age, gender ) {
    this.name = name;
    this.age = age;
    this.gender = gender;
}

// 需要提供一个 Student 的构造函数创建学生对象
// 学生也应该有 name, age, gender, 同时还需要有 course 课程
function Student ( name, age, gender, course ) {
    Person.call( this, name, age, gender );
    this.course = course;
}
```



