# 静态成员和实例成员

静态成员和实例成员这两个概念其实也是从面相对象的编程语言中引入的，对应到JavaScript中的理解为：

## 静态成员（Person.成员）

静态成员是指_**静态属性**_和_**静态方法**_，所谓静态，就是有**构造函数**提供的。

## 实例成员（p.成员）

实例成员是指_**实例属性**_和_**实例方法**_，所谓实例，就是由构造函数创建出来的**实例对象**。

## 举例说明：

```javascript
function Person(){
    this.name = "zs" ,
    this.sayHello = function(){
        console.log("Hello World");
    }
}
//下面这个sayHi方法就是构造函数自己的方法，也就是静态方法
Person.sayHi = function(){ 
    console.log("I'm a Person");
}

//原型属性属于构造函数，所以原型属性是静态属性
Person.prototype = {};
var p = new Person();

//这里的name是构造函数创建出来的实例对象的属性，所以是实例属性
p.name = "李四";

//这里的sayHello也是构造函数创建出来的实例对象的方法，所以是实例方法
p.sayHello();
```

## 提示：

一般工具型方法都有静态成员提供, 一般与实例对象有关的方法由实例成员表示.

工具方法：比如`jQuery.Ajax()`、`jQuery.trim()`、`jQuery.Each()`

