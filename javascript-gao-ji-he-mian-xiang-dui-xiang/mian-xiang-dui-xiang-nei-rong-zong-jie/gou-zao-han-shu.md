# 构造函数

```text
function
Person
(
name, age
)
{

this
.name = name;

this
.age = age;
}
```

```text
//断点调试，进行类型查看
var
 p1 = 
new
 Person();

var
 p2 = 
new
Object
();

var
 p3 = 
new
Date
();

var
 p4 = 
new
RegExp
();

var
 p5 = {};
```

## 1.构造函数是干什么用的？ <a id="1&#x6784;&#x9020;&#x51FD;&#x6570;&#x662F;&#x5E72;&#x4EC0;&#x4E48;&#x7528;&#x7684;&#xFF1F;"></a>

在JavaScript中，构造函数是给对象添加属性，初始化属性用的。

## 2. 对象的创建过程 <a id="2-&#x5BF9;&#x8C61;&#x7684;&#x521B;&#x5EFA;&#x8FC7;&#x7A0B;"></a>

```text
var
 p = 
new
 Person();
```

以上面这个p对象创建为例：

1. 首先使用new关键字创建对象，类似于使用`{}`,这个时候创建出来的对象是一个"没有任何成员"的对象。这里需要注意两点：
   * 使用

     `new`

     关键字创建的对象，对象的类型就是创建这个对象使用的构造函数的函数名

   * 使用

     `{}`

     创建对象，对象的类型一定是

     `Object`

     ，相当于使用了

     `new Object()`
2. 使用构造函数为其初始化成员
   * 在构造函数调用开始的时候，有一个赋值操作，也就是让

     `this = 刚创建出来的对象`

   * 在构造函数中，

     `this`

     就代表刚创建出来的对象
3. 在构造函数中，利用对象的动态特性，为对象添加成员
