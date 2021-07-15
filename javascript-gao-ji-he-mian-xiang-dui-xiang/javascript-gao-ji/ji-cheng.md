### 继承

> 定义：自己没有的属性和方法，拿过别人有的来用，就叫继承
>
> 实现：利用原型中的成员可以被和其相关的对象共享这一属性

### 原型链继承

> 原型链继承就是利用修改原型链的结构\( 增加一个节点, 删除一个节点, 修改节点中的成员 \), 来使得实例对象可以使用整条链中的所有成员.

```js
function SuperType(){
    this.property = true
}

SuperType.prototype.getSuperValue = function(){
    return this.property
}

function SubType(){
    this.subProperty = false
}

SubType.prototype = new SuperType()   // 替换原型

SubType.prototype.getSubValue = function(){
    return this.subProperty
}

var instance = new SubType()

instance.getSuperValue()    // true

// instance
// SubType {
//     subProperty: false,
//     __proto__ : {
//         property: true,
//         getSubValue: ƒ (),
//         __proto__: {
//             getSuperValue: ƒ (),
//             constructor: ƒ SuperType()
//             __proto__: Object
//         }
//     }
// }
```

**注意：instance.constructor指向superType，因为SubType的原型指向SuperType的原型，所以constructor属性指向SuperType。**

**缺点：**

1. 通过原型实现的继承（即原型实际上是另一个类型的实例），该原型属性会被**所有实例共享，造成污染**
2. 在创建子类型（SubType）实例时，不能向超类型的**构造函数**（SuperType）中传递参数

```js
function SuperType(){
    this.property = true,
    this.colors = ['red', 'green', 'blue']
}

function SubType(){
    this.subProperty = false
}

SubType.prototype = new SuperType()   // 替换原型

var instance1 = new SubType()
var instance2 = new SubType()

instance1.colors.push('black')

instance1.colors   // ["red", "green", "blue", "black"]
instance2.colors   // ["red", "green", "blue", "black"]
```

### 借用构造函数（经典继承）

```js
function SuperType(name){
    this.name = name
    this.colors = ['red', 'blue', 'green']
}

function SubType(name){
    // 继承 SuperType
    SuperType.call(this, name)
}

var instance1 = new SubType('jack')    

instance1.colors.push('black')

console.log(instance1)      
// SubType {name: "jack", colors: ["red", "blue", "green", "black"]}

var instance2 = new SubType('rose')

console.log(instance2)      
// SubType {name: "rose", colors: ["red", "blue", "green"], __proto__: {constructor: ƒ SubType(name)}}
```

**优点：**

1. 避免了引用类型的属性被所有实例共享
2. 在创建子类型实例时，可以向超类型构造函数传递参数

**缺点：**

1. **函数无法复用**（**只是子类型的实例**，不是超类型的实例）
2. 方法都在超类型的构造函数中，只能使用这种模式

```js
instance1 instanceof SubType     // true
instance1 instanceof SuperType   // false
```

### 组合继承（伪经典继承）：将原型链和借用构造函数的技术组合到一块

> 背后实现思路：利用原型链实现对原型属性和方法的继承，通过构造函数实现对实例属性的继承

```js
function SuperType(name){
    this.name = name
    this.colors = ['red', 'blue', 'green']
}

SuperType.prototype.getName = function(){
    // 继承 SuperType
    console.log(this.name)
}

function SubType(name, age){
    SuperType.call(this, name)        // 第二次调用超类型构造函数
    this.age = age
}

// 替换原型
SubType.prototype = new SuperType()   // 第一次调用超类型构造函数

SubType.prototype.getAge = function(){
    console.log(this.age)
}

var instance1 = new SubType('jack', 20)

instance1.colors.push('black')

console.log(instance1)
// SubType {
//     name: "jack"
//     colors: ["red", "blue", "green", "black"]
//     age: 20
//     __proto__: {
//         name: undefined
//         colors: ["red", "blue", "green"]
//         getAge: ƒ ()
//         __proto__:{
//             getName: ƒ ()
//             constructor: ƒ SuperType(name)
//             __proto__: Object
//             }
//     }
// }
instance1.getName()      // jack
instance1.getAge()       // 20

var instance2 = new SubType('rose', 18)

console.log(instance2)
// SubType {
//     name: "rose"
//     colors: ["red", "blue", "green"]
//     age: 18
//     __proto__: {
//         name: undefined
//         colors: ["red", "blue", "green"]
//         getAge: ƒ ()
//         __proto__:{
//             getName: ƒ ()
//             constructor: ƒ SuperType(name)
//             __proto__: Object
//             }
//     }
// }
instance2.getName()  // rose
instance2.getAge()   // 18
```

