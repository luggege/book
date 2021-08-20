### class

* ES6的class类，只是一个**语法糖**，只是看起来更像面向对象编程的语法而已，完全可以看作是**构造函数**的另一种写法

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

* 类本身就指向**构造函数**

```js
typeof Person  // function
Person === Person.prototype.constructor   // true
```

**注意：**

* 类内部定义的各方法之间无需用逗号隔开
* 定义在**类内部**的方法是**不可枚举**的，通过**Object.assign\(\)**和ES5中直接向**构造函数的原型上**添加的方法是**可枚举**的

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

* 类内部默认constructor，且constructor默认返回this（实例对象），同样也可返回指定对象

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

* 对某个**属性**设置，getter 和 setter 存值函数和取值函数，拦截该属性的存取行为

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

* class表达式

```js
// Point是定义在class内部的，不能直接new
const MyPoint = class Point {
    say() {
        console.log(111)
    }
}
(new MyPoint()).say()   // 111

// 可以简写为
const MyPoint = class {
    say() {
        console.log(111)
    }
}

// 进而可以写出立即执行的类
const p = new class {
    say() {
        console.log(111)
    }
}
p.say()  // 111
```

注意点

* * class内部默认严格模式
* * class不存在变量提升

```js
// 不报错
new Student()
function Student(){}

// Person is not defined
new Person()
class Person{}
```

* * this指向

> 类中方法中的this默认指向实例。但是如果将方法单独提取出来使用（**直接调用**），this会指向该方法**运行时的所在环境**，造成的this指向错误问题

```js
class Foo {
    say(name = 'jack') {
        this.print(name)
    }
    print(name) {
        console.log(name)
    }
}
const foo = new Foo()
// foo.say()：实例调用，this指向实例
const {say} = foo
// say()：直接调用，类中默认开启严格模式，所以this指向undefined
say()  // Cannot read property 'print' of undefined
```

解决办法

* * * constructor**绑定this**，给**实例添加**属性方法

```js
class Foo {
    constructor(){
        // bind作用：生成一个新的函数、改变this
        this.say = this.say.bind(this)
    }
    say(name = 'jack') {
        this.print(name)
    }
    print(name) {
        console.log(name)
    }
}
const f1 = new Foo()
const {say} = f1
say() // jack
```

* * * **箭头函数**（this取决于上下文）

  ```js
  class Foo {
      constructor(){
          console.log('this', this)
          this.getThis = () => this
      }
  }

  const f1 = new Foo()
  f1.getThis() === f1    // true
  ```

  ```js
  class Foo {
      // 定义在实例上的方法
      say = (name = 'jack') => {
          this.print(name)
      }
      // 定义在原型上的方法
      print(name) {
          console.log(name)
      }
  }
  const f1 = new Foo()
  const {say} = f1
  say() // jack
  ```
* 静态方法

> 方法前加**static**关键字，只能**构造函数调用**，实例不能调用

* 属性的新写法

> 通常**实例**的属性写在constructor里，新写法可以提取出来去掉this与其他方法平级（prop = 0）

* 静态属性

> 老写法在构造函数上绑定属性（Foo.prop），不符合相关代码放在一起的代码组织原则且容易忽略。新写法在属性前加**static**关键字，表示**构造函数的属性**



