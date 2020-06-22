### Map

> 传统的JavaScript只能用字符串当作对象的键，ES6提供了一种Map结构可用**对象当作键**

* Map构造函数接受**数组**作为**参数**

```js
let map = new Map([['name', 'Jack'], ['age', '18']])

 // Map(1) {"name" => "Jack", "age" => "18"}
 // [[Entries]]
 //   0: {"name" => "Jack"}
 //   1: {"age" => 18}
 //   size: 2 
 // __proto__: Map
```

实际上执行如下算法

```js
const items = [
    ['name', 'Jack'],
    ['age', '18']
]

const map = new Map()

items.forEach(([key, value]) => map.set(key, value))

// Map(2) {"name" => "Jack", "age" => "18"}
```

#### 方法

```js
1. set
map.set({p: 'Hello World'}, 'content')
// Map(3) {"name" => "Jack", "age" => "18", {…} => "content"}
// [[Entries]]
//     0: {"name" => "Jack"}
//     1: {"age" => "18"}
//     2: {Object => "content"}
//         key: {p: "Hello World"}
//         value: "content"
//     size: 3
// __proto__: Map

1.1 同一个键多次赋值，后边覆盖前边
m3.set('baz', 333)
// Map(1) {"baz" => 333}

1.2 只有对同一个对象的引用，才视为同一个键
m3.set(['aaa'], 111)
m3.get(['aaa'])
// undefined

const arr = ['bbb']
m3.set(arr, 222)
m3.get(arr)
// 222

1.3 简单类型的值（字符串、布尔、数字）作为Map的键，只有严格相等，才认为是同一个键，但NaN虽然不严格等于自身，但Map认为同一个键
m1.set(NaN, 123)
m1.get(NaN)
// 123

m1.set(undefined, 111)
m1.set(null, 222)
m1.get(undefined)
// 111

m1.set(+0, 333)
m1.set(-0, 444)
m1.get(+0)
// 444

m1.set(true, 555)
m1.set('true', 666)
m1.get(true)
// 555

2. get
map.get('name')
// "Jack"

3. has
map.has('age')
// true

4. size
map.size
// 3

5. keys
map.keys()
// MapIterator {…}, "name", "age"}

6. values
map.values()
// MapIterator {"content", "Jack", "18"}

7. entries
map.entries()
// MapIterator {…} => "content", "name" => "Jack", "age" => "18"}

8. forEach
map.forEach((value, key) => console.log(key,value))
// {p: "Hello World"} "content"
// name Jack
// age 18

等同于
for(let [key, value] of map3.entries()){
    console.log(key, value)
}

等同于
for(let [key, value] of map3){
    console.log(key, value)
}

8.1 利用forEach的第二个参数来绑定this，将回调函数的this指向第二个参数
let reporter1 = {
  report: function(key, value) {
    console.log("Key: %s, Value: %s", key, value);
  }
};

map3.forEach(function(value, key, map) {
  this.report(key, value);
}, reporter1);
// Key: Object, Value: content
// Key: name, Value: Jack
// Key: age, Value: 18

9. delete
map.delete('name')
// true

10. clear
map.clear()
```

* 任何具有iterator接口、且每个成员都是双元素的数组的数据结构，都可以作为Map构造函数的参数，即Set和Map都可以作为参数用来生成新的Map

```js
const set = new Set([
    ['foo', 1],
    ['baz', 2]
])
const m1 = new Map(set)
// Map(2) {"foo" => 1, "baz" => 2}

const m2 = new Map([['baz', 3]])
const m3 = new Map(m2)
// Map(1) {"baz" => 3}
```

* 可使用扩展运算符（...）或Array.from，快速将Map数据结构**转为数组**结构

```js
[...map.keys()]
// [{…}, "name", "age"]

[...map.values()]
// ["content", "Jack", "18"]

[...map.entries()]
// [Array(2), Array(2), Array(2)]

[...map]
//[Array(2), Array(2), Array(2)]
// 0: (2) [{…}, "content"]
// 1: (2) ["name", "Jack"]
// 2: (2) ["age", "18"]
```

* 利用数组的map、filter，实现Map的遍历和过滤

```js
const map6 = [...map3].map(([key, value]) => ['key_' + key, 'value_' + value])
 // [
 //     ["key_[object Object]", "value_content"]
 //     ["key_name", "value_Jack"]
 //     ["key_age", "value_18"]
 // ]

const map1 = [...map].filter(([key, value]) => key === 'name')
// [["name", "Jack"]]
```

### WeakMap

> 类似于Map结构，用于生成键值对的集合

```js
const wm = new WeakMap()
const key = {foo: 1}
wm.set(key, 2)
wm.get(key)
// 2
```

* 可传数组作为参数，但只能以对象作为键名，不能以基本数据类型和Symbol类型作为键名，否则报错

```js
const wm1 = new WeakMap([
    [{foo: 1}, 2],
    [[4,5,6], 3],
    [undefined, 5]
])

// Uncaught TypeError: Invalid value used as weak map key
```

#### 区别

1. 只能以对象作为键名
2. WeakMap的健名指向的对象，不计入垃圾回收机制

#### 方法

1. set
2. get
3. has
4. delete

#### 用途

WeakMap典型的应用场合就是DOM节点作为键名，DOM节点删除，该状态自动消失，不存在内存泄漏的风险

