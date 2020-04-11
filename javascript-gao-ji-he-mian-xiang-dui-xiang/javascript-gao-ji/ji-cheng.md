# 继承

## 继承

> 定义：自己没有的属性和方法,拿过别人有的来用,就叫继承
>
> 实现：利用原型中的成员可以被和其相关的对象共享这一属性

* ### 混入式继承

for in

### 原型继承

> 通过修改原型的结构，实现的继承是原型继承

１．继承原型的成员

２．直接替换原型对象\(手动添加constructor属性\)

３．利用混入的方式给原型对象添加成员

注意：使用替换原型的方式实现继承，现有原型中的成员就会丢失

### 借用构造函数（经典继承）

Object.create\(obj\)

#### 解决兼容性问题:

1. 检测浏览器是否支持 Object.create 方法,如果支持,直接返回 Object.create\(obj\) .如果不支持,手动添加给
2. 自定义函数,在函数内部判断是否 支持 Object.create 方法,如果不支持,手动添加

### 组合继承

### 原型链继承

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

1. 通过原型实现的继承（即原型实际上是另一个类型的实例），该原型属性会被所有实例共享，造成污染
2. 在创建子类型（SubType）实例时，不能向超类型的**构造函数**（SuperType）中传递参数

```js
function SuperType(){
    this.property = true,
    this.colors = ['red', 'green', 'blue']
}

function SubType(){
    this.subProperty = false
}

SubType.prototype = new SuperType()

var instance1 = new SubType()
var instance2 = new SubType()

instance1.colors.push('black')

instance1.colors   // ["red", "green", "blue", "black"]
instance2.colors   // ["red", "green", "blue", "black"]
```

### 寄生式继承

### 寄生组合式继承



