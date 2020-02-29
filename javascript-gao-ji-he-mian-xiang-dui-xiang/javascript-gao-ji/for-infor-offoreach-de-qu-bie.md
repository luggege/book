# for in、for of、forEach的区别

### for in  **只遍历对象自身的和继承的可枚举属性**

1. 只遍历可循环属性，跳过空值  
2. 循环的输出顺序问题：先遍历**整数**属性（按照**升序**），其他属性按照创建顺序遍历
3. 对于数组中的属性（如：test： testing），只有for-in循环才能打印出这种键值对

### for of

1. for-of不会跳过空值，默认为undefined。
2. for-in、forEach遇数组空项会跳过，for-in循环遇数组空项key值发生变化
3. 对于数组中的属性（如：test： testing），不能遍历出

### forEach

1. 不能使用break，continue跳出循环，不同于for-in、for-of

```javascript
1、Object
var obj = {
  2: 'aaa',
  c: 333,
  1: 'bbb',
  a: 111,
  3: 'ccc',
  d: 222
}

obj.b = "ddd"

for(let i in obj){
  console.log('in````````', i, obj[i])
}
// in```````` 1 bbb
// in```````` 2 aaa
// in```````` 3 ccc
// in```````` c 333
// in```````` a 111
// in```````` d 222
// in```````` b ddd

for(let item of obj){
  console.log('of````````', item)
}
//Uncaught TypeError: obj[Symbol.iterator] is not a function


2、Array
var arr = [0, , null, 1, undefined, 2, 3]

arr.test = 'testing'

for(var item in arr){
  console.log('in`````', item, arr[item])
  // ["0", "2", "3", "4", "5", "6", "test"]

  // 0 0
  // 2 null
  // 3 1
  // 4 undefined
  // 5 2
  // 6 3
  // test testing
}

for(var item of arr){
   console.log('of`````', item)
  // [0, undefined, null, 1, undefined, 2, 3]  
}

arr.forEach(element => {
  console.log('forEach```````', element)
  // [0, null, 1, undefined, 2, 3] 
})

3、String
var str = 'aaabbbccc'

for(let item in str){
  console.log('in`````', item)
}
// in````` 0
// in````` 1
// in````` 2
// in````` 3
// in````` 4
// in````` 5
// in````` 6
// in````` 7
// in````` 8

for(let item of str){
  console.log('of`````', item)
}
// of````` a
// of````` a
// of````` a
// of````` b
// of````` b
// of````` b
// of````` c
// of````` c
// of````` c
```

### 属性遍历的方式

1. for in：  遍历**自身**的和**继承**的**可枚举**属性
2. Object.keys\(\) ：遍历**自身**的**可枚举**属性
3. Object.getOwnPropertyNames\(Object.prototype\)： 遍历**自身**的**可枚举或不可枚举**属性（不包含Symbol属性）
4. Object.getOwnPropertySymbols\(obj\)： 只遍历自身的**Symbol属性**
5. Reflect.ownKeys\(obj\)： 返回对象自身的所有键名的数组，**不管是否是Symbol，是否可枚举**

```js
1.for in


2.Object.keys([])
// []

3.Object.getOwnPropertyNames(Object.prototype)
// ["constructor", "__defineGetter__", "__defineSetter__", "hasOwnProperty", "__lookupGetter__", "__lookupSetter__", "isPrototypeOf", "propertyIsEnumerable", "toString", "valueOf", "__proto__", "toLocaleString"]

4.Object.getOwnPropertySymbols({ [Symbol()]:0, b:0, 10:0, 2:0, a:0 })
// [Symbol()]

5. Reflect.ownKeys({ [Symbol()]:0, b:0, 10:0, 2:0, a:0 })
// ["2", "10", "b", "a", Symbol()]
```

以上的 5 种方法遍历对象的键名，都遵守同样的属性遍历的次序规则。

* 首先遍历所有**数值键**，按照数值**升序**排列。
* 其次遍历所有**字符串键**，按照**加入时间**升序排列。
* 最后遍历所有 **Symbol 键**，按照**加入时间**升序排列。



