# Object.keys\(\)

## Object.keys\(\)：返回一个数组，参数是一个\*对象\*自身所有可枚举属性的\*键名\*

```js
var obj  = {
  2: 'aaa',
  c: 333,
  1: 'bbb',
  a: 111,
  3: 'ccc',
  d: 222
}
obj.b = "ddd"

1. 对象
console.log(Object.keys(obj))
// ["1", "2", "3", "c", "a", "d", "b"]
console.log(Object.values(obj))
// ["bbb", "aaa", "ccc", 333, 111, 222, "ddd"]

2. 数组
var arr = [0, null, 1, undefined, 2, 3];
console.log(Object.keys(arr))
//  ["0", "1", "2", "3", "4", "5"]

3. 字符串
var str = 'aaabbbccc'
console.log(Object.keys(str))
//  ["0", "1", "2", "3", "4", "5", "6", "7", "8"]

4. 数值、布尔值（其包装对象都不会为实例添加非继承的属性，所以返回空数组）
Object.keys(666);  // []
Object.keys(true); // []

5. undefined、null（由于不会转为对象，所以报错）
Object.keys(undefined);
Object.keys(null);   // VM11854:1 Uncaught TypeError: Cannot convert undefined or null to object
```

## Object.values\(\)：返回一个数组，参数是一个\*对象\*所有可遍历属性的\*键值\*

```javascript
1. 对象
Object.values({'a': 1, 'b': 2, 'c': 3}); //  [1, 2, 3]
Object.values(["a", "b", "c"]);   //  ["a", "b", "c"]

2. 字符串（会转成类似数组的对象，每个字符作为一个属性，最终返回键值组成的数组）
Object.values('foo');  // ["f", "o", "o"]

3. 数值、布尔值（其包装对象都不会为实例添加非继承的属性，所以返回空数组）
Object.values(666);  // []
Object.values(true); // []

4. undefined、null（由于不会转为对象，所以报错）
Object.values(undefined);
Object.values(null);   // VM11854:1 Uncaught TypeError: Cannot convert undefined or null to object
```

## Object.entries\(\)：返回一个数组，参数是一个\*对象\*所有可遍历属性的\*键值对\*数组

```javascript
Object.entries({'a': 1, 'b': 2, 'c': 3}); // (3) [["a", 1], ["b", 2], ["c", 3]]
```



