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



