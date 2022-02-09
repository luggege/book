### Object.create\(proto\[, propertiesObject\]\): 创建一个以该对象为原型对象的新对象

> 兼容：IE9+、Firefox4+、Safari5+、Opera12+、Chrome

* proto：必填，新创建对象的原型对象

```js
Object.create()/Object.create(undefined)
// VM1719:1 Uncaught TypeError: Object prototype may only be an Object or null: undefined

o = Object.create(null)
// {}

Object.create(Object.prototype)
// {__proto__:{}}

// 创建一个以空对象为原型的对象
Object.create({})
// {__proto__:{__proto__: Object}}
```

* propertiesObject：可选，添加到新创建对象上的不可枚举（默认）或可枚举属性，对应Object.defineProperty的参数

```js
o = Object.create({}, {p: {value: 111}})

for(var i in o){
    console.log(i)
}
// undefined

o = Object. create({}, {q: {value: 222, configurable: true, enumerable: true}})
for(var i in o){
    console(i)
}
// q
```



