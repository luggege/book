#### Object.getOwnPropertyDescriptor\(obj, prop\)：返回指定对象\*所有\***自身**（非继承性）属性的**描述对象，**返回值是一个对象

* 如果是数据描述符，这个对象的属性包含：value、writable、enumerable、configurable
* 如果是访问描述符，这个对象的属性包含：enumerable、configurable、get、set

```js
Object.getOwnPropertyDescriptor(obj, 'a')
// {value: 111, writable: false, enumerable: false, configurable: false}

Object.getOwnPropertyDescriptor(obj, 'b')
// {value: "222", writable: true, enumerable: true, configurable: true}

// 重新赋值
obj.b = 2222
Object.getOwnPropertyDescriptor(obj, 'b')
// {value: 2222, writable: true, enumerable: true, configurable: true}

// 遍历
for(let i in obj){
    console.log(i, obj[i])   // b , 222
}
```

```js
// Object.assign()只拷贝对象自身的可枚举属性（忽略enumerable: false的属性）
let obj1 = Object.assign({}, obj)

obj1      // {b: 222}
```

如：对象原型的valueOf方法，以及数组的length属性，可通过设置enumerable为false，规避for in遍历到继承自原型上的属性

```js
Object.getOwnPropertyDescriptor(Object.prototype, 'valueOf')
// {writable: true, enumerable: false, configurable: true, value: ƒ valueOf()}

Object.getOwnPropertyDescriptor([], 'length')
// {value: 0, writable: true, enumerable: false, configurable: false}
```

#### Object.getOwnPropertyNames\(obj\)：遍历**自身**的\***可枚举\***或\***不可枚举\***属性（不包含Symbol属性）

#### Object.getPrototypeOf\(obj\)：获取实例对象的\*原型\*

#### obj.hasOwnProperty\(property\)：检测对象自身是否含有某个属性（**不包含原型链**上的属性）



