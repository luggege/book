### 构造函数

```javascript
function Person(name, age){
  this.name = name;
  this.age = age;
}
```

```javascript
//断点调试，进行类型查看
var p1 = new Person();
var p2 = new Object();
var p3 = new Date();
var p4 = new RegExp();
var p5 = {};
```

#### 构造函数是干什么用的？

> 在JavaScript中，构造函数是给对象添加属性，初始化属性用的。

#### **对象的创建过程**

```javascript
var p = new Person();
```

以上面这个p对象创建为例：

* 首先使用new关键字创建对象，类似于使用`{}`,这个时候创建出来的对象是一个"没有任何成员"的对象。这里需要注意两点：
* * 使用`new`关键字创建的对象，对象的类型就是创建这个对象使用的构造函数的函数名
  * 使用`{}`创建对象，对象的类型一定是`Object`，相当于使用了`new Object()`
* 使用构造函数为其初始化成员

* * 在构造函数调用开始的时候，有一个赋值操作，也就是让`this = 刚创建出来的对象`
  * 在构造函数中，`this`就代表刚创建出来的对象
* 在构造函数中，利用对象的动态特性，为对象添加成员

#### **关于构造函数中**`return`**关键字的补充说明**

* 构造函数中不需要`return`, 就会默认的`return this`
* 如果手动的添加`return`, 就相当于 `return this`
* 如果手动的添加`return`基本类型; 无效, 还是保留原来 返回`this`
* 如果手动添加`return null`; 或`return undefiend`, 无效
* 如果手动添加`return 对象类型`; 那么原来创建的`this`就会被丢掉, 返回的是`return`后面的对象



