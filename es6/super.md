### super

> this关键字总是指向函数所在的当前对象，ES6新增类似的super关键字，总是指向**当前对象的原型对象**

```js
const proto = {
  foo: 'hello'
};

const obj = {
  foo: 'world',
  find() {
    return super.foo;
  }
};

Object.setPrototypeOf(obj, proto);
obj.find() // "hello"
```

```js
const proto = {
  x: 'hello',
  foo() {
    console.log(this.x);
  },
};

const obj = {
  x: 'world',
  foo() {
    // 调用原型对象的foo方法，但是绑定的this还是当前对象obj
    super.foo();
  }
}

Object.setPrototypeOf(obj, proto);

obj.foo() // "world"
```

* super关键字只能用在**对象的方法**之中，用在其他地方会报错 

```js
// Uncaught SyntaxError: 'super' keyword unexpected here
const obj = {
  // super用在属性里面
  foo: super.foo
}

const obj = {
  // super用在函数里，然后赋值给foo
  foo: () => super.foo
}

const obj = {
  // super用在函数里，然后赋值给foo
  foo: function () {
    return super.foo
  }
}

// super.foo 等同于 Object.getPrototypeOf(this).foo 或者 Object.getPrototypeOf(this).foo.call(this)
```

* super 实现继承，删除 super 上的属性将抛出异常

```js
class A{
    constructor(n){
        console.log(n); //=>100;
        this.x = 300;
    }
    getX(){
        console.log(this.x);
    }
    add() {
        return this.x + this.y
    }
}

class B extends A{ //=>extends 类似实现原型继承
    constructor(){
        // 注意: 在派生的类中, 在你可以使用'this'之前, 必须先调用super()
        super(100);//=>类似于call的继承：在这里super相当于把A的constructor给执行了，并且让方法中的this是B的实例，super当中传递的实参都是在给A的constructor传递。
        this.y = 200;
    }
    getY(){
        console.log(this.y);
    }
    add() {
        return super.add()
    }
}

let f = new B();

f        // {x: 300, y: 200}
f.add()  // 500
```

* 删除 super 上的属性将抛出异常

```js
delete() {
    delete super.foo; 
}

f.delete(); // ReferenceError: invalid delete involving 'super'.
```



