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

