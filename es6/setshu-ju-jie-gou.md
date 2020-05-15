## Set

> 一种**新的数据结构**，Set本身是一个**构造函数**，用来生成Set数据结构。类似于数组，但是成员是唯一的，**没有重复**

```js
1. 使用add为Set添加属性
const aaa = new Set()
[1, undefined, undefined, 2, null, 2, 3, 4, 4].forEach(x => aaa.add(x))
for(let i of aaa){
    console.log(i)  // 1, undefined, 2, null, 3, 4
}

2. 直接通过传参生成Set
const set = new Set([1, undefined, undefined, 2, null, 2, 3, 4, 4])
// Set(6) {1, undefined, 2, null, 3, …}

3. 转成真正的数组
Array.from(set)
// [1, undefined, 2, null, 3, 4]
[...set]
// [1, undefined, 2, null, 3, 4]

4. 属性
set.size
// 6

5. 字符串去重
[...new Set('abbacc')]
// ["a", "b", "c"]

6. NaN 认为是同一个只添加一次
set.add(NaN)
set.add(NaN)
set.size // 7

7. 空对象 当作不同 可重复添加
set.add({})
set.add({})
set.size // 9
```

### 属性和方法

```js
1.add

2.size

3.has
set.has(3)          // true

4.delete
set.delete(NaN)    // true

5.clear            
set.clear()        // undefined
set                // Set(0) {}

6.keys
set.keys()
// SetIterator {111, 222}
[...set.keys()]
// [111, 222]

7.values
set.values()
// SetIterator {111, 222}

8.entries
[...set.entries()]
// [[111, 111], [222, 222]]

9.forEach
set.forEach((item, value) => console.log(item, value))
// 111 111
// 222 222
```

### 使用

* 并集

```js
let a = new Set([1, 2, 3])
let b = new Set([2, 3, 4])

let c = new Set([...a], [...b])
// Set(4) {1, 2, 3, 4}
```

* 交集

```js
let d = new Set([...a].filter(x => b.has(x)))
// Set(2) {2, 3}
```

* 差集

```js
let e = new Set([...a].filter(x => !b.has(x)))
// Set(1) {1}
```

### 改变原有set结构

* ...扩展运算符

```js
a = new Set([...a].map(x => x * 2))
// Set(3) {2, 4, 6}
```

* Array.from

```js
a = new Set(Array.from(a, x => x * 10))
// Set(3) {20, 40, 60}
```

## WeakSet

> 是一种**构造函数，**类似Set，不重复值的集合

区别：

1. **成员只能是对象**，不能是其他类型
2. WeakSet中的成员都是**弱引用**，随时可能消失，所以**不能遍历**，所以**没有size属性**

```js
let ws = new WeakSet()

1.ws.add()

2.ws.delete()

3.ws.has()
```



