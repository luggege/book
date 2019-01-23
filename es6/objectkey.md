#### Object.keys\(\)：返回一个数组，参数是一个\*对象\*所有可遍历属性的\*键名\*

```js
Object.keys({'a': 1, 'b': 2, 'c': 3});   // ["a", "b", "c"]
Object.keys(["a", "b", "c"]);   // ["0", "1", "2"]
```

#### Object.values\(\)：返回一个数组，参数是一个\*对象\*所有可遍历属性的\*键值\*

```js
1. 对象
Object.values({'a': 1, 'b': 2, 'c': 3}); //  [1, 2, 3]
Object.values(["a", "b", "c"]);   //  ["a", "b", "c"]

2. 字符串（会转成类似数组的对象，没个字符作为一个属性，最终返回键值组成的数组）
Object.values('foo');  // ["f", "o", "o"]

3. 数值、布尔值（其包装对象都不会为实例添加非继承的属性，所以返回空数组）
Object.values(666);  // []
Object.values(true); // []

4. undefined、null（由于不会转为对象，所以报错）
Object.values(undefined);
Object.values(null);   // VM11854:1 Uncaught TypeError: Cannot convert undefined or null to object
```

#### Object.entries\(\)：返回一个数组，参数是一个\*对象\*所有可遍历属性的\*键值对\*数组

```js
Object.entries({'a': 1, 'b': 2, 'c': 3}); // (3) [["a", 1], ["b", 2], (2) ["c", 3]]
```