```js
instance1 instanceof SuperType               // true
instance1 instanceof SubType                 // true

SuperType.prototype.isPrototypeOf(instance1) // true
SubType.prototype.isPrototypeOf(instance1)   // true
```

**优点：**

1. 实例可共享且通过向超类型构造函数传参使得相互独立

**缺点：**

1. 会调用两次超类型构造函数

### 原型式继承

```js
function object(o){
    function F(){}
    F.prototype = o
    return new F()
}

var person = {
    name: 'zhangsan',
    skill: ['eat', 'drink']
}

var anotherPerson = object(person)
anotherPerson.name = 'jack'
anotherPerson.skill.push('sleep')

var yetAnotherPerson = object(person)
yetAnotherPerson.name = 'rose'
yetAnotherPerson.skill.push('play')
console.log(person.skill)     // ["eat", "drink", "sleep", "play"]
```

后来Object.create做了规范

```js
var person = {
    name: 'zhangsan',
    skill: ['eat', 'drink']
}

var anotherPerson = Object.create(person)
anotherPerson.name = 'jack'
anotherPerson.skill.push('sleep')

var yetAnotherPerson = Object.create(person)
yetAnotherPerson.name = 'rose'
yetAnotherPerson.skill.push('play')
console.log(person.skill)    // ["eat", "drink", "sleep", "play"]
```

### 寄生式继承

```js
function object(o){
    var F = function(){}
    F.prototype = o
    return new F()
}

function createAnother(o){
    var clone = object(o)
    clone.sayHi = function(){
        alert('Hi')
    }
    return clone
}

var person = {
    name: 'jack',
    age: 18
}

var anotherPerson = createAnother(person)

anotherPerson.sayHi()  // Hi
```

**优点：**

在原型式继承的基础上新增一些函数或方法

**缺点：**

**重复创建方法**，无法达到函数复用，降低效率

### 寄生组合式继承

```js
function superType(name){
    this.name = name
    this.colors = ['red', 'blue', 'gray']
}

superType.prototype.sayName = function(){
    console.log(this.name)
}

function subType(name, age){
    superType.call(this, name)
    this.age = age
}

function object(obj){
    function F(){}
    F.prototype = obj
    return new F()
}

function inheritPrototype(subType, superType){
    var prototype = object(superType.prototype)
    prototype.constructor = subType
    subType.prototype = prototype
}

inheritPrototype(subType, superType)

var instance1 = new subType('xiaohong', 18)

console.log(instance1)
// subType {name: "xiaohong", colors: Array(3), age: 18}
//   name: "xiaohong"
//   colors: (3) ["red", "blue", "gray"]
//   age: 18
//   __proto__: superType
//       constructor: ƒ subType(name, age)
//       __proto__:
//           sayName: ƒ ()
//           constructor: ƒ superType(name)
//           __proto__: Object
// }
```

**优点：**

只调用一次superType构造函数，**避免了在subType的prototype上创建不必要的属性和方法**

### 面试题

已知如下类Animal，要求设计一个Cat类继承自Animal，并实现如下功能：

```js
// Animal:
function Animal(){
    this.name = "Animal";
    this.showName = function(){
        console.log(this.name);
    }
}

// Cat:
function Cat(){
    this.name = "Cat";
    this.showName1 = function(){
        console.log(this.name); 
    }
    this.showName2 = function(){
        console.log(this.name); 
    } 
    this.showName3 = function(){
        console.log(this.__super.name + "=>" + this.name); 
    }
}
```

代码运行：

// 请完善Cat部分相关代码，得到如下结果：

```js
var cat = new Cat();
console.log(cat instanceof Animal); // 得到：true
cat.showName1();     // 得到："Cat" (需要读到Cat中的name属性) 
cat.showName2();    //  得到：”Animal" (需要读到Animal中的name属性) 
cat.showName3();    //得到：”Animal" => "Cat" (需要同时读到Cat中的name和Animal中的name)
```

```js
function Animal(){
    this.name = 'Animal'
    this.showName = function(){
        console.log(this.name)
    }
}

function Cat(){
    this.name = 'Cat'
    this.__super = Cat.prototype
    this.showName1 = function(){
        console.log(this.name)
    }
    this.showName2 = function(){
        console.log(this.name)
    }
    this.showName3 = function(){
        console.log(this.__super.name + '=>' + this.name)
    }
}

Cat.prototype = new Animal()

var cat = new Cat()

cat instanceof Animal  // true
cat.showName1()        // Cat
cat.showName2.call(Cat.prototype)        // Animal
cat.showName3()        // Animal=>Cat
```



