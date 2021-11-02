### Object.setPrototypeOf\(obj, proto\)：设置一个对象的原型对象，返回参数对象本身

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

### Object.getPrototypeOf\(obj\)：获取对象的原型对象

```js
Object.getPrototypeOf(obj)             // {y: 20, z: 40}
Object.getPrototypeOf(obj) === proto   // true
```

```js
// 如果参数不是对象，会被自动转为对象
Object.getPrototypeOf(1)  // 等同于 Object.getPrototypeOf(Number(1))
// Number {0, constructor: ƒ, toExponential: ƒ, toFixed: ƒ, toPrecision: ƒ, …}constructor: ƒ Number()toExponential: ƒ toExponential()toFixed: ƒ toFixed()toLocaleString: ƒ toLocaleString()toPrecision: ƒ toPrecision()toString: ƒ toString()valueOf: ƒ valueOf()__proto__: Object[[PrimitiveValue]]: 0
Object.getPrototypeOf('1') // 等同于 Object.getPrototypeOf(String(1))
// String {"", constructor: ƒ, anchor: ƒ, big: ƒ, blink: ƒ, …}anchor: ƒ anchor()big: ƒ big()blink: ƒ blink()bold: ƒ bold()charAt: ƒ charAt()charCodeAt: ƒ charCodeAt()codePointAt: ƒ codePointAt()concat: ƒ concat()constructor: ƒ String()endsWith: ƒ endsWith()fixed: ƒ fixed()fontcolor: ƒ fontcolor()fontsize: ƒ fontsize()includes: ƒ includes()indexOf: ƒ indexOf()italics: ƒ italics()lastIndexOf: ƒ lastIndexOf()length: 0link: ƒ link()localeCompare: ƒ localeCompare()match: ƒ match()matchAll: ƒ matchAll()normalize: ƒ normalize()padEnd: ƒ padEnd()padStart: ƒ padStart()repeat: ƒ repeat()replace: ƒ replace()replaceAll: ƒ replaceAll()search: ƒ search()slice: ƒ slice()small: ƒ small()split: ƒ split()startsWith: ƒ startsWith()strike: ƒ strike()sub: ƒ sub()substr: ƒ substr()substring: ƒ substring()sup: ƒ sup()toLocaleLowerCase: ƒ toLocaleLowerCase()toLocaleUpperCase: ƒ toLocaleUpperCase()toLowerCase: ƒ toLowerCase()toString: ƒ toString()toUpperCase: ƒ toUpperCase()trim: ƒ trim()trimEnd: ƒ trimEnd()trimLeft: ƒ trimStart()trimRight: ƒ trimEnd()trimStart: ƒ trimStart()valueOf: ƒ valueOf()Symbol(Symbol.iterator): ƒ [Symbol.iterator]()__proto__: Object[[PrimitiveValue]]: ""
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



