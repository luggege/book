#### Object.setPrototypeOf\(obj, proto\)：设置一个对象的原型对象，返回参数对象本身

```js
let proto = {}
let obj = {
    x: 10
}
Object.setPrototypeOf(obj, proto)

proto.y = 20
proto.z = 40

obj.x   // 10
obj.y   // 20
obj.z   // 40
```

```js
// 如果参数不是对象，会转为对象
Object.setPrototypeOf(1, {})     // 1
Object.setPrototypeOf('1', {})   // "1"
Object.setPrototypeOf(true, {})  // true

// 由于undefined和null无法转为对象，会报错
Object.setPrototypeOf(undefined, {})
Object.setPrototypeOf(null, {})
// Uncaught TypeError: Object.setPrototypeOf called on null or undefined
```

#### Object.getPrototypeOf\(obj\)：获取对象的原型对象

```js
Object.getPrototypeOf(obj)             // {y: 20, z: 40}
Object.getPrototypeOf(obj) === proto   // true
```

```js
// 如果参数不是对象，会被自动转为对象
Object.getPrototypeOf(1)  // 等同于 Object.getPrototypeOf(Number(1))
// Number {0, constructor: ƒ, t...
Object.getPrototypeOf('1') // 等同于 Object.getPrototypeOf(String(1))
// String {"", constructor: ƒ, ...
Object.getPrototypeOf(true) // 等同于 Object.getPrototypeOf(Boolean(1))
// Boolean {false, constructor: ƒ, toString: ƒ, valueOf: ƒ}

Object.getPrototypeOf(1) === Number.prototype // true
Object.getPrototypeOf('1') === String.prototype // true
Object.getPrototypeOf(true) === Boolean.prototype // true

// 由于undefined和null无法转为对象，会报错
Object.getPrototypeOf(undefined)
Object.getPrototypeOf(null)
// Uncaught TypeError: Cannot convert undefined or null to object、
```

#### proto.isPrototypeOf\(obj\)：判断一个对象是否在另一个对象的原型链上



