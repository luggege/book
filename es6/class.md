### class

* ES6的class类，只是一个语法糖，只是看起来更像面向对象编程的语法而已，完全可以看作是构造函数的另一种写法

```js
class Person {
    constructor(name) {
        this.name = name
    }

    skill() {
        return '我的名字叫：' + this.name
    }
}

// 相当于
function Person(name) {
    this.name = name
}
Person.prototype.skill = function() {
    return '我的名字叫：' + this.name
}
```

* 类本身就指向构造函数

```js
Person === Person.prototype.constructor   // true
```

**注意：**

* 类内部定义的各方法之间无需用逗号隔开
* 定义在**类内部**的方法是**不可枚举**的，通过Object.assign\(\)和ES5中直接向**构造函数的原型上**添加的方法是**可枚举**的

```js
Object.keys(Person.prototype)     // []
Object.getOwnPropertyNames(Person.prototype)      // ["constructor", "skill"]

// 通过Object.assign()添加方法
Object.assign(Person.prototype, {
    like() {
        return '我喜欢运动'
    }
})

Object.keys(Person.prototype)     // ["like"]
```

* 类直接调用报错，普通构造函数直接调用不会报错

```js
Person()
// VM2102:1 Uncaught TypeError: Class constructor Person cannot be invoked without 'new'

Student()
// undefined
```

* 类内部默认constructor，且constructor默认返回this（同样也可返回指定对象）

```js
class Teacher {

}

// 等同于
class Teacher {
    constructor() {}    
}
```

```js
class Foo {
    constructor() {
        return Object.create(null)
    }
}

new Foo() instanceof Foo     // false

// 说明：新生成的对象不在原构造函数的原型链上
```

* getter 和 setter 存值函数和取值函数

```js
class Point {
    constructor() {}

    get prop() {
        return 'getter'
    }
    set prop(value) {
        console.log('setter: ' + value)
    }
}

let point = new Point()

point.prop = 123      // setter: 123

point.prop            // "getter"
```

* 属性表达式

```js
let methodName = 'getArea'

class Square {
    constructor(){}

    [methodName]() {}
}

let s = new Square()

s.__proto__.hasOwnProperty('getArea')    // true
```



